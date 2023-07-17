<h1>VHS-in-CSS</h1>
<h2>How it looks</h2>
<p><a href="https://al1almasi.ir/VHS-in-CSS">Live preview is here!</a></p>
<h2>How it works</h2>
<h3>Hard stops</h3>
<p>
The pattern is created using a CSS linear-gradient (using the direction "to bottom") with what are known as <a href="https://css-tricks.com/books/greatest-css-tricks/hard-stop-gradients/">"hard stops"</a>. A hard stop is created by defining the end of one colour in the same place as the start of the next colour.
</p>
<h3>"vh" (Viewport's height) units</h3>
<p>
The biggest design challenge was making sure the full pattern of 14 colours was visible at any viewport size, and didn't scroll with the content. The key was to use vh unit to determine the size of each colour stop. The vh unit is a relative unit, and describes a percentage of the viewport height. 1vh is 1% of the viewport height, 50vh is 50% of the viewport height and so on. Using vh is what enables the full gradient pattern to respond to the height of the viewport. <a href="https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Values_and_units">Read more about different units in CSS on MDN</a>.
</p>
<p>Here's a two-colour hard stop gradient as an example, in which we're using the vh unit to specify the size of each colour stop.</p>
<pre lang="css">.twoColorStop {
  min-height: 100vh;
  background: linear-gradient(
    to bottom, 
    red 0 50vh,
    yellow 50vh 100vh
  );
}</pre>
<p>Here's the result.
</p>
<img src="./yellow_red_hard_stop.avif">
<p>
Notice that:
<li>the first colour (red) starts at 0 and ends at 50vh</li>
<li>the second colour (yellow) starts at 50vh and ends at 100vh</li>
Where red stops, yellow begins, creating a hard stop. There are ways you can write the CSS above in a shorthand form, but I've written it out verbosely to demonstrate the concept more clearly.
</p>
<p>
The only differences between this example and the full example is that I'm using 14 colours instead of two colours, and I'm using <a href="https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties">CSS custom properties</a> and <a href="https://developer.mozilla.org/en-US/docs/Web/CSS/calc">CSS calc()</a> to avoid writing out 14 lines of magic numbers. Notice though, that where one colour ends, another colour begins at the same vh value.
</p>
<img src="./stop_size_example.avif">
<p>And finally, to allow the page content to scroll while the background pattern stays fixed in place in the viewport, it's wrapped in a vertically-scrollable element inside the container providing the background gradient pattern. Set height: 100vh on this element to prevent the content increasing the height of the last colour in the gradient.</p>
