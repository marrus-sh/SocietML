# SocietML #

Markup for sociality.

##  Markup:  ##

There are currently two markup types supported by SocietML: FB and MSG.
To create a SocietML element, simply set the `data-societml-type` attribute to either `fb` or `msg` (case-insensitive) on a normal HTML element.
This element will henceforth be referred to as the "parent element"; we recommend using `<blockquote>`.

Each markup type has its own syntax:

###  type-FB  ###

(Coming soon!)

Type-FB represents a longform social-media post.

###  type-MSG  ###

Type-MSG represents messaging; for example in a text-message or chatroom setting.
The only permitted child elements of a type-MSG parent are `<p>` elements.
The `data-societml-name` attribute represents the person talking; each person should be represented by exactly one `data-societml-name` attribute.

On the first `<p>` element with a given `data-societml-name` attribute, a few additional parameters may be set: `data-societml-bg` and `data-societml-text`.
These associate background and text colours with the name in question.
These can only be set the first time a name appears, and cannot be changed later.

Here is a sample type-MSG SocietML element:

```html
<blockquote data-societml-type="msg">
    <p data-societml-name="Person 1" data-societml-bg="#E6E5EB" data-societml-text="black">Hey what's up?</p>
    <p data-societml-name="Person 2" data-societml-bg="#1289FD" data-societml-text="white">Not much yo.</p>
    <p data-societml-name="Person 1">Only specify data-societml-bg and data-societml-text the first time someone's name comes up.</p>
    <p>If data-societml-name is omitted it defaults to the second-previous one.</p>
</blockquote>
```

##  Processing:  ##

The `societml.js` file contains a script to render SocietML elements.
Simply include this script in your file and run `SocietML.parse()`.
If you only want to process a single element or document, `SocietML.parse()` will take this as a parameter; otherwise, it will process `document.documentElement`.
