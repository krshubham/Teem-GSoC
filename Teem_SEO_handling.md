## Handling SEO in Teem

Teem is entirely based on AngularJs `1.x` and thus much like other javascript based web applications it suffers from the problem of SEO indexing. The crawlers do not execute javascript and thus when the crawler hits the web page it gets a blank HTML page with no content specific to that page! This a major drawback, and thus a major challenge also!

### What we do:

- We basically have a `nginx.conf` file which allows us to look for the HTTP User Agent that is fetching ou site.

- Based on this filtering we redirect the user agent to another port where it gets a copy of `index.html` with the available `og:tags`!



### Fetching the [OpenGraph](http://ogp.me) meta data

- The base file from which the processing starts is [this](https://github.com/krshubham/teem-link-preview/blob/master/src/routes/teemSEOHandler.js)

- When the request comes to the server, it makes a query to the SwellRT server as can be seen [here](https://github.com/krshubham/teem-link-preview/blob/master/src/routes/utils/ogscraper.js).

-  This is the same meta data that Teem fetches from the SwellRT server when a successful websocket connection is established with the server. The establishment of this websocket connection is what makes SEO of teem complex and difficult for standard solutions like prerender!

-  Even if we use prerender the time taken is longer and hence a crawler would simply reach its timeout and bounce off the page.

-  After getting the meta data we construct the `index.html` page by linking all the meta data in the head section of the page and thus we return this HTML page back to the crawler.

**Submissions:**

- Contributed to the new repository created specially for this purpose. Added to Teem using a simple docker container added in the [docker-compose] (https://github.com/Grasia/teem/pull/380/commits/997258f2b85d98bdc1207792d0f0296eb0189308) file.

- Repository URL: [krshubham/teem-link-preview](https://github.com/krshubham/teem-link-preview/) 