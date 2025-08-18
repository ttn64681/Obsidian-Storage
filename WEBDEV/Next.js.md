- ***server-side rendering (SSR)***
	- essentially runs code on server first to generate the HTML
	- Then, same code runs in browser when page loads

**SSR vs CSR vs SSG vs ISR:**
- client-side rendering (CSR)
	- sends minimal HTML file to browser
	- **Pros:** fast initial server response, good for highly interactive apps
	- **Cons**: Poor SEO
- server-side rendering (SSR)
	- server executes JS code and generates complete HTML for page
	- server sends fully rendered HTML to browser
	- browser displays HTML immediately, and then the JS code is downloaded and executed (hydration)
	- **Pros**: Improved SEO, faster initial page load
	- **Cons**: Higher server load, slower time to first byte
- ***static-side generation (SSG)***
	- HTML is generated at build-time
	- generated HTML is served directly to the browser
	- Pros: Excellent SEO, very fast performance
	- Cons: Not suitable suitable for pages w/ frequently changing data
- incremental static regeneration (ISR)
	- similar to SSG, but pages can be regenerated in the background after deployed
	- This allows you to serve static pages while updating content


<hr>

Next.js is designed to make SSR and SSG easy.

Next.js also offers file-based routing via API routes.
These routes run on the server and can be used to fetch data from databases or other API
This removes the need for a separate backend
