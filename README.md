# Lab 7 - E2E Testing with Jest & Puppeteer

Sanjana Kalarickal

## Check Your Understanding

**1) Where would you fit your automated tests in your Recipe project development pipeline? Select one of the following and explain why.**

**Answer:** Within a GitHub Action that runs whenever code is pushed.

I would put the automated tests inside a GitHub Action that runs every time code is pushed or a pull request is opened. That way, the tests run automatically instead of depending on someone to remember to do it manually. It also helps catch bugs early before broken code gets merged into `main`.

Another reason this is useful is because the tests run in a clean CI environment, so everyone’s code is checked under the same conditions instead of only working on one developer’s machine. If tests are only run at the end of development, bugs can pile up and become much harder to track down later.

---

**2) Would you use an end to end test to check if a function is returning the correct output? (yes/no)**

**Answer:** No.

An end-to-end test would not be the right choice for checking whether a single function returns the correct value. That type of check is better handled with a unit test because unit tests are faster, simpler, and much easier to debug.

E2E tests are meant to test the entire application flow from the user’s perspective, so using them for one small function would be unnecessary and inefficient.

---

**3) What is the difference between navigation and snapshot mode?**

**Answer:** Navigation mode tests a page while it is loading, while snapshot mode analyzes the page in its current state.

Navigation mode reloads the page and measures how the site performs during the loading process. This is where metrics like First Contentful Paint (FCP) and Largest Contentful Paint (LCP) come from. It helps evaluate overall page performance and loading behavior.

Snapshot mode is different because it does not reload the page. Instead, it captures and analyzes the page exactly as it currently appears in the browser. Because of that, it is more useful for checking things like accessibility issues or best practices in the current DOM state rather than load performance.

---

**4) Name three things we could do to improve the CSE 110 shop site based on the Lighthouse results.**

1. **Optimize the product images.**
   The images being loaded are much larger than the size they are displayed at on the page. Resizing them properly and using newer formats like WebP or AVIF would reduce loading time and improve performance.

2. **Improve accessibility information.**
   Adding a `lang` attribute to the `<html>` tag, including a proper meta description, and making sure buttons and links have accessible labels would improve both accessibility and SEO scores.

3. **Reduce render-blocking resources and improve caching.**
   Some scripts and assets slow down the initial page load. Deferring non-essential JavaScript, minifying CSS/JS files, and enabling better caching for static assets would help the site load faster, especially for returning users.
