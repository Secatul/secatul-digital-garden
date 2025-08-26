---
title: Day 1 – Email classifier
---

Yesterday, I moved forward in a company’s selection process, and they gave me a really interesting challenge: build an email classifier.

The goal is to automate reading and classifying emails, and even suggest automatic responses using AI. The stack is:

- **Frontend:** HTML, CSS, JavaScript  
- **Backend:** Python  

The catch? I only know a little bit of Python... so I’ll definitely need help from AI for the backend (which, luckily, is allowed in this project).

---

## 🎨 Starting with What I Know  

I kicked things off in my comfort zone: the frontend.  

I built an upload form that lets users upload their email files (either `.txt` or `.pdf`). Alternatively, they can just paste plain text into a textarea.  

When the user hits **“Process Document”**, the AI should generate the classification and suggested response.  

Here’s the code for my initial form:  

```html
<div class="container">
  <form id="emailForm">
    <fieldset>
      <legend>Send email</legend>

      <label for="emailFiles">(.txt or pdf) files</label>
      <input
        id="emailFiles"
        type="file"
        accept=".txt,.pdf,text/plain,application/pdf"
        multiple
      >

      <div class="hint">Accepts .txt and .pdf (multiple files allowed).</div>
      <p class="hint">or</p>

      <label for="emailText">Paste the email text</label>
      <textarea 
        name="emailText" 
        id="emailText" 
        placeholder="Paste the email content here..." 
        rows="8">
      </textarea>

      <button type="submit">Proccess document</button>
    </fieldset>
  </form>
  <div id="results"></div>
</div>
```

I also touched the CSS a bit... which I haven’t done in years since I’ve mostly been relying on TailwindCSS. Here’s what the first version of the UI looks like:  

<img src="./imgs/email_classifier_ai_initial_ui.png" alt="Email Classifier UI v1"/>  

Not too bad for version one, right? My plan is to start small and keep improving as I go.  

---

## ⏳ The Challenge  

Here’s the tough part: I only have **3 days** to complete this project. That means I’ll need AI to help me out with the Python backend.  

Even so, I want to learn every single line of code. I might not finish the backend completely by myself, but I’ll do my best 🫡, and let AI handle the rest while I focus on understanding the process.  

---

## 🚀 Wrap-Up  

That’s it for Day 1. Tomorrow I’ll dive into the backend and start wiring up the AI logic.  

See you then.  

<img src="./imgs/study.gif" alt="Studying" width="300"/>  
