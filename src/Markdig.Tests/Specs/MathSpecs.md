# Extensions

Adds support for mathematics spans:

## Math Inline
 
Allows to define a mathematic inline block embraced by `$...$`

```````````````````````````````` example
This is a $math inline$
.
<p>This is a <span class="math">\(math inline\)</span></p>
````````````````````````````````

Or by `$$...$$` embracing it by:

```````````````````````````````` example
This is a $$math inline$$
.
<p>This is a <span class="math">\(math inline\)</span></p>
````````````````````````````````

Newlines inside an inline math are not allowed:

```````````````````````````````` example
This is not a $$math 
inline$$ and? this is a $$math inline$$
.
<p>This is not a $$math
inline$$ and? this is a <span class="math">\(math inline\)</span></p>
````````````````````````````````

```````````````````````````````` example
This is not a $math 
inline$ and? this is a $math inline$
.
<p>This is not a $math
inline$ and? this is a <span class="math">\(math inline\)</span></p>
````````````````````````````````
An opening `$` can be followed by a space if the closing is also preceded by a space `$`:

```````````````````````````````` example
This is a $ math inline $
.
<p>This is a <span class="math">\(math inline\)</span></p>
````````````````````````````````

```````````````````````````````` example
This is a $    math inline     $ after
.
<p>This is a <span class="math">\(math inline\)</span> after</p>
````````````````````````````````

```````````````````````````````` example
This is a $$    math inline     $$ after
.
<p>This is a <span class="math">\(math inline\)</span> after</p>
````````````````````````````````

```````````````````````````````` example
This is a not $ math inline$ because there is not a whitespace before the closing
.
<p>This is a not $ math inline$ because there is not a whitespace before the closing</p>
````````````````````````````````

For the opening `$` it requires a space or a punctuation before (but cannot be used within a word):

```````````````````````````````` example
This is not a m$ath inline$
.
<p>This is not a m$ath inline$</p>
````````````````````````````````

For the closing `$` it requires a space after or a punctuation (but cannot be preceded by a space and cannot be used within a word):

```````````````````````````````` example
This is not a $math inlin$e
.
<p>This is not a $math inlin$e</p>
````````````````````````````````

For the closing `$` it requires a space after or a punctuation (but cannot be preceded by a space and cannot be used within a word):

```````````````````````````````` example
This is should not match a 16$ or a $15
.
<p>This is should not match a 16$ or a $15</p>
````````````````````````````````

A `$` can be escaped between a math inline block by using the escape `\\` 

```````````````````````````````` example
This is a $math \$ inline$
.
<p>This is a <span class="math">\(math \$ inline\)</span></p>
````````````````````````````````

At most, two `$` will be matched for the opening and closing:

```````````````````````````````` example
This is a $$$math inline$$$
.
<p>This is a <span class="math">\($math inline$\)</span></p>
````````````````````````````````

Regular text can come both before and after the math inline

```````````````````````````````` example
This is a $math inline$ with text on both sides.
.
<p>This is a <span class="math">\(math inline\)</span> with text on both sides.</p>
````````````````````````````````
A mathematic inline block takes precedence over standard emphasis `*` `_`:

```````````````````````````````` example
This is *a $math* inline$
.
<p>This is *a <span class="math">\(math* inline\)</span></p>
````````````````````````````````
An opening $$ at the beginning of a line should not be interpreted as a Math inline:

```````````````````````````````` example
$$ math $$ starting at a line
.
<p><span class="math">\(math\)</span> starting at a line</p>
````````````````````````````````

## Math Block

The math block can spawn on multiple lines by having a $$ starting on a line.
It is working as a fenced code block.

```````````````````````````````` example
$$
\begin{equation}
  \int_0^\infty \frac{x^3}{e^x-1}\,dx = \frac{\pi^4}{15}
  \label{eq:sample}
\end{equation}
$$
.
<div class="math">
\[
\begin{equation}
  \int_0^\infty \frac{x^3}{e^x-1}\,dx = \frac{\pi^4}{15}
  \label{eq:sample}
\end{equation}
\]</div>
````````````````````````````````
