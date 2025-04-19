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
