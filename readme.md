#Tumblr API jQuery Plugin

##Requires:

jQuery 1.7 or later.<br>
A tumblr account with an API key (http://www.tumblr.com/docs/en/api/v2).

##Usage:
 
	$( "target container to embed tumblr in" ).embedTumblr( "your tumblr API key url" );

If your blog is at myblog.tumblr.com and your API key is abc123, the format of "your tumblr API key url" would be something like:

	http://api.tumblr.com/v2/blog/myblog.tumblr.com/posts?api_key=abc123

For information on the Tumblr API and/or to get your tumblr's API key, visit http://www.tumblr.com/docs/en/api/v2.

Style the mark-up noted below however you wish.

Current configuration options:

postsPerPage - int = fairly self explainatory.<br>
pagination - boolean = turns on/off pagination functionality and UI for pagination.<br>
currentPage - int = indicates which page will be displayed first.<br>
loading - HTML as string = accepts any HTML to be displayed while the request is loading via AJAX.<br>
previousBtn - string = inner HTML for previous button created for paging if pagination is enabled.<br>
nextBtn - string = same as previousBtn.<br>
error - HTML as string - HTML to display in the dreadful event that the tumblr API can't be accessed.

More configuration options will probably be available soon.

##Mark-up

This plugin creates A LOT of mark-up for the developer, 
so the following notes quickly explain some of the mark-up used:

All individual posts' containers have the class 'post' plus a post-type specific class:
'text-post', 'audio-post', 'video-post', 'quote-post', etc.

	Ex. <div class="post text-post">...

	Posts' converted timestamps are in <p class="post-date"> elements.

###Text posts
	
A typical text post will be marked up something like:
	
	<div class="post text-post">
		<h2>Hello World.</h2>
		<p class="post-date">8/1&nbsp;2011&nbsp;11:41AM</p>
		<p>Whatís up, Tumblr?</p>
		<a href="http://atumblrblog.tumblr.com">Go to tumblr post...</a>
	</div>

###Photo posts
	
Photos that are in posts with > 1 photo get the class 'multi-photo' on their containing element.
This allows for different styling, sizing etc via CSS between single and multiple photo posts.

Photo sizes are conditionally selected based on their original size -
If the original photo is > 500px width, then a smaller 500px width photo is used,
otherwise, the original size is loaded. All photos link to their original size.

A typical photo post will marked up as follows:
	
	<div class="post photo-post">
		<p class="post-date">8/1&nbsp;2011&nbsp;11:51AM</p>
		<div class="tumblr-photos">
			<figure>
				<a title="" target="_blank" href="http://photo-url.jpg">
					<img src="http://photo-url.jpg">
				</a>
				<figcaption>Photo caption</figcaption>
			</figure>
		</div>
		<p>Photo post text.</p>
		<a href="http://atumblrblog.tumblr.com">Go to tumblr post...</a>
	</div>	

------

If any of the markup doesn't suit your needs, it should be quick to customize yourself in each post type case within the formatPosts function (line 79 and below).
	
Now that you have an idea of the mark-up, it should be relatively easy to decipher the other post types :)