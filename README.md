# comment-patterns

> A list of comment-patterns for different languages

This module contains an extract of the [language-database of `groc`](http://nevir.github.io/groc/languages.html)
with information about how single- and multi-line comments are written in different languages.

"abc"

## Usage

```js
var commentPattern = require('comment-patterns');
var p = commentPattern('filename.hbs');

/*
Result:
    {
         name: 'Handlebars',
         nameMatchers: ['.handlebars', '.hbs'],
         multiLineComment: [
             {start: '<!--', middle: '', end: '-->'},
             {start: '{{!', middle: '', end: '}}'}
         ]
    }
*/
```

### [commentPattern](index.js#L30)

Load the comment-pattern for a given file.
The file-language is determined by the file-extension.

**Params**

* `filename` **{string}**: the name of the file    
* `returns` **{object}**: the comment-patterns  

### [.commentPattern.regex](index.js#L70)

Load the comment-regex for a given file. The result contains a regex that matches the comments in the specification. It also has information about which the different capturing groups of an object. For example

Note that only one the groups from `cg.contentStart` to `cg.beforeCode - 1` will have a match.
This depends on the comment-pattern that was used in the comment.

**Params**

* `filename` **{string}**: the name of the file    
* `returns` **{object}**: an object containing regular expressions and capturing-group metadata  

**Example**

```js
{
    regex: /^([ \t]*)(\/\*\*?([\s\S]*?)\*\/|((?:\/\/.*[\r\n]+)+))([\r\n]*)(.*)/gm,
    cg: {
        indent: 1,  // match[1] is the initial indent of the for comment start
        wholeComment: 2,  // match[2] contains the whole comment
        contentStart: 3,  // match[3] and the following contain the contents of the comment
                          // if the match[3] for multiline-comment, match[4] for single-line-comments
        beforeCode: 5,  // match[5] contains the newlines between the end of match[2] and match[6]
        code: 6  // match[6] contains the line-of-code directly following the comment.
     },
    middle: [  // line-start for comment-contents in match[i - cg.contentStart]
        /^\* ?/gm,    // matches the line-start of comments captured in match[3]
        /^\/\/ ?/gm   // matches the line-start of comments captured in match[4]
    ],
    name: "C"  // the name of the language (for debugging purposes)
}
```

## The database

The language-specification can be found in the 
`languages`-directory. There is one file
for each language. The actual databases will be
created from these files on `prepublish`.

### C

* Name-Matchers:  `.c`  `.h` 

* Multi-line comment: `/\/\*\*?/`, `"*"`, `"*/"`

* Single-line comment: `"//"`

### Clojure

* Name-Matchers:  `.clj`  `.cljs` 

* Single-line comment: `";;"`

### CoffeeScript

* Name-Matchers:  `.coffee`  `Cakefile` 

* Multi-line comment: `"###*"`, `/ \*|#/`, `"###"`

* Multi-line comment: `"###"`, `"#"`, `"###"`

* Single-line comment: `"#"`

### C++

* Name-Matchers:  `.cpp`  `.hpp`  `.c++`  `.h++`  `.cc`  `.hh`  `.cxx`  `.hxx` 

* Multi-line comment: `/\/\*\*?/`, `"*"`, `"*/"`

* Single-line comment: `"//"`

### CSharp

* Name-Matchers:  `.cs` 

* Multi-line comment: `/\/\*\*?/`, `"*"`, `"*/"`

* Single-line comment: `"//"`

### CSS

* Name-Matchers:  `.css` 

* Multi-line comment: `/\/\*\*?/`, `"*"`, `"*/"`

### Go

* Name-Matchers:  `.go` 

* Single-line comment: `"//"`

### Handlebars

* Name-Matchers:  `.handlebars`  `.hbs` 

* Multi-line comment: `"<!--"`, `""`, `"-->"`

* Multi-line comment: `"{{!"`, `""`, `"}}"`

### Haskell

* Name-Matchers:  `.hs` 

* Single-line comment: `"--"`

### HTML

* Name-Matchers:  `.htm`  `.html` 

* Multi-line comment: `"<!--"`, `""`, `"-->"`

### Jade

* Name-Matchers:  `.jade` 

* Single-line comment: `"//"`

* Single-line comment: `"//-"`

### Jake

* Name-Matchers:  `.jake` 

* Single-line comment: `"//"`

### Java

* Name-Matchers:  `.java` 

* Multi-line comment: `/\/\*\*?/`, `"*"`, `"*/"`

* Single-line comment: `"//"`

### JavaScript

* Name-Matchers:  `.js` 

* Multi-line comment: `/\/\*\*?/`, `"*"`, `"*/"`

* Single-line comment: `"//"`

### JSON

* Name-Matchers:  `.json` 

### JSP

* Name-Matchers:  `.jsp` 

* Multi-line comment: `"<!--"`, `""`, `"-->"`

* Multi-line comment: `"<%--"`, `""`, `"--%>"`

### LaTeX

* Name-Matchers:  `.tex`  `.latex`  `.sty` 

* Single-line comment: `"%"`

### LESS

* Name-Matchers:  `.less` 

* Single-line comment: `"//"`

### LiveScript

* Name-Matchers:  `.ls`  `Slakefile` 

* Multi-line comment: `/\/\*\*?/`, `"*"`, `"*/"`

* Single-line comment: `"#"`

### Lua

* Name-Matchers:  `.lua` 

* Single-line comment: `"--"`

### Make

* Name-Matchers:  `Makefile` 

* Single-line comment: `"#"`

### Markdown

* Name-Matchers:  `.md`  `.markdown`  `.mkd`  `.mkdn`  `.mdown` 

* File only consists of comments

### Mustache

* Name-Matchers:  `.mustache` 

* Multi-line comment: `"{{!"`, `""`, `"}}"`

### Objective-C

* Name-Matchers:  `.m`  `.mm` 

* Multi-line comment: `/\/\*\*?/`, `"*"`, `"*/"`

* Single-line comment: `"//"`

### Perl

* Name-Matchers:  `.pl`  `.pm` 

* Single-line comment: `"#"`

### PHP

* Name-Matchers:  `.php`  `.php3`  `.php4`  `.php5`  `.fbp` 

* Single-line comment: `"//"`

### Puppet

* Name-Matchers:  `.pp` 

* Single-line comment: `"#"`

### Python

* Name-Matchers:  `.py` 

* Single-line comment: `"#"`

### Ruby

* Name-Matchers:  `.rb`  `.ru`  `.gemspec` 

* Single-line comment: `"#"`

### Sass

* Name-Matchers:  `.sass` 

* Single-line comment: `"//"`

### SCSS

* Name-Matchers:  `.scss` 

* Multi-line comment: `/\/\*\*?/`, `"*"`, `"*/"`

* Single-line comment: `"//"`

### Shell

* Name-Matchers:  `.sh` 

* Single-line comment: `"#"`

### SQL

* Name-Matchers:  `.sql` 

* Single-line comment: `"--"`

### Swift

* Name-Matchers:  `.swift` 

* Multi-line comment: `/\/\*\*?/`, `"*"`, `"*/"`

* Single-line comment: `"//"`

### TypeScript

* Name-Matchers:  `.ts` 

* Multi-line comment: `/\/\*\*?/`, `"*"`, `"*/"`

* Single-line comment: `"//"`

### YAML

* Name-Matchers:  `.yml`  `.yaml` 

* Single-line comment: `"#"`

## Updating the language-database

The language-specifications where initially pulled from the  
[language-database of `groc`](http://nevir.github.io/groc/languages.html).
It may still be good to pull an update
from `groc`, which can be done by the following command:

```bash
npm i -d && npm run-script update-from-groc
```

**Please be careful when doing this: Language-specifications may have been changed manually,
so be careful not to override any changed files.**

## Run tests

Install dev dependencies:

```bash
npm i -d && npm test
```

## Related

[extract-comments](https://github.com/jonschlinkert/extract-comments): Extract code comments from string or from a glob of files.

## Author

**Nils Knappmeier**

+ [github/jonschlinkert](https://github.com/jonschlinkert)
+ [twitter/jonschlinkert](http://twitter.com/jonschlinkert)

## License

Copyright (c) 2015 Nils Knappmeier
Released under the MIT license.

***

_This file was generated by [verb-cli](https://github.com/assemble/verb-cli) on May 14, 2015._

<!-- reflinks generated by verb-reflinks plugin -->

[assemble]: http://assemble.io
[template]: https://github.com/jonschlinkert/template
[verb]: https://github.com/assemble/verb