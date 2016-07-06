# UserPath Documentation
Our documentation - for the time being. If you have any questions, please don't hesitate to email support@userpath.co - we will get back to you as quickly as possible!

## Plugin Installation Instructions

![On Google Tag Manager](http://userpath.co/new-site/images/img21.png)

------
fdsfs

### On WordPress

------
fdsfs

### On Shopify

------
fdsfs

### On Magento

------
fdsfs

### On BigCommerce

------
fdsfs

### On 3DCart

------
fdsfs

### On PrestaShop

------
fdsfs

### On Weebly

------
fdsfs

### On SquareSpace

------
fdsfs

### On Tumblr

------

1. Go to the profile icon in the top right
2. Click on the Tumblr you want to add the UserPath plugin to
3. Click "edit appearance"
4. Click "edit theme"
5. At the top on the left click on the tiny "Edit HTML" link
6. Scroll to bottom of code
7. Paste in your code

__REMEMBER:__ You must drop the URL of your tumblr blog into your allowed domains in the widget configuration.


## App Download Plugin Installation

If you're trying to use the `drop-in` layout so you can place the app download form where ever you  want on your page, then you must place the snippet provided to you in the HTML, like so:

```html
<script></script>
<div class="userpath-plug-f4a1aedz66"></div>
```

If you'd like to place the form in more than one place on the same page, simply copy the line with the div tag and place it multiple times in your HTML where ever you would like it to appear. For instance, say you have a `header`, a `main section`, a `download section` and `footer`. Let's say you want to have your App Download widget in the `header` and the `download section` and this is your HTML:

```html
<!DOCTYPE html>
<html>
<head>
	<title>My App Homepage</title>
</head>
<body>
	<header>
		<button>Download for iOS</button>
		<button>Download for Android</button>
	</header>
	<section id="main">
		<ul>
			<li>It's free</li>
			<li>It's live streaming</li>
			<li>It's social</li>
			<li>It's local</li>
			<li>It's viral</li>
			<li>It's gamified</li>
		</ul>
	</section>
	<section id="download">
		<button>Download for iOS</button>
		<button>Download for Android</button>
	</section>
	<footer>
		<p>&copy; 2016 My App Homepage</p>
		<a href="#">about</a>
		<a href="#">contact</a>
	</footer>
</body>
</html>
```

You would simply add the `script` tag to the bottom, like so:

```html
<!DOCTYPE html>
<html>
<head>
	<title>My App Homepage</title>
</head>
<body>
	... <!-- your code above this -->
	<script type="text/javascript"></script>
</body>
</html>
```

and finally, drop the `div`s in the appropriate sections (`header` and `download`) like this:

```html
<!DOCTYPE html>
<html>
<head>
	<title>My App Homepage</title>
</head>
<body>
	<header>
		...
		<div class="userpath-plugin-fa96ed3cz"></div>
	</header>
	<section id="main">
		<ul>
			...
		</ul>
	</section>
	<section id="download">
		<div class="userpath-plugin-fa96ed3cz"></div>
		...
	</section>
	<footer>
		...
	</footer>
	<script type="text/javascript"></script>
</body>
</html>
```
