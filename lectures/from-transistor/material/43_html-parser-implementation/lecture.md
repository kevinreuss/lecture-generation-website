# HTML Parser Implementation

HTML parsing is the process of analyzing HTML code and generating a structured representation, typically a tree, which can be used by the rest of a web rendering engine. 

## Two Main Parsing Models

1. **DOM-based HTML Parsing** - It creates a tree structure known as the Document Object Model (DOM) for the HTML document. The DOM can then be manipulated or queried for information. DOM parsers are generally used in browsers. 

```javascript
let parser = new DOMParser();
let doc = parser.parseFromString('<h1>Hello World</h1>', 'text/html');
console.log(doc.body); // Output: <body><h1>Hello World</h1></body>
```

2. **SAX-based HTML Parsing** - SAX (Simple API for XML) is an event-driven online algorithm for parsing XML documents. SAX parsers work better for situations where you only need to handle the HTML data as it comes in, and you do not need to build up an in-memory representation of the document.

```java
public class MyHandler extends DefaultHandler {
    public void startElement(String uri, String localName, String qName, Attributes attributes) throws SAXException {
        System.out.println("Start Element :" + qName);
    }
    public void endElement(String uri, String localName, String qName) throws SAXException {
        System.out.println("End Element :" + qName);
    }
}
```

## Tokenization

HTML parsing starts with tokenization. A tokenizer breaks the input into the following tokens: StartTag, EndTag, Comment, Character, Doctype, etc. This is typically implemented using a finite state machine.

```python
from html.parser import HTMLParser
class MyHTMLParser(HTMLParser):
    def handle_starttag(self, tag, attrs):
        print("Encountered a start tag:", tag)
```

## Tree Construction

The tree construction stage takes tokens from the tokenizer and processes them to build up the DOM. The process is guided by the HTML specification and involves creating and inserting nodes into the tree in response to tokens.

```python
class MyHTMLParser(HTMLParser):
    def handle_starttag(self, tag, attrs):
        print("Start tag:", tag)
        for attr in attrs:
            print("     attr:", attr)
    def handle_endtag(self, tag):
        print("End tag  :", tag)
```

## Error Handling

Real-world HTML parsers must also be prepared to handle ill-formed HTML, correcting errors on the fly. This error handling process is also specified in the HTML standard.

Remember, HTML parsing is a complex topic, and this is just a brief overview. The actual implementation of an HTML parser involves many more details and edge cases.
