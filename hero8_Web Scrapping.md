# Basic Components of a WebSite
## HTML
ML stands for Hypertext Markup Language and every website on the internet uses it to display information. Even the jupyter notebook system uses it to display this information in your browser. If you right click on a website and select "View Page Source" you can see the raw HTML of a web page. This is the information that Python will be looking at to grab information from.\
## CSS
CSS stands for Cascading Style Sheets, this is what gives "style" to a website, including colors and fonts, and even some animations! CSS uses tags such as id or class to connect an HTML element to a CSS feature, such as a particular color. id is a unique id for an HTML tag and must be unique within the HTML document, basically a single use connection. class defines a general style that can then be linked to multiple HTML tags. Basically if you only want a single html tag to be red, you would use an id tag, if you wanted several HTML tags/blocks to be red, you would create a class in your CSS doc and then link it to the rest of these blocks.\

## Web Scrapping in Python
There are a few libraries you will need, you can go to your command line and install them with conda install (if you are using anaconda distribution), or pip install for other python distributions.\
\
If you are not using the Anaconda Installation, you can use pip install.
~~~
pip install requests
pip install lxml
pip install bs4
~~~

## Example Task 0 - Grabbing the title of a page
Let's start very simple, we will grab the title of a page. Remember that this is the HTML block with the title tag. For this task we will use www.example.com which is a website specifically made to serve as an example domain.
~~~
import requests
# Step 1: Use the requests library to grab the page
# Note, this may fail if you have a firewall blocking Python/Jupyter 
# Note sometimes you need to run this twice if it fails the first time
res = requests.get("http://www.example.com")

type(res)
# requests.models.Response

res.text
# '<!doctype html>\n<html>\n<head>\n....
~~~
Now we use BeautifulSoup to analyze the extracted page. Technically we could use our own custom script to loook for items in the string of res.text but the BeautifulSoup library already has lots of built-in tools and methods to grab information from a string of this nature (basically an HTML file). Using BeautifulSoup we can create a "soup" object that contains all the "ingredients" of the webpage.\
~~~
import bs4
soup = bs4.BeautifulSoup(rex.txt, 'lxml')
soup
# html page - view page source

## Now use the .select() method to grab elements. We are looking for the 'title' tag, so we will pass in 'title'
title_tag = soup.select('title')
title_tag[0]
# <title>Example Domain</title>
type(title_tag[0])
# bs4.element.Tag
title_tag[0].getText()
# 'Example Domain'
~~~

## Example Task 1 - Grabbing all elements of a class
Let's try to grab all the section headings of the Wikipedia Article on Grace Hopper from this URL: https://en.wikipedia.org/wiki/Grace_Hopper
~~~
## First get the request
res = requests.get('https://en.wikipedia.org/wiki/Grace_Hopper')
## Create a soup from request
soup = bs4.BeautifulSoup(res.text,"lxml")
~~~
Now its time to figure out what we are actually looking for. Inspect the element on the page to see that the section headers have the class "mw-headline". Because this is a class and not a straight tag, we need to adhere to some syntax for CSS.
~~~
Syntax to pass to the .select() method	  Match Results
soup.select('div')	                       All elements with the <div> tag
soup.select('#some_id')	                  The HTML element containing the id attribute of some_id
soup.select('.class')	                    All the HTML elements with the CSS class named notice
soup.select('div span')	                  Any elements named <span> that are within an element named <div>
soup.select('div > span')	                Any elements named <span> that are directly within an element named <div>, with no other element in between
~~~

~~~
soup.select(".toctext")
## [<span class="mw-headline" id="Early_life_and_education">Early life and education</span>,
 <span class="mw-headline" id="Career">Career</span>,
 <span class="mw-headline" id="World_War_II">World War II</span>,
 <span class="mw-headline" id="UNIVAC">UNIVAC</span>, ...
for item in soup.select(".toctext"):
    print(item.text)
# Early life and education
# Career
# World War II
# UNIVAC ...
~~~

## Example Task 3 - Getting an Image from a Website¶
Let's attempt to grab the image of the Deep Blue Computer from this wikipedia article: https://en.wikipedia.org/wiki/Deep_Blue_(chess_computer)
~~~
res = requests.get("https://en.wikipedia.org/wiki/Deep_Blue_(chess_computer)")
soup = bs4.BeautifulSoup(res.text,'lxml')
image_info = soup.select('.thumbimage')
len(image_info)
# 2
computer = image_info[0]
type(computer)
# bs4.element.Tag
~~~
You can make dictionary like calls for parts of the Tag, in this case, we are interested in the src , or "source" of the image, which should be its own .jpg or .png link:
~~~
computer['src']
# '//upload.wikimedia.org/wikipedia/commons/thumb/b/be/Deep_Blue.jpg/220px-Deep_Blue.jpg'
## We can actually display it with a markdown cell with the following
<img src='https://upload.wikimedia.org/wikipedia/commons/thumb/b/be/Deep_Blue.jpg/220px-Deep_Blue.jpg'>
~~~
Now that you have the actual src link, you can grab the image with requests and get along with the .content attribute. Note how we had to add https:// before the link, if you don't do this, requests will complain (but it gives you a pretty descriptive error code).
~~~
image_link = requests.get('https://upload.wikimedia.org/wikipedia/commons/thumb/b/be/Deep_Blue.jpg/220px-Deep_Blue.jpg')
## The raw content (its a binary file, meaning we will need to use binary read/write methods for saving it)
image_link.content
~~~
Let's write this to a file:=, not the 'wb' call to denote a binary writing of the file.
~~~
f = open('my_new_file_name.jpg','wb')
f.write(image_link.content)
f.close()
~~~

## Example Project - Working with Multiple Pages and Items
Let's show a more realistic example of scraping a full site. The website: http://books.toscrape.com/index.html is specifically designed for people to scrape it. Let's try to get the title of every book that has a 2 star rating and at the end just have a Python list with all their titles.\
1. Figure out the URL structure to go through every page
2. Scrap every page in the catalogue
3. Figure out what tag/class represents the Star rating
4. Filter by that star rating using an if statement
5. Store the results to a list
\
\
We can see that the URL structure is the following:\
http://books.toscrape.com/catalogue/page-1.html
~~~
base_url = 'http://books.toscrape.com/catalogue/page-{}.html'
## We can then fill in the page number with .format()
res = requests.get(base_url.format('1'))
## Now let's grab the products (books) from the get request result:
soup = bs4.BeautifulSoup(res.text,"lxml")
soup.select(".product_pod")
## Now we can see that each book has the product_pod class. We can select any tag with this class, and then further reduce it by its rating.
products = soup.select(".product_pod")
example = products[0]
type(example)
example.attrs
# {'class': ['product_pod']}
## Now by inspecting the site we can see that the class we want is class='star-rating Two' , if you click on this in your browser, you'll notice it displays the space as a . , so that means we want to search for ".star-rating.Two"
list(example.children)
example.select('.star-rating.Three')
## But we are looking for 2 stars, so it looks like we can just check to see if something was returned
example.select('.star-rating.Two')
example.select('a')
example.select('a')[1]
example.select('a')[1]['title']

~~~
Okay, let's give it a shot by combining all the ideas we've talked about! (this should take about 20-60 seconds to complete running. Be aware a firwall may prevent this script from running. Also if you are getting a no response error, maybe try adding a sleep step with time.sleep(1).
~~~
two_star_titles = []

for n in range(1,51):

    scrape_url = base_url.format(n)
    res = requests.get(scrape_url)
    
    soup = bs4.BeautifulSoup(res.text,"lxml")
    books = soup.select(".product_pod")
    
    for book in books:
        if len(book.select('.star-rating.Two')) != 0:
            two_star_titles.append(book.select('a')[1]['title'])
~~~










