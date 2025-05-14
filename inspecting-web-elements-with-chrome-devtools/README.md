<h1>
  <span class="headline">Introduction to Selenium</span>
  <span class="subhead">Inspecting Web Elements with Chrome DevTools</span>
</h1>

**Learning Objective:** Use Chrome DevTools to inspect elements and relate them to Selenium interactions.

## Introduction to Chrome DevTools

Modern web applications are constructed from numerous components, including HTML elements, styles, and scripts. To automate browser tasks with Selenium, you need the ability to reliably identify and interact with specific parts on a page – such as buttons or input fields. That’s where Chrome DevTools becomes essential.

## Opening and navigating DevTools

Chrome DevTools is included in every up-to-date version of Chrome; you don’t need to install anything extra. Here’s how to open and start exploring:

- **Open Chrome and load a web page**.
- **Right-click** anywhere on the page—try this on a button or a form field.
- Select **“Inspect”** from the menu.

You can also use keyboard shortcuts for even quicker access:

- **Windows/Linux:** <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>I</kbd>
- **macOS:** <kbd>Command</kbd> + <kbd>Option</kbd> + <kbd>I</kbd>

## Using the Elements tab to inspect page structure

With the **Elements** tab, you can view the _Document Object Model_ (DOM) for the page—a tree structure representing every visible and invisible element.

To inspect any part of a page:

- Click the **cursor icon** (“Select an element in the page to inspect it”) in the top-left of DevTools. It resembles a mouse pointer inside a rectangle.
- Hover over webpage items to highlight them visually.
- Click on any element to scroll directly to its HTML representation in the Elements panel.

You’ll see HTML tags, attributes such as `id`, `class`, or `name`, and other metadata unique to each element.

**For example:**

```html
<button id="login-btn" class="primary-button">Log In</button>
```

As you examine different elements, notice the nested organization. This reflects parent-child relationships on the page—just like rooms and hallways within a building.

## Identifying element locators: ID, class, XPath, and more

To automate actions with Selenium, you must direct Selenium to the specific element you want to interact with. These directions are called _locators_—unique ways to identify a web element.

> 📚 A _locator_ is a description of how Selenium can identify the precise element to automate within a web page.

DevTools is your primary tool for uncovering these locator details:

| **Locator Type** | **Description**                                                                                                                                  |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| **ID**           | The `id` attribute is often unique per page, making it an ideal locator.                                                                         |
| **Class name**   | The `class` attribute labels a group of similar elements. Not always unique, but useful when they are.                                           |
| **Name**         | The `name` attribute is frequently found on form fields.                                                                                         |
| **XPath**        | Represents the path to an element within the HTML structure. Right-click an element in DevTools and choose “Copy → Copy XPath” for this locator. |
| **CSS selector** | Offers flexible targeting using tag, class, and attribute combinations.                                                                          |

## Examples:

### **ID**

```html
<input id="email-input" />
```

```python
driver.find_element("id", "email-input")
```

### **Class name**

```html
<button class="signup-btn">Sign Up</button>
```

```python
driver.find_element("class name", "signup-btn")
```

### **Name**

```html
<input name="password" />
```

```python
driver.find_element("name", "password")
```

### **CSS selector**

```python
driver.find_element("css selector", "button.primary-button")
```

### **XPath**

> ⚠ Be careful using copy-pasted XPaths, as page structure changes can break them.

```python
driver.find_element("xpath", "//button[text()='Log In']")
```

> 🏆 IDs are often the most reliable locator. If an element lacks a unique ID or name, try class, then XPath or CSS selectors as needed.

## Relating DevTools findings to Selenium commands

Once you have found an element using DevTools and recorded its key attributes, you are ready to create a Selenium command to select and interact with it.

Suppose DevTools reveals the following HTML for a search box:

```html
<input id="search-bar" class="search-input" name="q" type="text" />
```

These attributes let you use different locator strategies in your Python code:

- **By ID:**
  ```python
  search_box = driver.find_element("id", "search-bar")
  search_box.send_keys("Selenium tutorials")
  ```
- **By name:**
  ```python
  search_box = driver.find_element("name", "q")
  ```
- **By class name:**
  ```python
  search_box = driver.find_element("class name", "search-input")
  ```

Remember, your choice should reflect the attribute most likely to be unique and stable for the element you want to automate.

> 💡 Workflow summary:
>
> 1. Use DevTools to inspect and identify element attributes.
> 2. Choose the locator strategy (prefer ID, then name, class, or fallback to XPath or CSS).
> 3. Write your Selenium code using `driver.find_element()` with the chosen locator.

<div class="activity partner-exercise">
  <h2 class="title">Turn real web elements into Selenium actions</h2>
  <span class="minutes">15 min</span>
</div>

Time to connect your inspection skills in DevTools to real Selenium scripting. You will identify a key element on a live website and automate an interaction through Python code.

1. **Choose a familiar, globally accessible website.**  
   Pick a site that you visit often—such as <https://www.python.org>, <https://news.ycombinator.com>, or any site you know is safe and available worldwide.

2. **Inspect a prominent element.**

   - Right-click a notable element (for example, a search field or a main navigation button).
   - Select **“Inspect”** to view its HTML in the Elements panel.

3. **Record unique attributes.**

   - Note key attributes: `id`, `name`, or `class`.
   - If no unique attribute is available, use “Copy → Copy XPath” or “Copy selector” for a fallback locator.

4. **Write a Selenium code snippet.**

   - In a new Python script, use your chosen locator in a `driver.find_element()` command.
   - Example, if you found `id="search-bar"`:

     ```python
     from selenium import webdriver
     from selenium.webdriver.chrome.service import Service

     service = Service(executable_path="/path/to/chromedriver")
     driver = webdriver.Chrome(service=service)

     try:
         driver.get("https://www.example.com")
         search_input = driver.find_element("id", "search-bar")
         search_input.send_keys("Selenium automation")
     finally:
         driver.quit()
     ```

   - Adjust the code to match your chosen site and exact locator.

5. **Test your script.**

   - Run the script and observe whether the browser automates the action as expected.

> 📚 This exercise helps build the critical muscle of turning real-world page structures into automation actions—a daily task in professional browser automation.

<div class="activity discussion">
  <h2 class="title">Reflect</h2>
  <span class="minutes">3 min</span>
</div>

As you worked through the exercise, what did you learn about how websites are built? Did you notice that some elements were easier to target than others? Share any challenges you faced—such as elements without helpful IDs, or situations where several items shared the same class name. Discuss how you approached these challenges, and compare which locator strategies you found most effective.
