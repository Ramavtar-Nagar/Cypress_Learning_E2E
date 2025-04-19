# 🌿 Cypress Beginner Guide

A quick and beginner-friendly guide to get started with **Cypress** for testing web applications.

---



## 🌀 1. What is Cypress?

Cypress is a **JavaScript-based test automation tool** used to test web applications.

You can write tests that:

- 🌐 Visit web pages  
- ✍️ Click buttons, fill forms  
- ✅ Check if something is visible  
- 🔐 And make sure your app works as expected  

It’s mainly used for **End-to-End (E2E)** testing, but also supports **integration** and **component** testing.

---


## 🔥 2. Why Cypress?

- 💡 Easy to learn (if you know JavaScript)  
- ⚡ Fast & Real-time reloads  
- 🧪 Interactive GUI (you see what’s happening!)  
- 📦 Everything runs in the browser (no WebDriver needed)  
- 🧼 Clean syntax (`cy.get().click()`)

---


## 📦 3. How to Install Cypress

Run this in your project folder (Node.js required):

```bash
npm install cypress --save-dev
```

Then open Cypress GUI:

```bash
npx cypress open
```

---


## 📁 4. Cypress Folder Structure

Once Cypress is opened, it creates a cypress/ folder with:

- e2e/: where your test files go (*.cy.js)

- fixtures/: test data (JSON)

- support/: reusable commands

- cypress.config.js: configuration settings

---


## 🧪 5. Writing Your First Test

- Inside cypress/e2e/sample.cy.js, try this:

```js
describe('My First Test', () => {
  it('visits the site', () => {
    cy.visit('https://example.com')
    cy.contains('More information').click()
  })
})

```

---


## 6. 🎬 After Writing Your First Cypress Test — What Next?

Once you’ve written your test file (example: cypress/e2e/my_first_test.cy.js), you’ll need to go back to the Cypress GUI and run it.
Here’s how it works:

✅ Step-by-Step:

### 1. Open Cypress GUI
If it’s not open, run this in your terminal:

```bash
npx cypress open
```

This will launch the Cypress Test Runner GUI.

---

### 2. Select the Type of Test

Cypress will ask:

🧪 "What type of testing do you want to do?"

Choose:
➡️ E2E Testing (End-to-End)

You might need to configure it the first time — just follow the prompt and click through.

---

### 3. 🧭 Pick Your Browser

When you run Cypress, it shows you a list like:

- Chrome  
- Edge  
- Electron  
- Firefox  

👉 **Choose your preferred browser** (usually **Chrome** is the most stable).

---

### 4. ▶️ Run Your Test File

Cypress now shows a list of test files inside the `cypress/e2e/` folder.

➡️ **Click on your test file** — for example:  
`my_first_test.cy.js`

---

### 5. 🎥 Watch the Magic!

The browser opens and shows your test running in **real-time**, like a screen recording.

You'll see:

- 🧾 Each Cypress command on the **left** (`cy.visit()`, `cy.get()`, etc.)
- 🖥️ What’s happening on the **screen** on the right
- ✅ **Green** = Passed
- ❌ **Red** = Failed

---

### 💡 Bonus Tip

While it's running, you can **hover over each command** on the left — it will **highlight what was selected or clicked** in the browser view.

🔍 It’s super helpful for **debugging**.

---

## 🧪 Visual Summary

```bash
npx cypress open
↓
Choose: E2E Testing
↓
Pick: Chrome / Firefox / etc.
↓
Select your test file
↓
Watch test run in browser!
```

---



# 🔍 Selectors & Best Practices in Cypress (Easy + Deep + Fast)

A quick guide to mastering **element selection** in Cypress for reliable and maintainable tests.

---

## ✅ 1. What are Selectors in Cypress?

-Selectors are how you tell Cypress **which elements** to interact with on a webpage.

  Think of it like pointing at something and saying:
  "Hey Cypress, **click this button!**"  
  But you need to **point correctly** so Cypress finds the right element.

---

## 🧪 2. The Most Common Selectors in Cypress

```js
cy.get('button')           // Select by HTML tag
cy.get('.submit-btn')      // Select by class
cy.get('#username')        // Select by ID
cy.get('[name="email"]')   // Select by attribute
cy.get('[data-cy="login"]') // 🏆 Best practice: data-cy selector
```

--- 

## 🧠 3. Best Practices for Selectors

| DO ✅                          | DON'T ❌                              |
|--------------------------------|--------------------------------------|
| `data-cy="submit-btn"`         | `.btn-primary` (classes change)      |
| `[name="email"]`               | `#input-25` (auto-generated IDs)     |
| Short, readable selectors       | `div > form > div:nth-child(3) > button` |
| Reusable selectors             | Duplicated selectors everywhere      |

---

👉  Why data-cy is best?
Because it's only for testing - developers won't accidentally change it!

```html
<button data-cy="login-btn">Login</button>
```

```js
cy.get('[data-cy="login-btn"]').click()
```

---

## 🧰 4. Real-World Example

```html
<form>
  <input type="text" id="username" name="username" data-cy="username-input">
  <input type="password" id="password" name="password" data-cy="password-input">
  <button data-cy="submit-btn">Submit</button>
</form>
```

```js
cy.get('[data-cy="username-input"]').type('ramavtar')
cy.get('[data-cy="password-input"]').type('123456')
cy.get('[data-cy="submit-btn"]').click()
```

--- 

## 🔄 5. BONUS: Chaining and Traversing
Sometimes, you want to go deep inside elements. Example:

```js
cy.get('form').find('[data-cy="submit-btn"]').click()
```

or:

```js
cy.contains('Submit').click() // Select by visible text (very useful)
```

---

## 🧼 Summary Cheatsheet:

```js
cy.get('tag')              // By tag
cy.get('.class')           // By class
cy.get('#id')              // By ID
cy.get('[attr="value"]')   // By attribute
cy.get('[data-cy="xyz"]')  // ✅ Recommended for stable tests
cy.contains('text')        // By visible text
cy.get('parent').find('child') // Chaining
```

---


Let’s dive into Assertions in Cypress — what they are, how they work, and how to use them cleanly and quickly.

## 🎯 1. What Are Assertions?
Assertions are how you tell Cypress:
  -✅ "I expect this to be true!"
  -❌ If it’s not, the test fails.

They help you check if something happened as expected — like a button is visible, or text is correct.

---

## 🧪 2. Two Main Ways to Write Assertions

- ✅ Method 1: .should(...)

  ```js
  cy.get('button').should('be.visible')
  cy.get('.error-msg').should('contain', 'Invalid login')
  cy.get('input').should('have.value', 'Ramavtar')
  ```

- ✅ Method 2: .then() + expect(...) (for more control)
  
  ```js
    cy.get('.score').then(($el) => {
      expect($el.text()).to.equal('100')
    })
  ```

---

## 🧠 3. Common .should() Assertions

## 🎯 Common Cypress Assertions Cheat Sheet

| Assertion | Meaning | Example |
|-----------|---------|---------|
| `'be.visible'` | Element is visible | `cy.get('button').should('be.visible')` |
| `'exist'` | Element exists in DOM | `cy.get('#loader').should('exist')` |
| `'have.text', 'Welcome'` | Exact text match | `cy.get('h1').should('have.text', 'Welcome')` |
| `'contain', 'Ramavtar'` | Contains text | `cy.get('.user').should('contain', 'Ramavtar')` |
| `'have.class', 'active'` | Has CSS class | `cy.get('li').should('have.class', 'active')` |
| `'have.value', '123'` | Input value matches | `cy.get('input').should('have.value', '123')` |
| `'be.checked'` | Checkbox/radio is checked | `cy.get('[type="checkbox"]').should('be.checked')` |
| `'not.exist'` | Element doesn't exist | `cy.get('.toast').should('not.exist')` |

### 💡 Pro Tips:
- Chain multiple assertions:  
  ```js
  cy.get('button')
    .should('be.visible')
    .and('contain', 'Submit')
    .and('not.be.disabled')
  ```

---

## 4. ⚙️ Real Example: Login Form

```js
cy.get('[data-cy="username-input"]').type('ramavtar')
cy.get('[data-cy="password-input"]').type('123456')
cy.get('[data-cy="submit-btn"]').click()

// After submit, check welcome message
cy.get('[data-cy="welcome-msg"]').should('contain', 'Welcome, Ramavtar')
```

---

## 5. 🔥 Bonus: Negation (not.)

```js
cy.get('.error-msg').should('not.exist')
cy.get('button').should('not.be.disabled')
```

---

## 6. 🎁 Extra Power: .and() for chaining

```js
cy.get('button')
  .should('be.visible')
  .and('have.text', 'Submit')
  .and('not.be.disabled')
```

--- 

## 🧼 Summary Cheatsheet

```js
cy.get('.item').should('exist')
cy.get('input').should('have.value', 'Hello')
cy.get('.btn').should('have.class', 'active')
cy.get('.msg').should('contain', 'Success')
cy.get('.hidden').should('not.be.visible')

cy.get('.item').then($el => {
  expect($el.text()).to.include('Ramavtar')
})

```







