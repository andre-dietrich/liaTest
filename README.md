<!--

author:   Andre Dietrich

email:    dietrich@ivs.cs.uni-magdeburg.de

version:  1.0.0

language: en_US

narrator: US English Female


script:   https://cdn.jsdelivr.net/chartist.js/latest/chartist.min.js

script:   https://cdn.rawgit.com/davidedc/Algebrite/master/dist/algebrite.bundle-for-browser.js

script:   https://felixhao28.github.io/JSCPP/dist/JSCPP.es5.min.js


script:   https://interactivepython.org/runestone/static/thinkcspy/_static/skulpt.min.js

script:   https://interactivepython.org/runestone/static/thinkcspy/_static/skulpt-stdlib.js


script:   https://curiosity-driven.github.io/prolog-interpreter/parser.js

script:   https://curiosity-driven.github.io/prolog-interpreter/interpreter.js

-->

# Lia-Script

                                    --{{0}}--
With Lia, we try to implement an extended Markdown format that should enable
everyone to create, share, adapt, translate or correct and extend online courses
without the need of being a web-developer.

See the online rendered version at: https://liascript.github.io


                                    --{{0}}--
Click on the (ear) button at the navigation bar to switch between spoken and
plain text mode format. And use the arrows-buttons at the top for navigating.


*Lia-Script* <!-- class = "animated infinite bounce" style = "color: red;" --> is an extended Markdown format for writing interactive online
courses. Imagine all schoolbooks, technical or scientific literature could
become open-source projects and more interactive ... with collaborating teachers
and students ...

* easy to share adapt and translate
* no additional software required, everything is implemented in JavaScirpt/Elm
  and runs directly within the browser (online)
* automatic conversion to epub, pdf, ...


                                     --{{1}}--
Everything that is required is simple text-editor and a web-browser. Or you
start directly to create and share your course on github. The entire parsing and
transformation of Lia-Markdown to any other format is done within the browser at
client-side.


## *Markdown*-Syntax


                                     --{{0}}--
This section is intended to give a brief overview on the basic Markdown
formatting elements. The only difference to common Markdown at this point is,
that every course has to start with a comment, which defines authors, a language
and  a narrator voice, see https://responsivevoice.org for all supported voices.

Initial LIA-comment-tag for basic definitions:

``` XML
<!--

author:   Andre Dietrich

email:    dietrich[at]ivs.cs.uni-magdeburg.de

version:  1.0.0

language: en_US

narrator: US English Female

script:   javascript resourse url

script:   another javascript resourse url

-->
```

### Structuring

                                    --{{0}}--
A course is structured as any other Markdown document with starting hash-tags,
whereby the number of hash-tags is used to define the hierarchy.

```markdown
# Main Title

 ...

## Section Title 1

 ...

### Subsection Title

 ...
## Section Title 2
```

### Text-Formatting

                                    --{{0}}--
We tried to use the github flavored Markdown style for simple formatting with
some additional elements.

\*italic\* -> *italic*

\*\*bold\*\* -> **bold**

\*\*\*bold and italic \*\*\* -> ***bold and italic ***

\_also italic\_ -> _also italic_

\_\_also bold\_\_ -> __also bold__

\_\_\_also bold and italic\_\_\_ -> ___also bold and italic___

\~strike\~ -> ~strike~

                                     --{{1}}--
These exceptions are for example underline and its combination with strike
through or the application of superscript. If you, for example, superscript
superscript you can get even smaller.

                                       {{1}}
================================================================================

\~\~underline\~\~ -> ~~underline~~

\~\~\~strike and underline\~\~\~ -> ~~~strike and underline~~~

\^superscript\^ -> ^superscript^ ^^superscript^^ ^^^superscript^^^

================================================================================


#### Combinations

                                     --{{0}}--
As you can see from the examples, you can combine all elements freely.


\*\*bold \_bold italic\_\*\* -> **bold _italic_**

\*\*\~bold strike\~ \~\~bold underline\~\~\*\* -> **~bold strike~ ~~bold underline~~**

\*\~italic strike\~ \~\~italic underline\~\~\* -> *~italic strike~ ~~italic underline~~*

#### Escape Characters

\*, \~, \_, \#, \{, \}, \[, \], \|, \`, \$

                                     --{{0}}--
If you want to use multiple stars, hash-tags, or other syntax elements within
your script without applying their functionality, then you can escape them with
a starting backslash.

### Symbols

                                     --{{0}}--
One thing that we missed in standard Markdown, was an implementation for arrows.
The parenthesis shows, how arrows are defined in our Markdown implementation with
their result on the right (these symbols are generated automatically for you).

(`->`) ->, (`->>`) ->>, (`>->`) >->, (`<-`) <-, (`<-<`) <-<,
(`<<-`) <<-, (`<->`) <->, (`=>`) =>, (`<=`) <=, (`<=>`) <=>

(`-->`) -->, (`<--`) <--, (`<-->`) <-->, (`==>`) ==>, (`<==`) <==, (`<==>`) <==>

(`~>`) ~>, (`<~`) <~

                                     --{{1}}--
But you can also use some basic smileys. We will try to extend this partial
support in the future.

                                       {{1}}
`:-)` :-), `;-)` ;-), `:-D` :-D, `:-O` :-O, `:-(` :-(, `:-|` :-|,
`:-/` :-/, `:-P` :-P, `:-*` :-*, `:')` :'), `:'(` :'(

### References

The next section shows how external resources can be integrated.

#### Simple Links

                                     --{{0}}--
There are two ways of adding links to a Markdown document, either by inlining
the url directly or you can name it, as shown in listing 2, by applying the
typical brackets and parenthesis notation.


1. example of an url-link -> http://goo.gl/fGXNvu

   text-formatting can be applied also (`*** http://goo.gl/fGXNvu ***`) ->
   *** http://goo.gl/fGXNvu ***

2. naming the link (`[title](http://goo.gl/fGXNvu)`) -> [title](http://goo.gl/fGXNvu)

#### Images and Movies

                                    --{{0}}--
Images are marked with a starting exclamation mark before the link, movies are
defined by two exclamation marks.

* Image-notation: `![image](https://upload.wikimedia.org/wikipedia/commons/d/d0/Creative-Tail-Animal-lion.svg)`

  ![image](images/load.gif)

* Movie-notation: `!![movie](https://www.youtube.com/embed/XsNk5aOpqUc?&autoplay=1)`

  !![movie](https://www.youtube.com/embed/XsNk5aOpqUc?&autoplay=1)

  See also http://www.google.com/support/youtube/bin/answer.py?hl=en&answer=56107
  to get an overview on how a YouTube link has to be formatted to add a starting
  and/or end point, autoplay, subtitles, and other options.

### Styling

                                    --{{0}}--
Adding CSS elements or classes or any other HTML setting to an image or to any
other Markdown element is implemented via a trailing comment-tag, everything
within this comment is treated as a HTML attribute, so that it can
also be used to apply graphical filters of for positioning.


``` markdown
![image](...Creative-Tail-Animal-lion.svg)<!--
style = "width: 100px;
         border: 10px solid;
         filter: grayscale(100%);"

class = "animated infinite bounce"
-->
```


![image](https://upload.wikimedia.org/wikipedia/commons/d/d0/Creative-Tail-Animal-lion.svg)<!--
style = "width: 100px;
         border: 10px solid;
         filter: grayscale(100%);"

class = "animated infinite bounce"
-->
![image](https://upload.wikimedia.org/wikipedia/commons/d/d0/Creative-Tail-Animal-lion.svg)<!--
style="
  width: 120px;
  border: 10px solid;"
-->
![image](https://upload.wikimedia.org/wikipedia/commons/d/d0/Creative-Tail-Animal-lion.svg)<!--
  style="width: 140px;
  border: 10px solid;"
-->
![image](https://upload.wikimedia.org/wikipedia/commons/d/d0/Creative-Tail-Animal-lion.svg)<!--
  style="width: 120px;
  border: 10px solid;
  -webkit-filter: grayscale(100%); /* Safari 6.0 - 9.0 */
  filter: grayscale(100%);"
-->
![image](https://upload.wikimedia.org/wikipedia/commons/d/d0/Creative-Tail-Animal-lion.svg)<!--
  style="width: 100px;
  border: 10px solid;
  -webkit-filter: blur(5px); /* Safari 6.0 - 9.0 */
  filter: blur(5px);"
-->

                                     --{{1}}--
The same technique can also be applied to style and format movies and other inline
elements, such as links, words, symbols, or code...

                                       {{1}}
================================================================================

!![movie](https://www.youtube.com/embed/XsNk5aOpqUc)<!--
style = "width: 100px; height: 60px;"
-->
!![movie](https://www.youtube.com/embed/XsNk5aOpqUc)<!--
style = "width: 120px; height: 70px;"
-->
!![movie](https://www.youtube.com/embed/XsNk5aOpqUc)<!--
style = "width: 140px; height: 80px;"
-->
!![movie](https://www.youtube.com/embed/XsNk5aOpqUc)<!--
style = "width: 120px;
         height: 70px;
         -webkit-filter: grayscale(100%); /* Safari 6.0 - 9.0 */
         filter: grayscale(100%);"
-->
!![movie](https://www.youtube.com/embed/XsNk5aOpqUc)<!--
style = "width: 100px;
         height: 60px;
         -webkit-filter: blur(5px); /* Safari 6.0 - 9.0 */
         filter: blur(5px);"
-->

`:-) <!-- class = "animated infinite bounce" -->` --> :-) <!-- class = "animated infinite bounce" -->

`[google](www.google.de) <!-- style = "color: red;" -->` --> [google](www.google.de) <!-- style = "color: red;" -->

================================================================================

#### Block-Styling

                                  --{{0}}--
Settings for entire blocks can be set with a **starting** comment that includes
all required HTML-attributes and can even contain animation settings. These can
be used to highlight specific elements of your slides.


``` markdown
<!-- class = "animated rollIn" style = "animation-delay: 3s; color: purple" -->
The whole text-block should appear in purple color and with a wobbling effect.
Which is a **bad** example, please use it with causion ...
~~ ;-) ~~ <!-- class = "animated infinite bounce" style = "color: red;" -->
```

<!-- class = "animated rollIn" style = "animation-delay: 3s; color: purple" -->
The whole text-block should appear in purple color and with a wobbling effect.
Which is a **bad** example, please use it with causion ...
~~ ;-) ~~ <!-- class = "animated infinite bounce" style = "color: red;" -->

### Lists & Tables

Within the following part enumerations, itemizations and tables are presented,
actually with no difference to basic Markdown, so you can skip this section,
if you are already familiar with it.

#### Unordered Lists

                                 --{{0}}--
To define unordered list, starting stars, pluses, and minuses can be used and
mixed. If one point has more than one line, you can also use newlines, but with
spaces at the beginning. Paragraphs can be included in the same way, by using
two newlines.

Markdown-format:

``` markdown
* alpha
+ *beta*
- gamma
  and delta

  new Paragraph
```

Result:

* alpha
+ *beta*
- gamma
  and delta

  new Paragraph


#### Ordered Lists

                                 --{{0}}--
Ordered list start with a number and a dot. As you can see from the example, the
number does not count at the moment, the generated list will always count by the
order of appearance. And it is also possible to mix lists with other lists and
elements freely.

Markdown-format:

``` markdown
0. alpha
2. **beta**
1. * gamma
   * delta
   * and epsilon
3. probably zeta
```

Result:

0. alpha
2. **beta**
1. * gamma
   * delta
   * and epsilon
3. probably zeta

#### Tables

                                   --{{0}}--
Tables, we hope, are self-explanatory. The second line is used to define a table
header as well as the alignment of the column, which is indicated by the colon.
The default is left alignment.

Markdown-format:

``` markdown
| Tables            | Are           | Cool  |
| ----------------- |:-------------:| -----:|
| *** col 3 is ***  | right-aligned | $1600 |
| ** col 2 is **    | centered      |   $12 |
| * zebra stripes * | are neat      |    $1 |
```

Result:

| Tables            | Are           | Cool  |
| ----------------- |:-------------:| -----:|
| *** col 3 is ***  | right-aligned | $1600 |
| ** col 2 is **    | centered      |   $12 |
| * zebra stripes * | are neat      |    $1 |



### Blockquotes

Markdown-format:

``` markdown
<!--
style="font-size: 18px; font-style: italic; width: 500px; margin: 0.25em 0;"
-->
> Blockquotes are very handy in email to emulate reply text.
> This line is part of the same quote.

Quote break.

> This is a very long line that will still be quoted properly when it wraps...
```

Result:

<!--
style="font-size: 18px; font-style: italic; width: 500px; margin: 0.25em 0;"
-->
> Blockquotes are very handy in email to emulate reply text.
> This line is part of the same quote.

Quote break.

> This is a very long line that will still be quoted properly when it wraps. Oh boy let's keep writing to make sure this is long enough to actually wrap for everyone. Oh, you can *put* **Markdown** into a blockquote.


                                   --{{1}}--
Next to simple paragraphs also any other block element can be included ...


                                     {{1}}
================================================================================

``` markdown
> <!-- style="font-size: 18px; font-style: italic; width: 500px; margin: 5.25em 0;" -->
> | Tables            | Are           | Cool  |
> | ----------------- |:-------------:| -----:|
> | *** col 3 is ***  | right-aligned | $1600 |
> | ** col 2 is **    | centered      |   $12 |
> | * zebra stripes * | are neat      |    $1 |
```

Result:

> <!-- style="font-size: 18px; font-style: italic; width: 500px; margin: 5.25em 0;" -->
> | Tables            | Are           | Cool  |
> | ----------------- |:-------------:| -----:|
> | *** col 3 is ***  | right-aligned | $1600 |
> | ** col 2 is **    | centered      |   $12 |
> | * zebra stripes * | are neat      |    $1 |

================================================================================

### HTML

You can also use raw HTML in your Markdown, and it'll mostly work pretty well.

```HTML
Test **bold** and <b> HTML bold</b> works also inline

<dl>
  <dt style="color: red">Definition list</dt>
  <dd>Is something people use sometimes.</dd>

  <dt><b>Markdown in HTML</b></dt>
  <dd>Does *not* work **very** well. Use HTML <em>tags</em>.</dd>
</dl>
```

Test **bold** and <b> HTML bold</b> works also inline

<dl>
  <dt style="color: red">Definition list</dt>
  <dd>Is something people use sometimes.</dd>

  <dt><b>Markdown in HTML</b></dt>
  <dd>Does *not* work **very** well. Use HTML <em>tags</em>.</dd>
</dl>

#### HTML & JavaScirpt

                                 --{{0}}--
In contrast to common Markdown-Parsers it is also possible to include and
execute javascript code. If you combine it with your HTML elements, you are free
to integrate whatever you want.

``` markdown
<link rel="stylesheet" href="//cdn.jsdelivr.net/chartist.js/latest/chartist.min.css">
<div class="ct-chart ct-golden-section" id="chart"></div>
<script>
    // Initialize a Line chart in the container with the ID chart
    new Chartist.Line('#chart', {
        labels: [1, 2, 3, 4],
        series: [[100, 120, 180, 200]]
    });
</script>
```

<link rel="stylesheet" href="//cdn.jsdelivr.net/chartist.js/latest/chartist.min.css">


                                   {{0-1}}
<div class="ct-chart ct-golden-section" id="chart1"></div>
<script>
// Initialize a Line chart in the container with the ID chart1
new Chartist.Line('#chart1', {
  labels: [1, 2, 3, 4],
  series: [[100, 120, 180, 200]]
});
</script>


                                     {{1}}
<div class="ct-chart ct-golden-section" id="chart2"></div>
<script>
// Initialize a Line chart in the container with the ID chart2
new Chartist.Line('#chart2', {
  labels: [1, 2, 3, 4],
  series: [[-100, 120, 180, 20]]
});
</script>

                                --{{1}}--
Note, you have to include all required JavaScirpt-resourses in the initial
comment after the script definition. And by combining this feature with
LiaScript effects, you can build even more sophisticated courses.


## Math-Mode

{{0}}{{ via KaTex http://katex.org }}

{{1}}{{ Inline math-mode `$ \frac{a}{\sum{b+i}} $` -> $ \frac{a}{\sum{b+i}} $ }}

                                        {{2}}
Multi-line math-mode can be applied by double dollars `$$ formula $$`
$$
  \frac{a}{\sum{b+i}}
$$

                                    --{{0}}--
We apply KaTeX for math-formatting, see the documentation at www.katex.org.

                                    --{{1}}--
A formula can be either inline with single dollars.

                                    --{{2}}--
Or multi-line by using the double dollar notation.

## Syntax Highlighting

The following section shows a three types of code blocks, simple inline and
block-code as well as interactive block-code, as an extension to common
Markdown.

### Inline-Code

Inline code via \` enter some code in here 1\#\#\#\$& \` -> ` enter some code in here 1###$& `

### Block-Code

                                --{{0}}--
Syntax highlighting is enabled with highlight.js. Blocks of code are either by
lines with three back-ticks \`\`\` and an identifier for the language. See a
complete list of examples and how to write language names at the
[highlight.js demo page](http://softwaremaniacs.org/media/soft/highlight/test.html).

\`\`\` `language (python, c, javascript, ...)`

code ...

\`\`\`

C example:

``` c
#include "test.h"

int main () {
    printf("this is an example\n");
    return 0;
}
```

Python example:

``` python
import math

def lia_sqrt(val):
    return math.sqrt(val) + 22
```

### Interactive Code

                                    --{{0}}--

Why should code examples not be interactive and editable, especially if it is
JavaScript or any other language that has been ported to it? Simply add the
required resources to the initial comment with keyword `script`.

1. Add resource to main-comment: `script: url.js`

2. Add a trailing script-tag to your code: `<script> {X} </script>`


                                     --{{1}}--
And add an additional script tag to the end of your language definition with an
big X in braces. This element is afterwards substituted with your code and
executed. We provide some basic examples within the following section.



#### JavaScript

                                    --{{0}}--
Click on the run-button to execute the script or double-click on the code to
edit it and to change the output ...

Double-click on the code to switch to edit mode and double-click to get out:

```
var i=0;
var j=0;
var result = 0;

for(i = 0; i<1000; i++) {
    for(j = 0; j<i; j++) {
        result += j;
    }
}
// the last statement defines the return statement
result;
```
<script> {X} </script>



#### JavaScript Chartist

A drawing example, for demonstrating that any javascript library can be used,
also for drawing.

<link rel="stylesheet" href="//cdn.jsdelivr.net/chartist.js/latest/chartist.min.css">

```javascript
// Initialize a Line chart in the container with the ID chart1
new Chartist.Line('#chart1', {
  labels: [1, 2, 3, 4],
  series: [[100, 120, 180, 200]]
});

// Initialize a Line chart in the container with the ID chart2
new Chartist.Bar('#chart2', {
  labels: [1, 2, 3, 4],
  series: [[5, 2, 8, 3]]
});
```
<script> {X} </script>

<div class="ct-chart ct-golden-section" id="chart1"></div>
<div class="ct-chart ct-golden-section" id="chart2"></div>


#### Computer-Algebra

An example of a Computer-Algebra-System (Algebrit), see xxx for more examples:

```javascript
x + x
```
<script> Algebrite.run(`{X}`) </script>



```javascript
f=sin(t)^4-2*cos(t/2)^3*sin(t)

f=circexp(f)

defint(f,t,0,2*pi)
```
<script> Algebrite.run(`{X}`) </script>



#### Elm

```elm
-- Read more about this program in the official Elm guide:
-- https://guide.elm-lang.org/architecture/user_input/buttons.html

import Html exposing (beginnerProgram, div, button, text)
import Html.Events exposing (onClick)


main =
  beginnerProgram { model = 0, view = view, update = update }


view model =
  div []
    [ button [ onClick Decrement ] [ text "-" ]
    , div [] [ text (toString model) ]
    , button [ onClick Increment ] [ text "+" ]
    ]


type Msg = Increment | Decrement


update msg model =
  case msg of
    Increment ->
      model + 1

    Decrement ->
      model - 1
```


#### C++

Teaching other language-basics is also possible, for this example we applied xxx
to run simple C++ programs:

```cpp
#include <iostream>
using namespace std;

int main() {
    int a = 120;
    int rslt = 0;
    for(int i=1; i<a; ++i) {
        rslt += i;
        cout << "rslt: " << rslt << endl;
    }
    cout << "final result = " << rslt << endl;
    return 0;
}
```
<script>
  var output = "";
  JSCPP.run(`{X}`, "", {stdio: {write: s => { output += s.replace(/\n/g, "<br>");}}});
  output;
</script>

#### Python

Running a Python-program with xxx:

```python
def hello(i):
  for _ in range(i):
    print "Hello World"

hello(12)
```
<script>
var output = "";

function builtinRead(x) {
    if (Sk.builtinFiles === undefined || Sk.builtinFiles["files"][x] === undefined)
            throw "File not found: '" + x + "'";
    return Sk.builtinFiles["files"][x];
}

Sk.pre = "output";
Sk.configure({output: e => {output += e;}, read: builtinRead});

var myPromise = Sk.misceval.asyncToPromise(function() {
   return Sk.importMainWithBody("<stdin>", false, `{X}`, true);
});
myPromise.then(function(mod) {
   console.log('success');
},
   function(err) {
   console.log(err.toString());
});
output;
</script>



#### Prolog

See the implementation details at: https://curiosity-driven.org/prolog-interpreter


** Load Database and Rules: **

```prolog
exists(A, list(A, _, _, _, _)).
exists(A, list(_, A, _, _, _)).
exists(A, list(_, _, A, _, _)).
exists(A, list(_, _, _, A, _)).
exists(A, list(_, _, _, _, A)).

rightOf(R, L, list(L, R, _, _, _)).
rightOf(R, L, list(_, L, R, _, _)).
rightOf(R, L, list(_, _, L, R, _)).
rightOf(R, L, list(_, _, _, L, R)).

middle(A, list(_, _, A, _, _)).

first(A, list(A, _, _, _, _)).

nextTo(A, B, list(B, A, _, _, _)).
nextTo(A, B, list(_, B, A, _, _)).
nextTo(A, B, list(_, _, B, A, _)).
nextTo(A, B, list(_, _, _, B, A)).
nextTo(A, B, list(A, B, _, _, _)).
nextTo(A, B, list(_, A, B, _, _)).
nextTo(A, B, list(_, _, A, B, _)).
nextTo(A, B, list(_, _, _, A, B)).

puzzle(Houses) :-
    exists(house(red, english, _, _, _), Houses),
    exists(house(_, spaniard, _, _, dog), Houses),
    exists(house(green, _, coffee, _, _), Houses),
    exists(house(_, ukrainian, tea, _, _), Houses),
    rightOf(house(green, _, _, _, _), house(ivory, _, _, _, _), Houses),
    exists(house(_, _, _, oldgold, snails), Houses),
    exists(house(yellow, _, _, kools, _), Houses),
    middle(house(_, _, milk, _, _), Houses),
    first(house(_, norwegian, _, _, _), Houses),
    nextTo(house(_, _, _, chesterfield, _), house(_, _, _, _, fox), Houses),
    nextTo(house(_, _, _, kools, _),house(_, _, _, _, horse), Houses),
    exists(house(_, _, orangejuice, luckystike, _), Houses),
    exists(house(_, japanese, _, parliament, _), Houses),
    nextTo(house(_, norwegian, _, _, _), house(blue, _, _, _, _), Houses),
    exists(house(_, _, water, _, _), Houses),
    exists(house(_, _, _, _, zebra), Houses).

solution(WaterDrinker, ZebraOwner) :-
    puzzle(Houses),
    exists(house(_, WaterDrinker, water, _, _), Houses),
    exists(house(_, ZebraOwner, _, _, zebra), Houses).
```
<script>
var rules = parser(lexer(`{X}`)).parseRules();
window['prolog_db'] = new Database(rules);

"database loaded";
</script>

** Query: ( it may take some time ;-) ) **

```prolog
solution(WaterDrinker, ZebraOwner)
```
<script>
var rslt = "";

var goal = parser(lexer(`{X}`)).parseTerm();

for (var item of window.prolog_db.query(goal)) {
    rslt += "Yes: " + item + "<br>";
}

if (rslt === "") {
   'No';
} else {
   rslt;
}
</script>

## Quizzes

Quizzes are an essential element of every online course for students to reflect
and test their knowledge. Lia currently supports three different types of
quizzes which can be tweaked, if required.

### Text Inputs

                                  --{{0}}--
A text input field is defined simply by a newline and two brackets around the
solution word, value or sentence. In the depicted example, the word solution is
the solution. If you enter something else, the check will fail.

Markdown-format: `[[solution]]`

Please enter the word * "solution" * into the text-field!

    [[solution]]

### Single-Choice

                                  --{{0}}--
A single choice quiz can be defined with parenthesis within brackets and an X,
which marks the only correct answer option. The additional text is Lia-Markdown
again.

Markdown-format:

``` markdown
    [( )] Wrong
    [(X)] This is the **correct** answer
    [( )] This is ~~wrong~~ too!
```

Only one element can be selected!

    [( )] Wrong
    [(X)] This is the **correct** answer
    [( )] This is ~~wrong~~ too!


### Multiple-Choice

                                  --{{0}}--
A multiple choice quiz can be defined with brackets within brackets and an X,
which are used to mark the correct answer option. In contrast to single choice
quizzes, there can be multiple selected choices or no one, which is also allowed.

``` markdown
    [[ ]] Do not touch!
    [[X]] Select this one ...
    [[X]] ... and this one too!
    [[ ]] also not correct ...
```

Multiple of them can be selected, or all, or none of them ...

    [[ ]] Do not touch!
    [[X]] Select this one ...
    [[X]] ... and this one too!
    [[ ]] also not correct ...

### Hints

                                  --{{0}}--
To any type of quiz you can add as many hints as you want, which are revealed in
order by clicking onto the question mark.

Markdown-format:

``` markdown
    [[super]]
    [[?]] another word for awesome
    [[?]] not great or mega
    [[?]] hopefully not that bad
    [[?]] there are no hints left
```

A text input with additional hints:

    [[super]]
    [[?]] another word for awesome
    [[?]] not great or mega
    [[?]] hopefully not that bad
    [[?]] there are no hints left


### Solution

                                   --{{0}}--
And finally, some quizzes might require some more explanations, if they are
solved or not. That is why, with additional three opening and three closing
brackets you mark the beginning and the end of your solution, which can contain
multiple paragraphs, formulas, program code, videos, etc as well as effects (see
therefor the next section).

Markdown-format:

``` markdown
    [[super]]
    [[?]] hint 1
    [[?]] hint 2
    [[[

                                {{1}}
You are right, super was the correct answer again

* {{2}}{{super}} as an effect
* $\sum x + 3$
* terra

![image](https://upload.wikimedia.org/wikipedia/commons/d/d0/Creative-Tail-Animal-lion.svg)

]]]
```

A quiz with hints and a revealed result.

    [[super]]
    [[?]] hint 1
    [[?]] hint 2
    [[[

                                    {{1}}
You are right, super was the correct answer again

* {{2}}{{super}} as an effect
* $\sum x + 3$
* terra

![image](https://upload.wikimedia.org/wikipedia/commons/d/d0/Creative-Tail-Animal-lion.svg)

]]]

## Effects

There are currently three types of effects, that are supported by liaScript:

1. Inline effects
2. Block effects
3. and a narrator

Every effect is defined by two braces around one or two numbers `{{1-2}}`, which
marks the order of their appearance. The second and optional number defines, at
which step the element becomes invisible again.

### Inline Effects

                                   --{{0}}--
Inline effects can be used in nearly all liaScript elements, as already
mentioned, the first number within curly braces defines the number of appearance
while the second part defines those Markdown elements that should be revealed
step wise. If you use 0, then the effect will be revealed immediately.

Use this to highlight important facts and to structure your slides (multiple
effects can be combined, due to the usage of equal numbers):

``` markdown
* no effect here
* but in this line {{1}}{{show *** first ***}}
* as well as this one {{1-2}}{{show *** first ***}}, which contains two effects
  {{2}}{{![image](https://upload.wikimedia.org/wikipedia/commons/d/d0/Creative-Tail-Animal-lion.svg)}}
```

* no effect here
* but in this line {{1}}{{show *** first ***}}
* as well as this one {{1-2}}{{show *** first ***}}, which contains two effects
  {{2}}{{![image](https://upload.wikimedia.org/wikipedia/commons/d/d0/Creative-Tail-Animal-lion.svg)}}


### Animations

                                   --{{0}}--
To define animations and transitions, you can use the animate.css notation,
simply place an animation definition within the comment tag after the effects,
as it is done within the examples.


See https://daneden.github.io/animate.css for more animation effects.

``` markdown
* {{0}}{{ *bounce* }} <!-- class = "animated infinite bounce" style = "animation-delay: 5s;" -->
* {{1-2}}{{zoomIn}} <!-- class = "animated zoomIn" -->
* {{2-3}}{{zoomOut}} <!-- class = "animated zoomOut" -->
* {{3}}{{![image](https://upload.wikimedia.org/wikipedia/commons/d/d0/Creative-Tail-Animal-lion.svg)}} <!-- class = "animated rubberBand" -->
```

* {{0}}{{ *bounce* }} <!-- class = "animated infinite bounce" style = "animation-delay: 5s;" -->
* {{1-2}}{{zoomIn}} <!-- class = "animated zoomIn" -->
* {{2-3}}{{zoomOut}} <!-- class = "animated zoomOut" -->
* {{3}}{{![image](https://upload.wikimedia.org/wikipedia/commons/d/d0/Creative-Tail-Animal-lion.svg)}} <!-- class = "animated rubberBand" -->

### Block Effects

                                   --{{0}}--
Block effects as animations are defined similarly to inline effects, just with
one additional newline after the effect definition. The following Markdown block
is then entirely associated with this effect.

                                   --{{1}}--
You can combine blocks by enclosing them into two lines of equality signs, as
you can see from the examples below, an effect can also contain further effects.


``` markdown
                               {{1-3}}
This is an example for a *single* block effect.

                               {{2-4}}
================================================================================

This is an example for a ... wait a second {{3 rubberBand}}{{**multi**}} ...
block effect.

* alpha
* beta
* gamma

================================================================================
```

                                  {{1-3}}
This is an example for a *single* block effect.

                                  {{2-4}}
================================================================================

This is an example for a ... wait a second {{3}}{{**multi**}} ...
block effect.

* alpha
* beta
* gamma

================================================================================

                                --{{4}}--
You can put spaces before the definition of a block effect, to prevent github
and others from adding the definition to a Markdown paragraph, and thus, to
render the script properly.

### Narrator
<!--
language: en_UK

narrator: UK English Male
-->


1. we are using the text-to-speech engine of https://responsivevoice.org
2. the narrator voice must be defined within the initial comment of a script
3. use `--{{id}}--` to indicate what is spoken and when

``` markdown
                                --{{1}}--
The entire ***Markdown*** paragraph right below the effect definition in double
minus notation is sent to responsivevoice to speak the text out loud. If you
click on the ear button at the navigation panel, then this paragraph gets
rendered at the place where it is defined.

                               --{{3 <!-- Deutsch Female-->}}--
Markdown ist eine vereinfachte Auszeichnungssprache, die von John Gruber und
Aaron Swartz entworfen und im Dezember 2004 mit Version 1.0.1 spezifiziert ...

                               --{{4 <!-- Russian Female-->}}--
Первоначально создан в 2004 году Джоном Грубером (англ. John Gruber) и Аароном
Шварцем. Многие идеи языка были позаимствованы из существующих соглашений ...
```

                                --{{1}}--
The entire ***Markdown*** paragraph right below the effect definition in double
minus notation is sent to responsivevoice to speak the text out loud. If you
click on the ear button at the navigation panel, then this paragraph gets
rendered at the place where it is defined.

                                --{{2}}--
The narrator voice is defined within the initial comment, but you can reset this
for the entire section, by adding such a definition directly after the title
tag, or you can add a comment directly after the comment identifier to let your
script talk in different languages. Proceed and listen ;-)

                                --{{3 <!-- Deutsch Female -->}}--
Markdown ist eine vereinfachte Auszeichnungssprache, die von John Gruber und
Aaron Swartz entworfen und im Dezember 2004 mit Version 1.0.1 spezifiziert
wurde. Ein Ziel von Markdown ist, dass schon die Ausgangsform ohne weitere
Konvertierung leicht lesbar ist.

                               --{{4 <!-- Russian Female -->}}--
Первоначально создан в 2004 году Джоном Грубером (англ. John Gruber) и Аароном
Шварцем. Многие идеи языка были позаимствованы из существующих соглашений по
разметке текста в электронных письмах. Реализации языка Markdown преобразуют
текст в формате Markdown в валидный, правильно построенный XHTML и заменяют
 левые угловые скобки («<») и амперсанды («&») на соответствующие коды сущностей.


## Charts

In many cases, a diagram is only used to present some kind of signal paths,
some primitive functions, some clusters or point clouds.

You can still generate images, but why not applying some basic kind of ASCII-art
to solve the most common tasks.

### Line-Plots 1

Markdown-format:

```markdown
                                      diagram titel
    1.5 |           *
        |
      y |        *      *
      - |      *          *
      a |     *             *       *
      x |    *                 *
      i |   *
      s |  *
        | *                              *        *
      0 +------------------------------------------
         2.0              x-axis                100
```

Result:

                            diagram titel
    1.5 |           *
        |
      y |        *      *
      - |      *          *
      a |     *             *       *
      x |    *                 *
      i |   *
      s |  *
        | *                              *        *
      0 +------------------------------------------
         2.0              x-axis                100


### Line-Plots 2

                                --{{0}}--
All diagram titles, labels, limits are optional, and if you do not define
limits, then the min max values 0 and 1 are used by default.

Markdown-format:

```markdown
         1 |                   *                       *
           |               *       *               *       *
           |*             *         *             *         *
    y-axis | *           *           *           *           *
           |  *         *             *         *             *
           |   *       *               *       *               *
           |       *                       *                      *
        -1 +--------------------------------------------------------
```

         1 |                   *                       *
           |               *       *               *       *
           |*             *         *             *         *
    y-axis | *           *           *           *           *
           |  *         *             *         *             *
           |   *       *               *       *               *
           |       *                       *                      *
        -1 +--------------------------------------------------------


### Multi-Line-Plots

                             --{{0}}--
Next to stars, you can also use any kind of character to define another line,
where the character defines the color. For example an r marks the color red and
a b the color blue.

Markdown-format:

```markdown
    | r          *
    |    r
    |       r *      *
    |        * r       *
    |       *      r      *       *
    |      *            r    *
    |     *                 r
    |   *                          r
    | *                              *    r    *
    +-------------------------------------------
```

    | r          *
    |    r
    |       r *      *
    |        * r       *
    |       *      r      *       *
    |      *            r    *
    |     *                 r
    |   *                          r
    | *                              *    r    *
    +-------------------------------------------



### Dot-Plots

                                 --{{0}}--
If the there are more point with the same character for one x-value, then only
dots are plotted. And by using upper and lower case characters you can also
define the size of the dots.

Markdown-format:

```markdown
    10 |        rrrrrrrrrrrr    x
       |    rrrrrrrrrrrrrrrr
       |  rrrrrrrrrrrrrrrrr  BBBBB
       | rrrrrrrrrrrrrrrr  BBBBBBBB
       |rrrrrrrrrrrrrrr  BBBBBBBBBBB
       |rrrrrrrrrrrrr  BBBBBBBBBBBBB
       |rrrrrrrrrrr  BBBBBBBBBBBBBBB
       | rrrrrrrr  BBBBBBBBBBBBBBBB
       |  rrrrr  BBBBBBBBBBBBBBBBB
       |        BBBBBBBBBBBBBBBB
       |   x    BBBBBBBBBBBBB
       +-----------------------------
         0                           2
```


    10 |        rrrrrrrrrrrr    x
       |    rrrrrrrrrrrrrrrr
       |  rrrrrrrrrrrrrrrrr  BBBBB
       | rrrrrrrrrrrrrrrr  BBBBBBBB
       |rrrrrrrrrrrrrrr  BBBBBBBBBBB
       |rrrrrrrrrrrrr  BBBBBBBBBBBBB
       |rrrrrrrrrrr  BBBBBBBBBBBBBBB
       | rrrrrrrr  BBBBBBBBBBBBBBBB
       |  rrrrr  BBBBBBBBBBBBBBBBB
       |        BBBBBBBBBBBBBBBB
       |   x    BBBBBBBBBBBBB
       +-----------------------------
         0                           2


## Surveys

                             --{{0}}--
A script should not define a one-way road to the student! So surveys are
required.

### Text-Inputs

Similar to text-quizzes, use the following syntax to define a text-survey, where
the number of underlines defines the presented line numbers:

   `[[___ ___ ___ ___]]`

What is your opinion on ... :

    [[___ ___ ___ ___]]

### Single Choice Vector

                              --{{0}}--
And also this kind of survey is similar to a single choice quiz, but in this
case numbers within parenthesis are used to define some kind of variable
identifier. That is why they do not have to be in order.

```markdown
    [(1)] option 1
    [(2)] option 2
    [(3)] option 3
    [(0)] option 0
```

You can only select one option:

    [(1)] option 1
    [(2)] option 2
    [(3)] option 3
    [(0)] option 0


### Multi Choice Vector

                               --{{0}}--
Similar to multi-choice quizzes, you can define multi-choice survey vectors with
a number in double square brackets. But, and this is also possible for all other
kinds of surveys you can define some kind of variable name with a starting colon.

```markdown
    [[:red]]         is it red
    [[:green]]       green
    [[:blue]]        or blue
    [[:dark purple]] no one likes purple ( last chance ;-) )
```

Select some of your favored colors!

    [[:red]]         is it red
    [[:green]]       green
    [[:blue]]        or blue
    [[:dark purple]] no one likes purple ( last chance ;-) )

### Single Choice Matrix

                              --{{0}}--
For defining survey blocks you only have to a header row, whose definition is
also used by the trailing rows.

Markdown-format:

```markdown
    [(:totally)(:agree)(:unsure)(:maybe not)(:disagree)]
    [                                                  ] liaScript is great?
    [                                                  ] I would use it to make online **courses**?
    [                                                  ] I would use it for online **surveys**?
```

    [(:totally)(:agree)(:unsure)(:maybe not)(:disagree)]
    [                                                  ] liaScript is great?
    [                                                  ] I would use it to make online **courses**?
    [                                                  ] I would use it for online **surveys**?

### Multi Choice Matrix

                               --{{0}}--
I guess, multi-choice blocks are self-explanatory...

Markdown-format:

```markdown
    [[1][2][3][4][5][6][7]]
    [                     ] question 1 ?
    [                     ] question 2 ?
    [                     ] question 3 ?
```

Result:

    [[1][2][3][4][5][6][7]]
    [                     ] question 1 ?
    [                     ] question 2 ?
    [                     ] question 3 ?


## Future Work

* Better integration with github/gitlab and the versioning of courses
* Free Integration of JavaScript and Elm resources
* Automagically analyzed surveys
* Integration of WebGl and a 3D navigation
* Inline function-plotter

## Contributors and Credit


{{1}}{{<h1> André Dietrich  </h1>}} <!-- class = "animated fadeInUpBig" -->

--{{1}}--
Programming paradigm experimenter and creator of liaScript and SelectScript...



{{2}}{{<h1> Sebastian Zug   </h1>}} <!-- class = "animated fadeInUpBig" -->

--{{2}}--
The mind in the dark and the man behind the eLab-project ...



{{3}}{{<h1> Fin Christensen </h1>}} <!-- class = "animated fadeInUpBig" -->

--{{3}}--
CSS and Web development enthusiast, outstanding git user ...


{{4}}{{<h1> Martin Koppehel </h1>}} <!-- class = "animated fadeInUpBig" -->

--{{4}}--
Hardware-architect and fully Fullstack developer ...


{{5}}{{<h1> Leon Wehmeier   </h1>}}<!-- class = "animated fadeInUpBig" -->

--{{5}}--
Coordinator and embedded development guru ...


{{6}}{{<h1> Karl Fessel     </h1>}} <!-- class = "animated fadeInUpBig" -->

--{{6}}--
Embedded systems developer, creator or arduinoview, and Markdown evangelist ...
