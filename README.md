# nimnjs-node
JS implementation of nimn specification. Highly Compressed JS object/JSON.

[![Code Climate](https://codeclimate.com/github/nimndata/nimnjs-node//badges/gpa.svg)](https://codeclimate.com/github/nimndata/nimnjs-node/) 
[![Known Vulnerabilities](https://snyk.io/test/github/nimndata/nimnjs-node//badge.svg)](https://snyk.io/test/github/nimndata/nimnjs-node/) 
[![Travis ci Build Status](https://travis-ci.org/nimndata/nimnjs-node/.svg?branch=master)](https://travis-ci.org/nimndata/nimnjs-node/) 
[![Coverage Status](https://coveralls.io/repos/github/nimndata/nimnjs-node//badge.svg?branch=master)](https://coveralls.io/github/nimndata/nimnjs-node/?branch=master)
[<img src="https://img.shields.io/badge/Try-me-blue.svg?colorA=FFA500&colorB=0000FF" alt="Try me"/>](https://nimndata.github.io/nimnjs-node/)

<img align="right" src="static/img/nimnjs-logo.png" /> 

## Introduction
NIMN JS can parse JS object to nimn data and vice versa. See Nimn [specification](https://github.com/nimndata/spec) for more detail.

## Usages
First install or add to your npm package
```
$npm install nimnjs
```

```js
var nimn = require("nimnjs");

var schema = {
    "type": "object",
    "properties": {
        "name": {
            "type": "string"
        },
        "age": {
            "type": "number"
        },
        "male": {
            "type": "boolean"
        },
        "projects": {
            "type": "array",
            "properties": {
                "item": {
                    "type": "object",
                    "properties": {
                        "name": {
                            "type": "string"
                        },
                        "decription": {
                            "type": "string"
                        }
                    }
                }
            }
        }
    }
}

var nimnObj = new nimn(schema);

var data = {
    "name" : "amit",
    "age" : 32,
    "male" : true,
    "projects" : [
        {
            "name": "some",
            "decription" : "some long description"
        }
    ]
}

var result = nimnObj.encode(data);//Æamitº32ÙÇÆsomeºsome long description
result = nimnObj.getDecoder().decode(result);
expect(result).toEqual(data); 
```

For date compression
```js
var nimnDateparser = require("nimn-date-parser");
//generate schema and data
var nimnInstance = new nimn(schema);
nimnInstance.configDataType("date",function(val){
    return nimnDateparser.parse(val,true,true,true)
},function(val){
     return nimnDateparser.parseBack(val,true,true,true)
});

var nimndata = nimnInstance.encode(data);
```

Include [dist](dist/nimn.js) in your HTML to use it in browser.


Check the [demo](https://nimndata.github.io/nimnjs-node/) for instant use. It generates schema automatically with the help of [schema builder](https://github.com/nimndata/nimnjs-schema-builder) when sample json is provided.


## Support
I need your expert advice, and contribution to grow nimn (निम्न) so that it can support all mazor languages. Please join the [official organization](https://github.com/nimndata) on github to support it. And ask your friends, and colleagues to give it a try. It can not only save bandwidth but speed up communication, search and much more.


### Worth to mention

 - [Stubmatic](https://github.com/NaturalIntelligence/Stubmatic) : A stub server to mock behaviour of HTTP(s) / REST / SOAP services.
 - **[fastify-xml-body-parser](https://github.com/NaturalIntelligence/fastify-xml-body-parser/)** : Fastify plugin / module to parse XML payload / body into JS object using fast-xml-parser.
  - [fast-lorem-ipsum](https://github.com/amitguptagwl/fast-lorem-ipsum) : Generate lorem ipsum words, sentences, paragraph very quickly.
- [Grapes](https://github.com/amitguptagwl/grapes) : Flexible Regular expression engine which can be applied on char stream. (under development)
- [fast XML Parser](https://github.com/amitguptagwl/fast-xml-parser) : Fastest pure js XML parser for xml to js/json and vice versa. And XML validation.