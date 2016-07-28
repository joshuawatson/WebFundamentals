project_path: /web/_project.yaml
book_path: /web/_book.yaml
description: Much of the web isn't optimized for those multi-device experiences. Learn the fundamentals to get your site working on mobile, desktop or anything else with a screen.

<p class="intro">
  While it may be helpful to think about defining breakpoints based on device classes, use caution.  Defining breakpoints based on specific devices, products,brand names, or operating systems that are in use today can result in a maintenance nightmare. Instead, the content itself should determine how the layout adjusts to its container.
</p>



















# WARNING: This page has an include that should be a callout (i.e. a highlight.liquid, but it has no text - please fix this)



# WARNING: This page has a highlight.liquid include that wants to show a list but it's not supported on devsite. Please change this to text and fix the issue






## Pick major breakpoints by starting small, then working up

Design the content to fit on a small screen size first, then expand the screen
until a breakpoint becomes necessary.  This allows you to optimize
breakpoints based on content and maintain the fewest number of breakpoints
possible.

Let's work through the example we saw at the beginning,
the [weather forecast](/web/fundamentals/design-and-ui/responsive/fundamentals/).
The first step is to make the forecast look good on a small screen.

<figure>
  <a href="/web/resources/samples/fundamentals/design-and-ui/responsive/fundamentals/weather-1.html">
    <img src="imgs/weather-1.png" class="center" srcset="imgs/weather-1.png 1x, imgs/weather-1-2x.png 2x" alt="Preview of the weather forecast displayed on a small screen.">
  </a>
</figure>

Next, resize the browser until there is too much white space between the
elements and the forecast simply doesn't look as good.  The decision is somewhat
subjective, but above 600px is certainly too wide.

<figure>
  <a href="/web/resources/samples/fundamentals/design-and-ui/responsive/fundamentals/weather-1.html">
    <img src="imgs/weather-2.png" class="center" srcset="imgs/weather-2.png 1x, imgs/weather-2-2x.png 2x" alt="Preview of the weather forecast as the page gets wider.">
  </a>
</figure>

To insert a breakpoint at 600px, create two new stylesheets, one to use when the
browser is 600px and below, and one for when it is wider than 600px.


  <div dir="ltr" class="highlight-module highlight-module--code highlight-module--right">
      <div class="highlight"><pre><span class="nt">&lt;link</span> <span class="na">rel=</span><span class="s">&quot;stylesheet&quot;</span> <span class="na">href=</span><span class="s">&quot;weather.css&quot;</span><span class="nt">&gt;</span>
<span class="nt">&lt;link</span> <span class="na">rel=</span><span class="s">&quot;stylesheet&quot;</span> <span class="na">media=</span><span class="s">&quot;(max-width:600px)&quot;</span> <span class="na">href=</span><span class="s">&quot;weather-2-small.css&quot;</span><span class="nt">&gt;</span>
<span class="nt">&lt;link</span> <span class="na">rel=</span><span class="s">&quot;stylesheet&quot;</span> <span class="na">media=</span><span class="s">&quot;(min-width:601px)&quot;</span> <span class="na">href=</span><span class="s">&quot;weather-2-large.css&quot;</span><span class="nt">&gt;</span>
</pre></div>
      <p>
        <a class="highlight-module__cta mdl-button mdl-js-button mdl-button--raised mdl-button--colored" href="/web/resources/samples/fundamentals/design-and-ui/responsive/fundamentals/weather-2.html">Try full sample</a>
      </p>
  </div>



Finally, refactor the CSS.  In this example, we've placed the common styles such
as fonts, icons, basic positioning, colors in `weather.css`.  Specific layouts
for the small screen are then placed in `weather-small.css` and large screen
styles are placed in `weather-large.css`.

<figure>
  <a href="/web/resources/samples/fundamentals/design-and-ui/responsive/fundamentals/weather-2.html">
    <img src="imgs/weather-3.png" class="center" srcset="imgs/weather-3.png 1x, imgs/weather-3-2x.png 2x" alt="Preview of the weather forecast designed for a wider screen.">
  </a>
</figure>

## Pick minor breakpoints when necessary

In addition to choosing major breakpoints when layout changes significantly, it
is also helpful to adjust for minor changes.  For example between major
breakpoints, it may be helpful to adjust the margins or padding on an element,
or increase the font size to make it feel more natural in the layout.

Let's start by optimizing the small screen layout.  In this case, let's boost
the font when the viewport width is greater than 360px.  Second, when there is
enough space, we can separate the high and low temperature so they're on the
same line, instead of on top of each other.  And let's also make the weather
icons a bit larger.


  <div dir="ltr" class="highlight-module highlight-module--code highlight-module--right">
      <div class="highlight"><pre><span class="k">@media</span> <span class="o">(</span><span class="nt">min-width</span><span class="o">:</span> <span class="nt">360px</span><span class="o">)</span> <span class="p">{</span>
  <span class="nt">body</span> <span class="p">{</span>
    <span class="k">font-size</span><span class="o">:</span> <span class="m">1.0em</span><span class="p">;</span>
  <span class="p">}</span>
<span class="p">}</span>

<span class="k">@media</span> <span class="o">(</span><span class="nt">min-width</span><span class="o">:</span> <span class="nt">500px</span><span class="o">)</span> <span class="p">{</span>
  <span class="nc">.seven-day-fc</span> <span class="nc">.temp-low</span><span class="o">,</span>
  <span class="nc">.seven-day-fc</span> <span class="nc">.temp-high</span> <span class="p">{</span>
    <span class="k">display</span><span class="o">:</span> <span class="k">inline</span><span class="o">-</span><span class="k">block</span><span class="p">;</span>
    <span class="k">width</span><span class="o">:</span> <span class="m">45%</span><span class="p">;</span>
  <span class="p">}</span>

  <span class="nc">.seven-day-fc</span> <span class="nc">.seven-day-temp</span> <span class="p">{</span>
    <span class="k">margin-left</span><span class="o">:</span> <span class="m">5%</span><span class="p">;</span>
  <span class="p">}</span>

  <span class="nc">.seven-day-fc</span> <span class="nc">.icon</span> <span class="p">{</span>
    <span class="k">width</span><span class="o">:</span> <span class="m">64px</span><span class="p">;</span>
    <span class="k">height</span><span class="o">:</span> <span class="m">64px</span><span class="p">;</span>
  <span class="p">}</span>
<span class="p">}</span>
</pre></div>
      <p>
        <a class="highlight-module__cta mdl-button mdl-js-button mdl-button--raised mdl-button--colored" href="/web/resources/samples/fundamentals/design-and-ui/responsive/fundamentals/weather-small.css">Try full sample</a>
      </p>
  </div>



<div class="mdl-grid">
  <div class="mdl-cell mdl-cell--6-col">
    <img src="imgs/weather-4-l.png" srcset="imgs/weather-4-l.png 1x, imgs/weather-4-l-2x.png 2x" alt="Before adding minor breakpoints.">
  </div>

  <div class="mdl-cell mdl-cell--6-col">
    <img src="imgs/weather-4-r.png" srcset="imgs/weather-4-r.png 1x, imgs/weather-4-r-2x.png 2x" alt="After adding minor breakpoints.">
  </div>
</div>

Similarly, for the large screens, it's best to limit to maximum width of the
forecast panel so it doesn't consume the whole screen width.


  <div dir="ltr" class="highlight-module highlight-module--code highlight-module--right">
      <div class="highlight"><pre><span class="k">@media</span> <span class="o">(</span><span class="nt">min-width</span><span class="o">:</span> <span class="nt">700px</span><span class="o">)</span> <span class="p">{</span>
  <span class="nc">.weather-forecast</span> <span class="p">{</span>
    <span class="k">width</span><span class="o">:</span> <span class="m">700px</span><span class="p">;</span>
  <span class="p">}</span>
<span class="p">}</span>
</pre></div>
      <p>
        <a class="highlight-module__cta mdl-button mdl-js-button mdl-button--raised mdl-button--colored" href="/web/resources/samples/fundamentals/design-and-ui/responsive/fundamentals/weather-large.css">Try full sample</a>
      </p>
  </div>



## Optimize text for reading

Classic readability theory suggests that an ideal column should contain 70 to 80
characters per line (about  8 to 10 words in English). Thus each time the width
of a text block grows past about 10 words, a breakpoint should be considered.

<div class="mdl-grid">
  <figure class="mdl-cell mdl-cell--4-col">
    <img src="imgs/reading-ph.png" srcset="imgs/reading-ph.png 1x, imgs/reading-ph-2x.png 2x" alt="Before adding minor breakpoints.">
    <figcaption>Before adding minor breakpoints.</figcaption>
  </figure>

  <figure class="mdl-cell mdl-cell--8-col">
    <img src="imgs/reading-de.png" srcset="imgs/reading-de.png 1x, imgs/reading-de-2x.png 2x" alt="After adding minor breakpoints.">
    <figcaption>After adding minor breakpoints.</figcaption>
  </figure>
</div>

Let's take a deeper look at the above blog post example.  On smaller screens,
the Roboto font at 1em works perfectly giving 10 words per line, but larger
screens will require a breakpoint. In this case, if the browser width is greater
than 575px, the ideal content width is 550px.


  <div dir="ltr" class="highlight-module highlight-module--code highlight-module--right">
      <div class="highlight"><pre><span class="k">@media</span> <span class="o">(</span><span class="nt">min-width</span><span class="o">:</span> <span class="nt">575px</span><span class="o">)</span> <span class="p">{</span>
  <span class="nt">article</span> <span class="p">{</span>
    <span class="k">width</span><span class="o">:</span> <span class="m">550px</span><span class="p">;</span>
    <span class="k">margin-left</span><span class="o">:</span> <span class="k">auto</span><span class="p">;</span>
    <span class="k">margin-right</span><span class="o">:</span> <span class="k">auto</span><span class="p">;</span>
  <span class="p">}</span>
<span class="p">}</span>
</pre></div>
      <p>
        <a class="highlight-module__cta mdl-button mdl-js-button mdl-button--raised mdl-button--colored" href="/web/resources/samples/fundamentals/design-and-ui/responsive/fundamentals/reading.html">Try full sample</a>
      </p>
  </div>



## Never completely hide content

Be careful when choosing what content to hide or show depending on screen size.
Don't simply hide content just because you can't fit it on screen.  Screen size
is not a definitive indication of what a user may want.  For example,
eliminating the pollen count from the weather forecast could be a serious issue
for spring time allergy sufferers who need the information to determine if they
can go outside or not.



