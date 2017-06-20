##I do: Introduction

 Ajax (Asynchronous JavaScript and XML) is a method of building interactive applications for the Web that process user requests immediately. Ajax combines several programming tools including JavaScript, dynamic HTML (DHTML), Extensible Markup Language (XML), cascading style sheets (CSS), the Document Object Model (DOM), and the Microsoft object, XMLHttpRequest. 
 

## I do: What is ajax ?

Ajax allows content on Web pages to update immediately when a user performs an action, unlike an HTTP request, during which users must wait for a whole new page to load. For example, a weather forecasting site could display local conditions on one side of the page without delay after a user types in a zip code.

Google Maps is one well-known application that uses Ajax. The interface allows the user to change views and manipulate the map in real time. Ajax applications do not require installation of a plug-in, but work directly with a Web browser. Because of the technique's reliance on XMLHttpRequest, early applications worked only with Microsoft's Internet Explorer browser, but most other browsers now support Ajax.

Applications created with Ajax use an engine that acts as an intermediary between a user's browser and the server from which it is requesting information. Instead of loading a traditional Web page, the user's browser loads the Ajax engine, which displays the page the user sees. The engine continues to run in the background, using JavaScript to communicate with the Web browser. User input or clicking on the page sends a JavaScript call to the Ajax engine, which can respond instantly in many cases. If the engine needs additional data, it requests it from the server, usually using XML, while it is simultaneously updating the page.

Ajax is not a proprietary technology or a packaged product. Web developers have been using JavaScript and XML in combination for several years. Jesse James Garrett of the consultancy firm Adaptive Path is credited with coining the name "Ajax" as a shorthand way to refer to the specific technologies involved in a current approach.

![Classic Web app versus ajax](http://www.adaptivepath.com/uploads/archive/images/publications/essays/ajax-fig1.png)

##I do: Ajax pros and cons

###Advantages

####Better interactivity
This is pretty much the most striking benefit behind why several developers and webmasters are switching to AJAX for their websites. AJAX allows easier and quicker interaction between user and website as pages are not reloaded for content to be displayed. 

####Easier navigation
AJAX applications on websites can be built to allow easier navigation to users in comparison to using the traditional back and forward button on a browser.

####Compact
With AJAX, several multi purpose applications and features can be handled using a single web page, avoiding the need for clutter with several web pages. For our use of AJAX on goedkope-zomervakantie.com, it took just a few lines of code!

####Backed by reputed brands
Another assuring reason to use AJAX on your websites is the fact that several complex web applications are handled using AJAX, Google Maps is the most impressive and obvious example, other powerful, popular scripts such as the vBulletin forum software has also incorporated AJAX into their latest version.


###Disadvantages

####The back and refresh button are rendered useless
With AJAX, as all functions are loaded on a dynamic page without the page being reloaded or more importantly a URL being changed (except for a hash symbol maybe), clicking the back or refresh button would take you to an entirely different web page or to the beginning of what your dynamic web page was processing. This is the main drawback behind AJAX but fortunately with good programming skills this issue can be fixed.

####It is built on javascript
While javascript is secure and has been heavily used by websites for a long period of time, a percentage of website surfers prefer to turn javascript functionality off on their browser rendering the AJAX application useless, a work around to this con is present as well, where the developer will need to code a parallel non-javascript version of the dynamic web page to cater to these users.
