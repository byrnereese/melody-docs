# An Introduction to the Melody Templating Language

To make full use of the Melody platform as a designer or a developer, it is essential to become familiar with the markup "language" used to generate a web site, or MTML (Melody Templating Markup Language). 

To many, the thought of having to learn a new "language" can at least be daunting, and at worse, cause you them to run in panic. This guide however will help reveal that the Melody template language is not only *easy* to learn and read, but it also has many other benefits, including:

* It is robust - MTML is a programming language in its own right in that one can *do* and produce just about anything with it. All of the logical and conditional constructs one may be used to in PHP, for example, are also found in the Melody templating language. 

* It is secure - unlike PHP and other programming languages popular with web site developers, MTML is constrained in a number of important ways that help prevent others from inflicting harm upon your web site or servers. 

* It is human-readable - unlike conventional programming languages that utilize forms and syntaxes created by computer scientists, MTML uses a syntax optimized for human-readability and one designed to be interwoven in HTML. 

* It is extensible - virtually any language can be augmented with functions to encapsulate code with easy-to-remember name, but Melody allows developers to extend the core semantics of the language itself with relative ease. Oh, and it *also* supports functions if that is your cup of tea.

In the following sections, you will introduced to the basics of the MTML syntax. Having this familiarity will help you a great deal when later we begin to employ the language to create more advanced features for your web site.

## Basic Syntax

MTML is a "markup language" which provides a simple way of annotating text in order to customize its appearance and content. If you are at all familiar with HTML, perhaps the single most popular markup language in the word, then you are well on your way to understanding MTML. Let's take a look at a quick example.

In HTML, if you want text to appear as **bold**, then you annotate, or "markup" your text with a simple HTML tag called `strong`. This is what it looks like:

    This text is <strong>bold</strong>.

As you can see the word "bold" is surrounded by an opening and closing "strong" tag which instructs the browser to display the text they encapsulate accordingly. 

MTML is really no different, except that it is a language designed to output text, not *format* text. Let's take a quick look at a simple example:

    My blog's name is <mt:BlogName>.

When Melody processes this template code, it will substitute the text `<mt:BlogName>` with -- you guessed it, the name of the blog. So if the name of your blog is, let's say, "The Best Blog," then the text above will be rendered as:

    My blog's name is The Best Blog.

Furthermore, the two markup languages (HTML and MTML) can be used together:

    My blog's name is <em><mt:BlogName></em>.

And by this point, I am confident you can figure out what the output would be. Right?

**Tag Types**

In Melody there are effectively two types of template tags:

* Function Tags

* Block or Container Tags

"Function tags," like the one seen above, are atomic in that they do not contain, or encapsulate text in any way. When Melody parses a function tag, it replaces a single tag with a single value, the way `<mt:BlogName>` is replaced with "My Best Blog."

"Container tags," sometimes referred to as "block tags" encapsulate or contain text and other tags. The most common container tag in Melody is the `<mt:if>` tag, which is a special type of container tag called a "conditional" tag. 

    <mt:if tag="AuthorName" eq="Byrne">
      This post is by Byrne-Baby-Byrne. 
    </mt:if>

As you can see in the example above, the tag consists of an opening tag `<mt:if>` and a closing tag `</mt:if>`. In between those two tags text can be found, or in other words, the text is "contained." Hence the name. 

**Syntax Conventions**

Melody template tags all have a few syntax rules. They are:

* template tags are case insensitive.
* template tags must be preceded by a prefix (most often the two character string "mt"), with an optional colon delimiting the prefix and the tag name, e.g. "mt:Foo" and "mtFoo."
* template tags must be bounded by either "<" and ">", or "<$" and "$>".

Within that simple ruleset is a great deal of latitude with regards to formatting. As a result and because Melody's templating language has been around for so many years it has supported many alternate syntaxes and coding conventions. As a result, depending upon the year or author of a plugin, theme or a piece of documentation you may observe many different styles in which template tags are written. For example, the following template tags are all functionally equivalent for a hypothetical tag named "FooBar":

* `<MTFooBar>`
* `<$MTFoobar$>`
* `<mt:fooBar>`
* `<$mt:foobar$>`
* `<MT:FOOBAR>`

At the project's inception, the Melody community decided that the plethora and variability of these styles was confusing. Thus, they adopted the following preferred coding convention for template tags:

* All tags will utilize the lowercase prefix of "mt:".
* All tag names will use mid-caps, e.g. MelodyIsGreatSoftware.

Then, to assist in the scan-ability and readability of template code:

* Function tags will be bounded by "<$" and "$>".
* Container tags will be bounded by "<" and ">".

While Melody's template tag parser is very forgiving with regards to the range of styles it will accept, all Melody users are strongly encouraged to use the coding convention above.

## Conditional Tags

A conditional container or block tag is a tag whose contents are evaluated and output only if a certain condition is met. Conditional expressions are important because in the world of programming as in the world of Melody templates, it is within conditional tags where all the "magic" happens.

The secret most programmers don't want you to know is that the "magic" of their program is not hard to understand, or even hard to replicate. In fact, just about anyone can wrap their head around it much like anyone who drives a car can easily get themselves from point A to point B:

> To get from Oakland to San Francisco I should take the 580 to the Bay Bridge, unless there is an accident on the bridge. Then I should take the 880 East to the 92, cross the San Mateo bridge and then take the 101 North. Unless things are *really* screwed up, then I will take BART. Oh wait, I forgot, I have a doctor's appointment; I will work from home today.

This example illustrates why some programmers refer to conditional statements by another name: "flow control." 

The most primitive conditional expression that exists in programming is the "if-then-else" block. Let's look at a quick example:

    <p>Directions from Oakland to the City:</p>
    <mt:if name="doctors_appointment"> 
      Work from home.
    <mt:else>
      <mt:if name="traffic" eq="really bad">
        Take BART.
      <mt:else name="traffic" eq="bad">
        Take 880E to 92W to 101N.
      <mt:else>
        Take the Bay Bridge, dummy.
      </mt:if>
    </mt:if>
    
The example above illustrates that if-statements can be nested and compounded in a number of ways to create huge variability in what is output to the page. 

The `<mt:if>` tag is the most commonly used tag in the Melody templating language. To learn more about its many facets and abilities, you are encouraged to read the official reference documentation for the template tag:

     http://bit.ly/mt-if

There is more to this family of tags though than just `<mt:if>`. There are in fact a huge number of conditional tags, most of which can be identified easily by having one of these words within its name:

* If
* Is
* Unless
* Has
* Contains

For example:

* EntryIfTagged - evaluate contained text if the current entry has a specific tag.
* IfRegistrationRequired - evaluate contained text if the blog administrator requires all commenters to have an account.
* IfCommenterTrusted - evaluate contained text if the current commenter has been flagged as "trusted."

Hopefully what these examples illustrate that Melody takes much of the complexity out of its many template tags by giving them simple and self-explanatory names. In most cases in fact, you should find, that most templates are actually pretty easy to read and most importantly, *understand.*

## Loops 

Another type of container or block tag is the loop tag. A loop tag outputs the results of rendering its contents as many times as the loop is iterated over. Once a designated condition has been met, the loop is terminated and Melody will begin processing the rest of the template. 

The most common set of loop tags are the ones designed to process a list of objects, like entries and comments. Here are a few of them:

* `<mt:Assets>`
* `<mt:Authors>`
* `<mt:Blogs>`
* `<mt:Categories>`
* `<mt:Comments>`
* `<mt:Entries>`
* `<mt:Folders>`
* `<mt:Pages>`

And those are just a hand full, but you get the idea. Each of the tags operates in more or less the same way. For example, to display a list of the last ten comments submitted in the system, you would use the following:

    <ul>
    <mt:Comments lastn="10">
      <li><$mt:CommentBody$></li>
    </mt:Comments>
    </ul>

The above code sample is straight forward, but it is imperfect in that it will *always* output a `<ul>` and `</ul>` tag even if there are no comments in the system. Ideally, you would only output the `ul` tags if an actual list was present. Luckily you are free to combine conditional and loop tags, as well as utilize a special set of meta loop variables maintained for you by Melody to achieve the result we are looking for:

    <mt:Comments lastn="10">
    <mt:if name="__first__"><ul></mt:if>
      <li><$mt:CommentBody$></li>
    <mt:if name="__last__"></ul></mt:if>
    </mt:Comments>

The loop variables referenced, `__first__` and `__last__` evaluate to true only for the first and last time through the loop respectively. Therefore the `ul` tags will only be output if there is at least one comment. Below is a list of all such meta loop variables that are managed for you by Melody for virtually every loop tag in the system:

**Meta Loop Variables**

`__first__` : true when the current loop iteration is the first time through the loop, false otherwise.
* `__last__` : true when the current loop iteration is the last time through the loop, false otherwise.
* `__odd__` : true when the current loop iteration is an odd one (1st, 3rd, 5th, 7th, etc), false otherwise.
* `__even__` : true when the current loop iteration is an even one (2nd, 4th, 6th, 8th, etc), false otherwise.
* `__counter__` : returns an integer representing how many times the loop has been iterated over (starting with 1).

In the examples above you also saw the use of the `lastn` attribute to instruct the loop to only display the last ten comments in the system. The `lastn` attribute is one of the many tags supported by most loop tags in Melody, which are listed below:

**Common Arguments**

* `lastn` : an integer which limits the maximum size of the list returned by the tag by the designated number.
* `offset` : an integer used in conjunction with `lastn`, to instruct the loop to skip the first n items in the list.
* `sort_by` : a string representing the name of the column by which to sort the results (e.g. `created_on`).
* `sort_order` : a string, either 'ascend' or 'descend' that controls whether the tag returns results ordered from greatest to lowest, or from lowest to greatest.

There are actually a great many arguments supported by all tags, but the ones above are the ones you will use most frequently. You are encouraged to read more about these arguments by consulting the reference manual for the specific tag you are using. 

## Variables

Believe it or not, you are well on your way to becoming a *programmer*. You never thought it possible did you? In the sections above you have learned about the mechanisms used to "control the flow" of a template - to conditionally process one set of tags or another. This is essential as it will allow you to customize the look and feel of any page of your web site depending upon who is looking at the page, what category they might be in, etc. 

Another critical aspect to working with templates is learning how to work with variables. To a seasoned programmer, variables are second nature to them. But to someone less technical, like a designer, this abstraction may be a little confusing. So let's begin by first understanding what a variable is. 

If you ever studied algebra, then chances are that you are already a master of this concept, you just haven't applied it in this context. In case you aren't though, here are the basics of variables in algebra. 

No one should be stumped by this simple equation:

    x + 3 = ?

Or in other words, the value of the equation varies depending upon the value of x, thus "x" is your variable. Change the value of x and you change the output of the equation.

Thus, one can think of variables as "holding a value." Their value is not explicit, rather their value has the potential to change, and based upon the value at any given time, the behavior of the application can change as a result. 

### Working with Variables

In working with variables there are only two operations one can perform: getting a value and setting a value. 

**Reading Variables**

To output the value contained by a variable in Melody, one used the `<mt:var>` tag. The syntax is simple:

    <$mt:var name="my_variable"$>

If this were to be placed in a template, and if the variable `my_variable` existed, then in place of this tag will be placed its value.

**Setting Variables**

Setting the value of a variable is done using the exact same tag as getting a variable: `<mt:var>`, however an additional attribute is taken as input. 

    <$mt:var name="my_variable" value="123"$>

When setting the value of a variable nothing is output to the screen or file. The operation is done silently in this respect. Here is an example to demonstrate. The following template code:

    <ul>
      <li><$mt:var name="foo"$></li>
    <$mt:var name="foo" value="ABC"$>
      <li><$mt:var name="foo"$></li>
    <$mt:var name="foo" value="123"$>
      <li><$mt:var name="foo"$></li>
    </ul>

Will output:

    <ul>
      <li></li>
      <li>ABC</li>
      <li>123</li>
    </ul>

You will notice that the first time the value of "foo" is retrieved that nothing is output. That is because it has not yet been assigned a value at the time.

Sometimes, the value you wish to assign to a variable is more complex than a simple number of string. Sometimes the value is derived by combining the output of multiple tags used together. In this case, you would use the template tag called `<mt:setvarblock>` like so:

    <mt:setvarblock name="blog_link">
      <a href="<$mt:BlogURL$>"><$mt:BlogName$></a>
    </mt:setvarblock>
    <h1><$mt:var name="blog_link"$></h1>

Which will output:

    <h1><a href="http://openmelody.org">Melody</a></h1>

**Variable Interpolation**

Sometimes you need to reference the value a variable holds within the context of another template tag. For example, let's say you have a variable called `entry_count` which holds an integer which determines how many entries to output to the screen. This is possible in Melody, but the syntax is not what many might expect. For example, while logical, the following would be *incorrect*:

    <$mt:var name="entry_count" value="5"$>
    <mt:Entries lastn="<$mt:var name="entry_count"$>">
      <li><$mt:EntryTitle$></li>
    </mt:Entries>

This example above is an illustration of the concept of "variable interpolation." When evaluating variables in this way, the proper syntax is to use a shorthand form of the variable as follows:

    <$mt:var name="entry_count" value="5"$>
    <mt:Entries lastn="$entry_count">
      <li><$mt:EntryTitle$></li>
    </mt:Entries>

## Functions and Custom Subroutines

Another concept many programmers are familiar with and would expect from any language they work with is the function. Functions provide programmers with a way of encapsulating code they want to run over and over again into a shorthand form. Again, if you are familiar with algebra, then this is a concept you are already familiar with. Let's take a look. Remember that equation we used above?

    x + 3 = ?

This equation can be expressed as a function like so:

    f(x) = x + 3

Allowing for one to refer to it in a shortened form, and evaluate it over and over again:

    f(3) = 6
    f(1) = 4
    f(45) = 48

Get the idea? You can even have functions that take multiple inputs:

    f(x,y) = (x + 10) - (y + 3)

To allow for this shortened form:

    f(1,2) = 6
    f(23,10) = 20

Functions in programming and in Melody templates work *exactly* the same way, except that a slightly different syntax is used. For example, suppose we wanted a function that would output the last *n* entries that contain a tag you specify. This is what it would look like:

    <mt:setvartemplate name="lastn_entries">
      <mt:Entries lastn="$count" tag="$tag">
        <mt:if name="__first__"><ul></mt:if>
        <li><$mt:EntryTitle$></li>
        <mt:if name="__last__"></ul></mt:if>
      </mt:Entries>
    </mt:setvartemplate>

Once the function has been declared via the `<mt:setvartemplate>` tag, it can be invoked and processed over and over again like so:

    <$mt:var name="lastn_entries" count="4" tag="foo"$>
    <$mt:var name="lastn_entries" count="2" tag="bar"$>
    <$mt:var name="lastn_entries" count="3" tag="baz"$>

This short hand is much more efficient and far less verbose than having to cut and paste the `<mt:Entries>` block repeatedly throughout your template code.

## Modifiers

One topic that should also be addressed is that of template tag "modifiers." Template tag modifiers are attributes that can be applied to *any* template tag in Melody, and result in transforming the output of that tag in someway. Here is a list of some of the more common modifiers used in Melody:

* `capitalize` - force the contents of the tag to uppercase.
* `encode_html` - convert special characters reserved for HTML to their unicode equivalent.
* `regex_replace` - replace text in the tag with other text you specify.
* `trim` - remove unwanted whitespace.

For example, the template code below:

    <$mt:var name="foo" value="I love Movable Type"$>
    <$mt:var name="foo" capitalize="1"$>

Will output:

    I LOVE MOVABLE TYPE

Tag modifiers can also be chained together, such that the following:

    <$mt:var name="foo" value="I love Movable Type"$>
    <$mt:var name="foo" regex_replace="/Movable Type/i","Melody"
        capitalize="1"$>
 
Would output:

    I LOVE MELODY  

When chaining modifiers together, it is important to note that they will be processed in the order with which they are specified. For example:

    <$mt:var name="foo" value="I love Movable Type"$>
    <$mt:var name="foo" capitalize="1"
        regex_replace="/Movable Type/i","Melody"$>

Will produce:

   I LOVE Melody

In this case, "Melody" is not capitalized because the string "I love Movable Type" is capitalized and *then* the (case-insenstive) string substitution of "Melody" for "Movable Type" occurs. 

For a complete list of template tag modifiers supported by Melody, consult the URL below:

http://www.movabletype.org/documentation/appendices/modifiers/
