# Awesome SSR [![Awesome](https://awesome.re/badge-flat.svg)](https://awesome.re)

A comprehensive list of techniques and tools to render JavaScript apps to HTML,
and a curated list of learning material.

Includes resources for Server-Side Rendering (SSR) as well as for Pre-Rendering and Static Site Generators.

Read the [Introduction](#introduction) for an explanation of what this is about, SSR, Pre-Rendering, and Static Site Generators.

#### Contents

- [Introduction](#introduction)
- [Learning Material](#learning-material)
- [Tools](#tools)


## Introduction

Instead of using HTML to display content,
modern frontends (React, Vue, Angular, ...) use JavaScript to load content and display it by manipulating the DOM.
Such content is available to a crawler only if it executes JavaScript.
Most crawlers don't execute JavaScript and rely exclusively on HTML.
Such "JavaScript-generated-content" is invisible to them.

Server-Side Rendering (SSR), Pre-Rendering, and Static Site Generators are techniques to render JavaScript-generated-content to HTML.
Making the content visible to crawlers.
These techniques also have performance benefits.
The performance benefits can be considerable on mobile.

###### SEO

The Google crawler is
the only crawler that executes JavaScript.
All other crawlers rely on HTML exclusively.
If you want your content to be crawled by all other search engines (Bing, Baidu, DuckDuckGo, ...), then your content needs to be included in your website's HTML.

Google's capability to execute JavaScript has limitations.
(See the Google I/O '18 talk "Deliver search-friendly JavaScript-powered websites" linked in the "Learning Material" section.)
It is safer to include your content to your website's HTML
rather than to rely on Google's crawler to execute your website's JavaScript.

###### SMO

The crawler of social media sites (Facebook, Twitter, ...) don't execute JavaScript and rely solely on HTML.

If you want your website to be correctly previewed when a user shares your website, then the corresponding `<meta>` tags need to be included in your website's HTML.

(SMO stands for Social Media Optimization.)

###### Performance

Rendering your website's pages to HTML decreases the perceived loading time:
Once the HTML is loaded, content can already be displayed before JavaScript is loaded/executed.

The improvement can be considerable on mobile
where loading/executing JavaScript is much slower.

###### Techniques

There are two ways to render JavaScript-generated-content to HTML:

- **Directly render to HTML**
  <br/>
  Most modern view libraries (React, Vue, Angular, ...) can directly render to HTML (instead of rendering to the DOM).
  (E.g. a React component can be rendered to HTML with `require('react-dom/server').renderToString`.)
- **Render to HTML via headless browser**
  <br/>
  A headless browser runs your website's JavaScript,
  the website's pages are rendered to the DOM of the headless browser,
  and HTML is automatically generated from the resulting DOM.

Leading to the following techniques:

- **Server-Side Rendering (SSR)**
  <br/>
  Directly render your website's pages to HTML at request-time:
  Every time a user requests a page, the server renders the page directly to HTML (which will then include your page's content).
  <br/>
  SSR is the most reliable option if your HTML changes frequently.
  (More precisely: If your website's content may change after deploy-time,
  e.g. if you website's content is generated by users.)
- **Pre-Rendering**
  <br/>
  A headless browser crawls your website, executes the website's JavaScript, and generates HTML upon the resulting DOM.
  Instead of using a headless browser,
  some pre-renderers directly render your pages to HTML.
- **Static Site Generators**
  <br/>
  A static website is a website that doesn't have any server code:
  The website is composed of static browser assets only (HTML, CSS, JavaScript, images, ...).
  Some generators generate HTML files: When your website is built, each page is rendered to a HTML file (which will then include the page's content).
  <br/>
  If your content may only change at deploy-time, then using a Static Site Generator is an option.


## Learning Material

 - [Deliver search-friendly JavaScript-powered websites (Google I/O '18)](https://www.youtube.com/watch?v=PFwUbgvpdaQ) - Talk that mentions how the Google crawler executes JavaScript.
 - [The Complete Guide for SSR with Vue](https://ssr.vuejs.org/) - Official guide.
 - [The Benefits of Server Side Rendering Over Client Side Rendering](https://medium.com/walmartlabs/the-benefits-of-server-side-rendering-over-client-side-rendering-5d07ff2cefe8)

## Tools

#### Contents

- [SSR](#ssr)
  - [React](#react)
    - [Frameworks](#frameworks)
    - [Libraries](#libraries)
  - [Vue](#vue)
    - [Frameworks](#frameworks-1)
    - [Libraries](#libraries-1)
  - [Angular](#vue)
- [Pre-Rendering](#pre-rendering)
  - [Dynamic Pre-Rendering](#dynamic-pre-rendering)
    - [SaaS](#saas)
    - [Libraries](#libraries)
  - [Static Pre-Rendering](#static-pre-rendering)
- [Static Site Generators](#static-site-generators)

### SSR

#### React

##### Frameworks

 - [Next.js](https://github.com/zeit/next.js)
 - [After.js](https://github.com/jaredpalmer/after.js) - Similar to Next.js but with improved routing based on React Router.
 - [React Server](https://github.com/redfin/react-server)
 - [Reframe](https://github.com/reframejs/reframe) - Does SSR by default.

##### Libraries

 - [Razzle](https://github.com/jaredpalmer/razzle) - Handles the building. You do the rest.
 - [React Universal Component](https://github.com/faceyspacey/react-universal-component) - Utility to code split your SSR app.


#### Vue

##### Frameworks

 - [Nuxt](https://github.com/nuxt/nuxt.js) - Similar to Next.js but for Vue.
 - [Reframe](https://github.com/reframejs/reframe) - Reframe can be used with Vue.

##### Libraries

 - [vue-server-renderer](https://www.npmjs.com/package/vue-server-renderer) - Official library for SSR with Vue.

#### Angular

 - [Angular Universal](https://github.com/angular/universal) - Official packages for SSR with Angular.





### Static Site Generators

Frameworks to generate static sites.

 - [Gatsby.js](https://github.com/gatsbyjs/gatsby) - Static site generator based on React and GraphQL.
 - [React Static](https://github.com/nozzle/react-static) - Static site generator based on React and focused on simplicity.
 - [Phenomic](https://github.com/phenomic/phenomic) - Static site generator based on a flexible plugin system.
 - [Next.js](https://github.com/zeit/next.js) - Although primarily focused on SSR, Next.js can also generate static sites.
 - [Reframe](https://github.com/reframejs/reframe) - Reframe can generate static sites.





### Pre-Rendering

#### Dynamic Pre-Rendering

Automatically and regularly render your deployed website to HTML.

##### SaaS

 - [Prerender.io](https://prerender.io/)
 - [SEO4Ajax](https://www.seo4ajax.com/)
 - [Prerender.cloud](https://www.prerender.cloud/)
 - [SEO.js](http://getseojs.com/)
 - [BromBone](https://www.brombone.com/)

##### Libraries

 - [Prerender.io Node Server](https://github.com/prerender/prerender) - The prerender.io Node Server is open source.

#### Static Pre-Rendering

Render your pages to HTML at build-time.

 - [Prerender SPA Plugin](https://github.com/chrisvfritz/prerender-spa-plugin) - Uses Puppeteer to crawl & render your pages.
 - [react-snap](https://github.com/stereobooster/react-snap) - Uses Puppeteer to crawl & render your pages.
 - [prep](https://github.com/prismagraphql/prep) - Uses Chromeless to crawl & render your pages.
 - [Static site generator webpack plugin](https://github.com/markdalgleish/static-site-generator-webpack-plugin) - Directly render your pages to HTML. You provide render functions and routes. All routes are rendered at build-time using the render functions you provided. Also has a crawl mode to use a headless browser to automatically discover your website's URLs.
 - [React Snapshot](https://github.com/geelen/react-snapshot) - Pre-render React apps at build-time. Uses `require('react-dom/server').renderToString` to generate the HTML and uses JSDOM as headless browser to automatically discover your app's URLs.





