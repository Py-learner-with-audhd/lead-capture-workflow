# Lead Capture Workflow — Setup Guide
### Form to Google Sheet + Email | Built with n8n

---

## What this workflow does

When someone fills in your contact form, this workflow:

1. **Receives the lead** — catches the form submission instantly via webhook
2. **Enriches the data** — formats and prepares the lead details
3. **Logs to Google Sheets** — adds the lead to your spreadsheet automatically
4. **Sends a confirmation email** — the customer gets a professional reply straight away
5. **Notifies you** — you get an instant email with their details so you can follow up

No leads get missed. No manual data entry. Every enquiry gets a response in seconds — even when you're busy.

---

## What you need before you start

- An n8n account (cloud or self-hosted)
- A Gmail account connected in n8n
- A Google Sheets account connected in n8n
- A contact form on your website (or you can use n8n's built-in form trigger)

---

## Step 1 — Import the workflow

1. Log into your n8n instance
2. Click **Add Workflow** (top right)
3. Click the three dots menu → **Import from file**
4. Select the `.json` file you downloaded
5. The workflow will open in your editor

---

## Step 2 — Connect Gmail

1. Click the **Send Confirmation** node
2. Click **Credential** → **Create new**
3. Sign in with your Gmail account and allow access
4. Click **Save**
5. Repeat for the **Notify Business Owner** node — you can use the same Gmail credential

---

## Step 3 — Connect Google Sheets

1. Click the **Add to Google Sheet** node
2. Click **Credential** → **Create new**
3. Sign in with your Google account and allow access
4. In the **Spreadsheet** field, select or paste the link to your Google Sheet
5. In the **Sheet** field, select the sheet tab you want leads logged to
6. Make sure your sheet has column headers that match your form fields (e.g. Name, Email, Message, Date)

---

## Step 4 — Set up your webhook

1. Click the **Receive Lead** node
2. Copy the **Webhook URL** shown
3. Go to your website contact form settings
4. Paste the webhook URL as the form submission endpoint

> **Using a different form tool?** Most form builders (Typeform, Tally, WPForms, Gravity Forms) let you send data to a webhook URL. Check their integration or webhook settings.

> **No website form yet?** You can use n8n's built-in **Form Trigger** node instead of the webhook — it gives you a hosted form you can share directly.

---

## Step 5 — Customise your emails

### Confirmation email (to the customer)
1. Click the **Send Confirmation** node
2. Update the **To** field to pull from your form data (e.g. `{{ $json.email }}`)
3. Edit the **Subject** and **Body** to match your brand

Example subject: `Thanks for getting in touch — I'll be back to you shortly`

Example body:
```
Hi {{ $json.name }},

Thanks for reaching out. I've received your message and will get back to you within 1 business day.

Speak soon,
[Your name]
```

### Notification email (to you)
1. Click the **Notify Business Owner** node
2. Update the **To** field with your own email address
3. Edit the body to include the fields you want to see at a glance

Example body:
```
New lead received:

Name: {{ $json.name }}
Email: {{ $json.email }}
Message: {{ $json.message }}
Submitted: {{ $now }}
```

---

## Step 6 — Test it

1. Click **Execute Workflow** in n8n
2. Submit a test entry through your form (or use n8n's test trigger)
3. Check that:
   - The lead appears in your Google Sheet
   - The confirmation email lands in your test inbox
   - The notification email lands in your own inbox
4. If anything doesn't fire, check the node for a red error icon and click it to see the message

---

## Step 7 — Activate

1. Once testing looks good, toggle the workflow to **Active** (top right switch)
2. The workflow will now run automatically every time someone submits your form

---

## Common questions

**Can I use this with any contact form?**
Yes — any form that supports webhook submissions will work. This includes Tally, Typeform, WPForms, Gravity Forms, Elementor Forms, and most others.

**What if I don't have a website yet?**
Use n8n's built-in Form Trigger node. It creates a hosted form you can share via link — no website needed.

**Can I log to multiple sheets or add more columns?**
Yes. In the Google Sheets node, you can map any field from your form to any column in your sheet.

**Can I send the notification to a Slack channel or WhatsApp instead?**
Yes — swap the Notify Business Owner node for a Slack node, Telegram node, or any other messaging node n8n supports.

**Something isn't working**
Click the node with the red icon to see the error message. Most issues are credential permissions or a mismatched field name.

---

## Want this built custom for your business?

This template covers the most common setup — but every business is different.

If you want a workflow built specifically around your tools, your forms, and your process — with integrations like CRM logging, Slack alerts, automated follow-up sequences, or custom qualification logic — reply to this email and let's talk.

I offer a one-off setup fee starting from £300 depending on complexity, plus an optional monthly retainer from £50/month for ongoing maintenance, tweaks, and support.
