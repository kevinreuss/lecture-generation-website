# Server-Side Rendering (SSR) vs Client-Side Rendering (CSR)

Server-Side Rendering (SSR) and Client-Side Rendering (CSR) are two methods used to display content on a user's browser.

## Server-Side Rendering (SSR)

In SSR, the server's responsibility is to generate the full HTML for a page in response to a request. It means the server converts the React components into an HTML string, then sends it to the client.

Consider this Node.js and Express example:

```javascript
app.get("/", (req, res) => {
  const html = ReactDOMServer.renderToString(<App />);
  res.send(html);
});
```

In this case, the server renders the `App` component into an HTML string and sends it as a response.

## Client-Side Rendering (CSR)

In CSR, an HTML file with a JavaScript bundle is sent to the client. The rendering happens in the browser, where the JavaScript creates the DOM elements and manipulates the HTML as needed.

Here's a simplified example with React:

```javascript
ReactDOM.render(<App />, document.getElementById("root"));
```

Here, `App` is a React component that gets rendered in the browser.

## Comparison

1. **Performance**: SSR can display a functional page faster than CSR as it sends fully composed HTML to the browser. However, CSR might feel faster as it only updates parts that need to change.
2. **SEO**: Search engine bots can crawl and index server-rendered pages more efficiently, which is advantageous for SEO.
3. **Complexity**: CSR is generally simpler to implement than SSR. But SSR can lead to better performance and SEO, so the complexity can be worthwhile.
