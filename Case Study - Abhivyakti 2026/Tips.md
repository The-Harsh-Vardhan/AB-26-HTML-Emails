# Tips — HTML Email Workflow

Practical tips for working with HTML emails, from importing into Gmail to creating them with AI.

---

## 1. How to import HTML mail in college id?

First install the **Mail Brother** extension on your **personal email**. Then while drafting a mail:

1. Click on the **red downwards arrow** next to **"Send Mass"**
2. Click **"Insert HTML"**
3. **Paste your HTML** code

Then send that mail to the email from which you want to send to participants or students.

---

## 2. How to send HTML mail from college id?

> **⚠️ NOTE:** Don't just forward the mail from your personal id as it is — it will then be collapsed under **"..."** in the mail. You can't do anything to change it from the HTML part.

**Workaround (Jugaad):**

1. Open the forwarded mail draft
2. Adjust your mail properly in the forward draft
3. **Select All** and **Copy** the entire mail
4. Click the **plus (+) icon** to make a **new draft**
5. **Paste** the copied content into the new draft

This way the mail will **not** be under "..." and will display fully to recipients.

---

## 3. How to use AI to make HTML mails?

1. First get the **content ready** using **ChatGPT** (text copy, structure, sections)
2. Then switch to **VS Code** with **GitHub Copilot**
3. Use **Claude Sonnet** or **Opus** models for the best results when generating and iterating on the HTML

> **📝 Note:** You will be needing to make **multiple iterations** to get the desired results. Don't expect a perfect email in one shot — refine progressively.

---

## 4. How to use images in my HTML mail?

HTML emails require images to be **hosted online** — local file paths won't work in email clients.

**Steps:**

1. Go to [https://imgbb.com/](https://imgbb.com/)
2. Upload your image (it's free, no account needed)
3. After uploading, go to the **profile section** of your desired image
4. Click **"Copy the link"** for **"HTML Image"**
5. Give that link to Copilot along with your prompt, or use it directly in your `<img>` tag:

```html
<img src="https://i.ibb.co/XXXXX/your-image.png" width="200" alt="Description"
     style="display:block; width:200px; height:auto;">
```
