# Lab 7 - E2E Testing with Jest & Puppeteer

## Check Your Understanding

**1) Where would you fit your automated tests in your Recipe project development pipeline? Select one of the following and explain why.**

- Within a Github action that runs whenever code is pushed
- Manually run them locally before pushing code
- Run them all after all development is completed

**Answer:** Within a GitHub action that runs whenever code is pushed.

Running tests automatically via a GitHub Action whenever code is pushed is the best fit. It guarantees the tests are run consistently (we don't have to rely on developers remembering to run them), it catches regressions immediately on every push/PR before bad code can be merged into `main`, and it tests the code in a clean, reproducible CI environment instead of just on a single developer's machine. Manually running tests locally is unreliable because people forget, and waiting until "after all development is completed" defeats the purpose of testing — bugs caught late are far more expensive to fix than ones caught at the moment they were introduced.

**2) Would you use an end to end test to check if a function is returning the correct output? (yes/no)**

**Answer:** No.

End-to-end tests are meant to emulate full user interactions with the application from the browser/UI down through the entire stack. Checking that a single function returns the correct output is the job of a **unit test**, which is much faster, more focused, and easier to debug. Using an E2E test for that would be slow, brittle, and overkill.

**3) What is the difference between navigation and snapshot mode?**

**Answer:** Navigation mode audits a page right after it finishes loading, so it measures the full load experience and is what gives you performance metrics like First Contentful Paint, Largest Contentful Paint, and overall load performance. Snapshot mode, on the other hand, just analyzes the page in its current state at the moment you run it — it does not reload the page or measure load behavior, so it can't give performance numbers or analyze JS execution. Snapshot is most useful for catching accessibility and best-practice issues in whatever state the DOM is currently in, while navigation is used when you care about how the page actually loads.

**4) Name three things we could do to improve the CSE 110 shop site based on the Lighthouse results.**

**Answer:**

1. **Properly size and modernize the product images.** The product images are loaded at their full original resolution but displayed in 200px-wide cards, which wastes bandwidth. Serving correctly sized images and using modern formats like WebP or AVIF would significantly improve performance.
2. **Improve accessibility metadata.** Adding a `lang` attribute to the `<html>` element, a `<meta name="description">` tag, and making sure buttons/links have accessible names would fix several accessibility and SEO audits that Lighthouse flags.
3. **Reduce render-blocking resources and improve caching.** The site loads all of its JS as `type="module"` at the top of the page and has no caching headers on its assets. Deferring non-critical scripts, minifying CSS/JS, and setting longer cache lifetimes on static assets would improve load time on repeat visits.
