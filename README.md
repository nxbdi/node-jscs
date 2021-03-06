node-jscs [![Build Status](https://travis-ci.org/mdevils/node-jscs.png?branch=master)](https://travis-ci.org/mdevils/node-jscs)
=========

JSCS — JavaScript Code Style.

`jscs` is a code style checker. `jscs` can check cases, which are not implemeted in jshint,
but it does not duplicate `jshint` functionality, so you should use `jscs` and `jshint` together.

Friendly packages
-----------------

 * Grunt task: https://github.com/gustavohenke/grunt-jscs-checker
 * Gulp task: https://github.com/sindresorhus/gulp-jscs

Installation
------------

`jscs` can be installed using `npm`:

```
npm install jscs
```

To run `jscs`, you can use the following command from the project root:

```
./node_modules/.bin/jscs path[ path[...]]
```

Configuration
-------------

`jscs` is configured using `.jscs.json` file, located in the project root.

Example configuration:

```javascript
{
    /*
        Option: requireCurlyBraces
        Requires curly braces after statements.

        Valid example:

        if (x) {
            x++;
        }

        Invalid example:

        if (x) x++;
    */
    "requireCurlyBraces": ["if", "else", "for", "while", "do", "try", "catch", "case", "default"],

    /*
        Option: requireSpaceAfterKeywords
        Requires space after keyword.

        Valid example:

        return true;

        Invalid example:

        if(x) {
            x++;
        }
    */
    "requireSpaceAfterKeywords": ["if", "else", "for", "while", "do", "switch", "return", "try", "catch"],

    /*
        Option: disallowSpaceAfterKeywords
        Disallows space after keyword.

        Valid example:

        if(x > y) {
            y++;
        }
    */
    "disallowSpaceAfterKeywords": ["if", "else", "for", "while", "do", "switch", "try", "catch"],

    /*
        Option: requireParenthesesAroundIIFE
        requires parentheses around immediately invoked function expressions.

        Valid example:

        var a = (function(){ return 1; })();
        var b = (function(){ return 2; }());
        var c = (function(){ return 3; }).call(this, arg1);
        var d = (function(){ return 3; }.call(this, arg1));
        var e = (function(){ return d; }).apply(this, args);
        var f = (function(){ return d; }.apply(this, args));

        Invalid example:

        var a = function(){ return 1; }();
        var c = function(){ return 3; }.call(this, arg1);
        var d = function(){ return d; }.apply(this, args);
    */
    "requireParenthesesAroundIIFE": true,


    /*
        Option: requireSpacesInFunctionExpression
        Requires space before () or {} in function declarations.

        Valid examples:
        function () {}
        function a () {}

        Invalid examples:
        function() {}
        function (){}

    */
    "requireSpacesInFunctionExpression": { "beforeOpeningRoundBrace": true, "beforeOpeningCurlyBrace": true },

    /*
        Option: disallowSpacesInFunctionExpression
        Disallows space before () or {} in function declarations.

        Valid examples:
        function(){}
        function a(){}

        Invalid examples:
        function () {}
        function a (){}

    */
    "disallowSpacesInFunctionExpression": { "beforeOpeningRoundBrace": true, "beforeOpeningCurlyBrace": true },

    /*
        Option: disallowMultipleVarDecl
        Disallows multiple var declaration (except for-loop).

        Valid example:

        var x = 1;
        var y = 2;

        for (var i = 0, j = arr.length; i < j; i++) {}

        Invalid example:

        var x = 1,
            y = 2;
    */
    "disallowMultipleVarDecl": true,

    /*
        Option: disallowEmptyBlocks
        Disallows empty blocks (except for catch blocks).

        Valid example:

        if ( a == b ) { c = d; }
        try { a = b; } catch( e ){}

        Invalid example:

        if ( a == b ) { } else { c = d; }
    */
    "disallowEmptyBlocks": true,

    /*
        Option: requireMultipleVarDecl
        Requires multiple var declaration.

        Valid example:

        var x = 1,
            y = 2;

        Invalid example:

        var x = 1;
        var y = 2;
    */
    "requireMultipleVarDecl": true,

    /*
        Option: disallowSpacesInsideObjectBrackets
        Disallows space after opening object curly brace and before closing.

        Valid example:

        var x = {a: 1};

        Invalid example:

        var x = { a: 1 };
    */
    "disallowSpacesInsideObjectBrackets": true,

    /*
        Option: disallowSpacesInsideArrayBrackets
        Disallows space after opening array square bracket and before closing.

        Valid example:

        var x = [1];

        Invalid example:

        var x = [ 1 ];
    */
    "disallowSpacesInsideArrayBrackets": true,

    /*
        Option: disallowSpacesInsideParentheses
        Disallows space after opening round bracket and before closing.

        Valid example:

        var x = (1 + 2) * 3;

        Invalid example:

        var x = ( 1 + 2 ) * 3;
    */
    "disallowSpacesInsideParentheses": true,

    /*
        Option: requireSpacesInsideObjectBrackets
        Possible values: "all" for strict mode, "allButNested" ignores closing brackets in a row.
        Requires space after opening object curly brace and before closing.

        Valid example for mode "all":

        var x = { a: { b: 1 } };

        Valid example for mode "allButNested":

        var x = { a: { b: 1 }};

        Invalid example:

        var x = {a: 1};
    */
    "requireSpacesInsideObjectBrackets": "all",

    /*
        Option: requireSpacesInsideArrayBrackets
        Possible values: "all" for strict mode, "allButNested" ignores closing brackets in a row.
        Requires space after opening array square bracket and before closing.

        Valid example for mode "all":

        var x = [ 1 ];

        Valid example for mode "allButNested":

        var x = [[ 1 ], [ 2 ]];

        Invalid example:

        var x = [1];
    */
    "requireSpacesInsideArrayBrackets": "all",

    /*
        Option: disallowQuotedKeysInObjects
        Possible values:
            `true`: for strict mode,
            "allButReserved" allows ES3+ reserved words to remain quoted. This is helpfull when using this option with JSHint's `es3` option.
        Disallows quoted keys in object if possible.

        Valid example for mode true:

        var x = { a: { default: 1 } };

        Valid example for mode "allButReserved":

        var x = {a: 1, 'default': 2};

        Invalid example:

        var x = {'a': 1};
    */
    "disallowQuotedKeysInObjects": true,

    /*
        Option: disallowDanglingUnderscores
        Disallows identifiers that start or end in _, except for some popular exceptions:
        _ (underscore.js), __filename (node.js global), and __dirname (node.js global).

        Valid example:

        var x = 1;
        var y = _.extend;
        var z = __dirname;
        var w = __filename;
        var x_y = 1;

        Invalid examples:

        var _x = 1;
        var x_ = 1;
        var x_y_ = 1;
    */
    "disallowDanglingUnderscores": true,

    /*
        Option: disallowSpaceAfterObjectKeys
        Disallows space after object keys.

        Valid example:

        var x = {a: 1};

        Invalid example:

        var x = {a : 1};
    */
    "disallowSpaceAfterObjectKeys": true,

    /*
        Option: requireSpaceAfterObjectKeys
        Requires space after object keys.

        Valid example:

        var x = {a : 1};

        Invalid example:

        var x = {a: 1};
    */
    "requireSpaceAfterObjectKeys": true,

    /*
        Option: disallowCommaBeforeLineBreak
        disallows commas as last token on a line in lists.

        Valid example:

        var x = {
            one: 1
            , two: 2
        };
        var y = { three: 3, four: 4};

        Invalid example:

        var x = {
            one: 1,
            two: 2
        };
    */
    "disallowCommaBeforeLineBreak": true,

    /*
        Option: requireCommaBeforeLineBreak
        requires commas as last token on a line in lists.

        Valid example:

        var x = {
            one: 1,
            two: 2
        };
        var y = { three: 3, four: 4};

        Invalid example:

        var x = {
            one: 1
            , two: 2
        };
    */
    "requireCommaBeforeLineBreak": true,

    /*
        Option: requireAlignedObjectValues
        Possible values:
            "all" for strict mode,
            "skipWithFunction" ignores objects if one of the property values is a function expression,
            "skipWithLineBreak" ignores objects if there are line breaks between properties
        Requires proper alignment in object literals.

        Valid example:

        var x = {
            a   : 1,
            bcd : 2,
            ef  : 'str'
        };

        Invalid example:

        var x = {
            a : 1,
            bcd : 2,
            ef : 'str'
        };
    */
    "requireAlignedObjectValues": "all",

    /*
        Option: requireOperatorBeforeLineBreak
        requires operators to appear before line breaks and not after.

        Valid example:

        x = y ? 1 : 2;
        x = y ?
            1 : 2;

        Invalid example:

        x = y
            ? 1 : 2;
    */
    "requireOperatorBeforeLineBreak": ["?", "+", "-", "/", "*", "=", "==", "===", "!=", "!==", ">", ">=", "<", "<="],

    /*
        Option: disallowLeftStickedOperators
        Disallows sticking operators to the left.

        Valid example:

        x = y ? 1 : 2;

        Invalid example:

        x = y? 1 : 2;
    */
    "disallowLeftStickedOperators": ["?", "+", "-", "/", "*", "=", "==", "===", "!=", "!==", ">", ">=", "<", "<="],

    /*
        Option: requireRightStickedOperators
        Requires sticking operators to the right.

        Valid example:

        x = !y;

        Invalid example:

        x = ! y;
    */
    "requireRightStickedOperators": ["!"],

    /*
        Option: disallowRightStickedOperators
        Disallows sticking operators to the right.

        Valid example:

        x = y + 1;

        Invalid example:

        x = y +1;
    */
    "disallowRightStickedOperators": ["?", "+", "/", "*", ":", "=", "==", "===", "!=", "!==", ">", ">=", "<", "<="],

    /*
        Option: requireLeftStickedOperators
        Requires sticking operators to the left.

        Valid example:

        x = [1, 2];

        Invalid example:

        x = [1 , 2];
    */
    "requireLeftStickedOperators": [","],

    /*
        Option: disallowSpaceAfterPrefixUnaryOperators
        Requires sticking unary operators to the right.

        Valid example:

        x = !y; y = ++z;

        Invalid example:

        x = ! y; y = ++ z;
    */
    "disallowSpaceAfterPrefixUnaryOperators": ["++", "--", "+", "-", "~", "!"],

    /*
        Option: requireSpaceAfterPrefixUnaryOperators
        Disallows sticking unary operators to the right.

        Valid example:

        x = ! y; y = ++ z;

        Invalid example:

        x = !y; y = ++z;
    */
    "requireSpaceAfterPrefixUnaryOperators": ["++", "--", "+", "-", "~", "!"],

    /*
        Option: disallowSpaceBeforePostfixUnaryOperators
        Requires sticking unary operators to the left.

        Valid example:

        x = y++; y = z--;

        Invalid example:

        x = y ++; y = z --;
    */
    "disallowSpaceBeforePostfixUnaryOperators": ["++", "--"],

    /*
        Option: requireSpaceBeforePostfixUnaryOperators
        Disallows sticking unary operators to the left.

        Valid example:

        x = y ++; y = z --;

        Invalid example:

        x = y++; y = z--;
    */
    "requireSpaceBeforePostfixUnaryOperators": ["++", "--"],

    /*
        Option: disallowSpaceBeforeBinaryOperators
        Requires sticking binary operators to the left.

        Valid example:

        x+ y;

        Invalid example:

        x + y;
    */
    "disallowSpaceBeforeBinaryOperators": ["+", "-", "/", "*", "=", "==", "===", "!=", "!=="],

    /*
        Option: requireSpaceBeforeBinaryOperators
        Disallows sticking binary operators to the left.

        Valid example:

        x !== y;

        Invalid example:

        x!== y;
    */
    "requireSpaceBeforeBinaryOperators": ["+", "-", "/", "*", "=", "==", "===", "!=", "!=="],

    /*
        Option: disallowSpaceAfterBinaryOperators
        Requires sticking binary operators to the right.

        Valid example:

        x +y;

        Invalid example:

        x+ y;
    */
    "disallowSpaceAfterBinaryOperators": ["+", "-", "/", "*", "=", "==", "===", "!=", "!=="],

    /*
        Option: requireSpaceAfterBinaryOperators
        Disallows sticking binary operators to the right.

        Valid example:

        x + y;

        Invalid example:

        x +y;
    */
    "requireSpaceAfterBinaryOperators": ["+", "-", "/", "*", "=", "==", "===", "!=", "!=="],

    /*
        Option: disallowImplicitTypeConversion
        Disallows implicit type conversion.

        Valid example:

        x = Boolean(y);
        x = Number(y);
        x = String(y);
        x = s.indexOf('.') !== -1;

        Invalid example:

        x = !!y;
        x = +y;
        x = '' + y;
        x = ~s.indexOf('.');
    */
    "disallowImplicitTypeConversion": ["numeric", "boolean", "binary", "string"],

    /*
        Option: requireCamelCaseOrUpperCaseIdentifiers
        Requires identifiers to be camelCased or UPPERCASE_WITH_UNDERSCORES

        Valid example:

        var camelCase = 0;
        var CamelCase = 1;
        var _camelCase = 2;
        var camelCase_ = 3;
        var UPPER_CASE = 4;

        Invalid examples:

        var lower_case = 1;
        var Mixed_case = 2;
        var mixed_Case = 3;
    */
    "requireCamelCaseOrUpperCaseIdentifiers": true,

    /*
        Option: disallowKeywords
        Disallows usage of specified keywords.

        Invalid example:

        with (x) {
            prop++;
        }
    */
    "disallowKeywords": ["with"],

    /*
        Option: disallowMultipleLineBreaks
        Disallows multiple blank lines in a row.

        Invalid example:

        var x = 1;


        x++;
    */
    "disallowMultipleLineBreaks": true,

    /*
        Option: validateLineBreaks
        Possible values: "CR", "LF", "CRLF"
        Option to check line break characters

        Invalid example:

        var x = 1;<CRLF>
        x++;
    */
    "validateLineBreaks": "LF",

    /*
        Option: validateQuoteMarks
        Possible values: "\"", "'", true
        Requires all quote marks to be either the supplied value, or consistent if "true"

        Valid example for mode "\"" or mode "true":

        var x = "x";

        Valid example for mode "'" or mode "true":

        var x = 'x';

        Invalid example for mode "true":

        var x = "x", y = 'y';
    */
    "validateQuoteMarks": "\"",

    /*
        Option: validateIndentation
        Possible values: a positive number, '\t'
        Validates indentation for arrays, objects, switch statements, and block statements

        Valid example for mode "2":

        if (a) {
          b=c;
          function(d) {
            e=f;
          }
        }

        Invalid example for mode "2":

        if (a) {
           b=c;
        function(d) {
               e=f;
        }
        }

        Valid example for mode "\t":

        if (a) {
            b=c;
            function(d) {
                e=f;
            }
        }

        Invalid example for mode "\t":

        if (a) {
             b=c;
        function(d) {
                   e=f;
         }
        }
    */
    "validateIndentation": "\t",

    /*
        Option: disallowMixedSpacesAndTabs
        Possible values: true, "smart"
        requires lines to not contain both spaces and tabs consecutively,
        or spaces after tabs only for alignment if "smart"

        Valid example for mode "true":

        \tvar foo = "blah blah";
        \s\s\s\svar foo = "blah blah";
        \t/**
        \t\s*
        \t\s*/ //a single space to align the star in a docblock is allowed

        Invalid example for mode "true":

        \t\svar foo = "blah blah";
        \s\tsvar foo = "blah blah";

        Valid example for mode "smart":

        \tvar foo = "blah blah";
        \t\svar foo = "blah blah";
        \s\s\s\svar foo = "blah blah";
        \t/**
        \t\s*
        \t\s*/ //a single space to align the star in a docblock is allowed

        Invalid example for mode "smart":

        \s\tsvar foo = "blah blah";
    */
    "disallowMixedSpacesAndTabs": true,

    /*
        Option: disallowTrailingWhitespace
        requires all lines to end on a non-whitespace character

        Valid example:
        var foo = "blah blah";

        Invalid example:

        var foo = "blah blah"; //<-- whitespace character here
    */
    "disallowTrailingWhitespace": true,

    /*
        Option: disallowKeywordsOnNewLine
        Disallows placing keywords on a new line.

        Valid example:

        if (x < 0) {
            x++;
        } else {
            x--;
        }

        Invalid example:

        if (x < 0) {
            x++;
        }
        else {
            x--;
        }
    */
    "disallowKeywordsOnNewLine": ["else"],

    /*
        Option: requireKeywordsOnNewLine
        Requires placing keywords on a new line.

        Valid example:

        if (x < 0) {
            x++;
        }
        else {
            x--;
        }

        Invalid example:

        if (x < 0) {
            x++;
        } else {
            x--;
        }
    */
    "requireKeywordsOnNewLine": ["else"],

    /*
        Option: requireLineFeedAtFileEnd
        Requires placing line feed at file end.
    */
    "requireLineFeedAtFileEnd": true,

    /*
        Option: maximumLineLength
        Requires all lines to be at most the number of characters specified
    */
    "maximumLineLength": 120,

    /*
        Option: requireCapitalizedConstructors
        Requires constructors to be capitalized (except for "this")

        Valid example:

        var a = new B();
        var c = new this();

        Invalid example:

        var d = new e();
    */
    "requireCapitalizedConstructors": true,

    /*
        Option: safeContextKeyword
        Option to check "var that = this" expressions

        Valid example:

        var that = this;

        Invalid example:

        var _this = this;
    */
    "safeContextKeyword": "that",

    /*
        Option: requireDotNotation
        requires member expressions to use dot notation when possible

        Valid example:

        var a = b[c];
        var a = b.c;
        var a = b[c.d];
        var a = b['while']; //reserved word

        Invalid example:

        var a = b['c'];
    */
    "requireDotNotation": true,

    /*
        Option: validateJSDoc
        Enables jsdoc validation.

        Option: validateJSDoc.checkParamNames
        Ensures param names in jsdoc and in function declaration are equal.

        Option: validateJSDoc.requireParamTypes
        Ensures params in jsdoc contains type.

        Option: validateJSDoc.checkRedundantParams
        Reports redundant params in jsdoc.
    */
    "validateJSDoc": {
        "checkParamNames": true,
        "checkRedundantParams": true,
        "requireParamTypes": true
    },

    /*
        Option: excludeFiles
        Disables style checking for specified paths.
    */
    "excludeFiles": ["node_modules/**"],

    /*
        Option: additionalRules
        Pluggable rules
    */
    "additionalRules": ["project-rules/*.js"],

    /*
        Option: preset
        Extends defined rules with preset rules
    */
    "preset": "jquery"
}
```

Browser Usage
-------------

File `jscs-browser.js` contains browser-compatible version of `jscs`.

Download and include `jscs-browser.js` into your page.

Example:

```html
<script type="text/javascript" src="jscs-browser.js"></script>
<script type="text/javascript">
var checker = new JscsStringChecker();
checker.registerDefaultRules();
checker.configure({disallowMultipleVarDecl: true});
var errors = checker.checkString('var x, y = 1;');
errors.getErrorList().forEach(function(error) {
    console.log(errors.explainError(error));
});
</script>
```
