# Contact Form Setup Guide

## 🚀 Quick Setup with Formspree (Recommended)

### Step 1: Create Formspree Account
1. Go to [https://formspree.io/](https://formspree.io/)
2. Sign up with your email (free plan allows 50 submissions/month)
3. Verify your email address

### Step 2: Create a Form
1. Click "New Form" in your dashboard
2. Name it "SkipTheFirm Contact Form"
3. Copy the form endpoint (e.g., `https://formspree.io/f/xyzabc123`)

### Step 3: Update Your Website
1. In `index.html`, find the form tag
2. Replace `YOUR_FORM_ID` with your actual form ID
3. Example: `action="https://formspree.io/f/xyzabc123"`

### Step 4: Deploy and Test
1. Deploy your changes to Vercel
2. Test the form on your live site
3. Check your email for submissions

## 📧 Form Configuration Options

### Email Notifications
- Formspree will send submissions to your registered email
- You can add multiple recipients in Formspree dashboard
- Configure custom email templates

### Spam Protection
- Formspree includes built-in spam protection
- Enable reCAPTCHA in your Formspree settings
- Set up custom validation rules

### Redirects
Add to your form for custom thank you page:
```html
<input type="hidden" name="_next" value="https://yoursite.com/thank-you">
```

## 🔧 Alternative Solutions

### Option 2: Netlify Forms (if hosting on Netlify)
```html
<form netlify name="contact" method="POST">
  <input type="hidden" name="form-name" value="contact">
  <!-- your form fields -->
</form>
```

### Option 3: Vercel API Route
Create `/api/contact.js`:
```javascript
export default async function handler(req, res) {
  if (req.method === 'POST') {
    // Handle form submission
    // Send email using SendGrid, Nodemailer, etc.
    res.status(200).json({ message: 'Email sent successfully' });
  }
}
```

### Option 4: EmailJS (Client-side)
```html
<script src="https://cdn.jsdelivr.net/npm/@emailjs/browser@3/dist/email.min.js"></script>
<script>
  emailjs.init("YOUR_PUBLIC_KEY");
  // Send email directly from browser
</script>
```

## 🎯 Current Form Features

✅ **User Experience:**
- Loading states with spinner
- Success/error messages
- Form validation
- Responsive design
- Accessible labels

✅ **Data Collected:**
- Name (required)
- Email (required) 
- Company (optional)
- Message (required)

✅ **Security:**
- CSRF protection
- Input validation
- Spam prevention (with Formspree)

## 📞 Testing Your Form

1. Fill out all required fields
2. Submit the form
3. Check for loading spinner
4. Verify success message appears
5. Check your email for the submission
6. Test error handling by disconnecting internet

## 💡 Pro Tips

- **Custom Domain Email**: Use contact@skipthefirm.com for more professional appearance
- **Auto-Responder**: Set up automatic "Thanks for contacting us" emails
- **CRM Integration**: Connect Formspree to your CRM system
- **Analytics**: Track form submissions in Google Analytics
- **A/B Testing**: Test different form layouts for better conversion

## 🆘 Troubleshooting

**Form not submitting?**
- Check console for JavaScript errors
- Verify Formspree endpoint URL
- Ensure internet connection

**Not receiving emails?**
- Check spam folder
- Verify email address in Formspree
- Check Formspree dashboard for submissions

**Getting CORS errors?**
- Formspree handles CORS automatically
- For custom backends, add proper CORS headers
