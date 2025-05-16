<h1>
  <span class="headline">Selenium: Intro to Browser Automation</span>
  <span class="subhead">Instructor Guide</span>
</h1>

## Setup

### Delivery tips

- Walk through the step-by-step workflow in the virtual environment and installation sections, highlighting the “separate workspace” analogy for virtual environments.
- Use the remote control and TV analogy to describe the role of web drivers, making the invisible communication process clear.
- Demonstrate the installation verification script live. Narrate what each step accomplishes: Python → Selenium → ChromeDriver → Chrome browser.
- During troubleshooting, ask learners to voice the error message and explain how they diagnosed and resolved it. Foster resilience and resourcefulness.
- Use the activity as a formative check—learners should be confident in the solo setup before they proceed further.

---

## Selenium's Role in Testing

### Delivery tips

- Encourage participants to share their own relatable experiences with tedious web tasks; frame those as automation opportunities.
- Walk through the sample Selenium script step-by-step, emphasizing how each Python command maps to a real browser action.
- Highlight the "scenario" and activity as a way to bridge learners' daily experiences to testing automation.
- Foster discussions on the challenges of automated testing, such as handling dynamic content and browser differences.

### Knowledge check answers

1. B. It allows you to automate interactions with a web browser using code.
2. B. It can automate repetitive browser tasks and supports multiple browsers.

---

## Writing Your First Selenium Script

### Delivery tips

- Before starting, review prior microlessons on environment setup so learners recognize their progress and see the connection between setup and first automation.
- Walk through the narrative and remote control analogy, linking each code concept to real-world activities learners do in a browser.
- When demoing, run the script live and narrate each step—highlight how feedback is given (assertion failures, print messages).
- Encourage learners to pick URLs that hold personal or professional interest, making the automation experience more meaningful.
- In the activity, remind learners to always change something after the first run and explain the value of experimentation.
- For the discussion, prompt learners to go beyond initial “page loaded” checks and consider real-world reliability issues (e.g., changing titles, logins, popups).

### Knowledge check answers

1. What is the main purpose of `assert "Python" in driver.title` in your Selenium script?

   - **Correct answer:** B. To check that the correct page loaded by looking for "Python" in the page title.

2. Why should you always use `driver.quit()` at the end of your Selenium script?
   - **Correct answer:** C. To close all browser windows opened by the script and free up system resources.

---

## Inspecting Web Elements with Chrome DevTools

### Delivery tips

- Begin by connecting to prior lessons, emphasizing how learners now move from simple navigation to precise element targeting.
- Use the “blueprint” and “x-ray scanner” analogies when introducing DevTools, grounding the technical work in relatable imagery.
- Demonstrate inspection of different types of elements on a live web page. Show how IDs, class names, names, and XPaths look in both DevTools and Selenium code.
- Encourage learners to inspect a variety of global, safe websites to ensure inclusivity and avoid region-locked or culturally narrow examples.
- For the activity, coach learners to document their locator choices and code. In group sharing, prompt discussions about where identification was challenging and why certain strategies worked better than others.
- Highlight that using unique IDs is preferred, but show fallback strategies using classes or XPath when needed.

### Activity solution suggestion

A strong student submission will include:

- The chosen web page and specific element targeted (e.g., the search bar on <https://www.python.org>).
- The raw HTML snippet or exact attributes found in DevTools (such as `id="search-bar"`).
- A working Selenium code snippet using the identified locator:
  ```python
  search_input = driver.find_element("id", "search-bar")
  search_input.send_keys("Testing search")
  ```
- A brief rationale for choosing that locator (e.g., “I used ID because it is unique to the search bar, making it the most stable choice.”)
- If fallback strategies were used (like XPath), the explanation should mention why, such as the lack of unique attributes, and any challenges faced or lessons learned.

---

🏗️ **Under Construction**

We are constantly working to improve our resources for instructors and students.

**Have something to contribute to this Instructor Guide?** [Let us know](https://pages.git.generalassemb.ly/modular-curriculum-all-courses/universal-resources-internal/module-feedback.html).
