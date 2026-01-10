# ⚡ ORION DEV CORE - Complete PWA Ecosystem

**AI Amplifies. I Create.**

A complete Progressive Web App ecosystem showcasing 4 AI-powered automation products for South African businesses.

---

## 📦 What's Included

### 🎯 4 Product Demos

1. **Orion Legal Suite** (R7,555) - AI-powered legal practice management with immediate payment
2. **Orion Hotel Suite** (Custom pricing) - 24/7 AI concierge with quote request system
3. **Orion mPOS** (R3,848) - Mobile point of sale with immediate payment
4. **Orion Surge** (FREE) - Token-based crash game with registration system

### 🛠️ Technical Stack

- **Frontend:** HTML5, CSS3, Vanilla JavaScript
- **PWA:** Service Workers, Web App Manifest
- **Backend:** Google Apps Script
- **Database:** Google Sheets
- **AI:** Google Gemini 2.0 Flash
- **Payments:** Yoco (South African gateway)
- **Notifications:** Discord webhooks
- **Hosting:** GitHub Pages

---

## 🚀 SETUP INSTRUCTIONS

### Step 1: GitHub Repository Setup

1. **Create/Update Your GitHub Repository**
   ```bash
   cd website
   git add .
   git commit -m "Deploy Orion Dev Core PWA ecosystem"
   git push origin main
   ```

2. **Enable GitHub Pages**
   - Go to repository Settings → Pages
   - Source: `main` branch, `/ (root)` folder
   - Save and wait for deployment
   - Your site will be at: `https://oriondevcore.github.io/website/`

3. **Add Your App Icons**
   - Create/upload these images to `icons/` folder:
     - `orion-core.png` (512x512px)
     - `legal.png` (192x192px)
     - `hotel.png` (192x192px)
     - `mpos.png` (192x192px)
     - `surge.png` (192x192px)

---

### Step 2: Google Sheets Setup

1. **Create New Google Sheet**
   - Go to [Google Sheets](https://sheets.google.com)
   - Create new spreadsheet: "Orion Dev Core - Leads Database"
   - Copy the Sheet ID from URL: `https://docs.google.com/spreadsheets/d/YOUR_SHEET_ID_HERE/edit`

2. **Sheet Configuration**
   - The script will auto-create these tabs on first submission:
     - `Demo_Legal` - Legal Suite purchases
     - `Demo_Hotel` - Hotel quote requests
     - `Demo_mPOS` - mPOS purchases
     - `Demo_Surge` - Surge registrations

---

### Step 3: Google Apps Script Setup

1. **Create Apps Script Project**
   - Open your Google Sheet
   - Extensions → Apps Script
   - Delete default code
   - Copy-paste **Code.gs Part 1** (main handlers)
   - Copy-paste **Code.gs Part 2** (helper functions) below Part 1

2. **Update Configuration**
   Find this line in Code.gs:
   ```javascript
   const SHEET_ID = 'YOUR_GOOGLE_SHEET_ID_HERE';
   ```
   Replace with your actual Sheet ID.

3. **Set Script Properties**
   - Project Settings (⚙️ icon) → Script Properties
   - Add these properties:

   | Property | Value | Where to Get It |
   |----------|-------|-----------------|
   | `GEMINI_API_KEY` | `AIza...` | [Get Gemini API Key](https://aistudio.google.com/app/apikey) |
   | `YOCO_SECRET_KEY` | `sk_live_...` | [Yoco Dashboard](https://portal.yoco.com) → Developers |
   | `DISCORD_WEBHOOK_URL` | `https://discord.com/api/webhooks/...` | Discord Server → Integrations → Webhooks |
   | `WEATHER_API_KEY` | (Optional) | [OpenWeatherMap](https://openweathermap.org/api) |

4. **Deploy as Web App**
   - Click **Deploy** → **New deployment**
   - Type: **Web app**
   - Description: "Orion Dev Core Backend v1"
   - Execute as: **Me** (graham@oriondevcore.com)
   - Who has access: **Anyone**
   - Click **Deploy**
   - **Copy the Web App URL** - you'll need this!

5. **Test the Setup**
   - Run the `testSetup()` function from Apps Script editor
   - Check execution log for ✓ confirmations
   - Check your Discord for test notification

---

### Step 4: Connect Frontend to Backend

Update the `SCRIPT_URL` in **ALL HTML files**:

1. **index.html** (line ~351)
2. **demos/legal.html** (line ~288)
3. **demos/hotel.html** (line ~353)
4. **demos/mpos.html** (line ~316)
5. **demos/surge.html** (line ~371)

Replace:
```javascript
const SCRIPT_URL = 'YOUR_GOOGLE_APPS_SCRIPT_URL_HERE';
```

With your actual Web App URL:
```javascript
const SCRIPT_URL = 'https://script.google.com/macros/s/YOUR_DEPLOYMENT_ID/exec';
```

**Save and push to GitHub!**

---

### Step 5: Discord Webhook Setup

1. **Create Discord Server** (if you don't have one)
   - Create new server or use existing
   - Create channel: `#orion-notifications`

2. **Create Webhook**
   - Channel Settings → Integrations → Webhooks
   - Create Webhook
   - Name: "Orion Dev Core Bot"
   - Copy Webhook URL
   - Add to Script Properties (you did this in Step 3)

3. **Test Notification**
   - Run `testSetup()` function in Apps Script
   - Check Discord for "SYSTEM TEST" message

---

### Step 6: Yoco Payment Setup

1. **Create/Login to Yoco Account**
   - Go to [portal.yoco.com](https://portal.yoco.com)
   - Complete business verification

2. **Get API Keys**
   - Developers → API Keys
   - Copy your **Secret Key** (starts with `sk_live_`)
   - Add to Script Properties (Step 3)

3. **Test Payment Flow**
   - Submit a demo form (use test email)
   - Verify redirect to Yoco payment page
   - Check Discord for notification
   - Check Google Sheet for entry

---

## 🧪 TESTING CHECKLIST

### ✅ Homepage (index.html)
- [ ] Page loads correctly
- [ ] All 4 app cards display with icons
- [ ] AI chat widget appears (bottom right)
- [ ] Chat opens when clicked
- [ ] Send test message → AI responds
- [ ] Demo buttons link to correct pages

### ✅ Legal Suite Demo (demos/legal.html)
- [ ] Form loads with all fields
- [ ] Submit form → redirects to Yoco
- [ ] Entry appears in Google Sheet `Demo_Legal` tab
- [ ] Discord notification received
- [ ] Pricing displayed correctly (R7,555)

### ✅ Hotel Suite Demo (demos/hotel.html)
- [ ] Star rating tiers display correctly
- [ ] Form submission → success message
- [ ] Entry in `Demo_Hotel` tab
- [ ] Discord notification with quote details
- [ ] Email sent to client

### ✅ mPOS Demo (demos/mpos.html)
- [ ] Form loads and validates
- [ ] Submit → Yoco redirect
- [ ] `Demo_mPOS` sheet updated
- [ ] Discord notification
- [ ] Pricing shown (R3,848)

### ✅ Surge Demo (demos/surge.html)
- [ ] Registration form works
- [ ] Username validation (alphanumeric + underscore)
- [ ] Duplicate username prevented
- [ ] `Demo_Surge` sheet updated
- [ ] Welcome email sent
- [ ] Discord notification

### ✅ PWA Features
- [ ] Manifest.json loads (check DevTools → Application)
- [ ] Service Worker registers
- [ ] "Add to Home Screen" prompt appears
- [ ] Works offline (cached pages load)
- [ ] Icons display correctly when installed

---

## 📊 MONITORING YOUR BUSINESS

### Google Sheets Dashboard
All submissions automatically save to your Google Sheet:
- **Demo_Legal** - Track legal suite purchases
- **Demo_Hotel** - Monitor hotel quote requests
- **Demo_mPOS** - See mPOS orders
- **Demo_Surge** - Player registrations

### Discord Notifications
Real-time alerts for:
- 💳 New purchases (Legal & mPOS)
- 📧 Quote requests (Hotel)
- 🎮 New player registrations (Surge)
- ⚠️ System errors or issues

### Yoco Dashboard
Track payments and transactions:
- portal.yoco.com → Transactions
- Filter by product name
- Export for accounting

---

## 🔧 CUSTOMIZATION

### Change Branding/Colors
Edit CSS variables in each HTML file:
```css
:root {
    --primary: #0a192f;      /* Dark blue background */
    --secondary: #112240;    /* Lighter blue */
    --accent: #64ffda;       /* Teal/cyan accent */
    --text: #8892b0;         /* Light gray text */
    --text-bright: #ccd6f6;  /* Bright white text */
}
```

### Update Pricing
Find and replace prices in:
- Brochure text (HTML content)
- JavaScript amount values (in cents)
- Google Sheet formulas

### Modify AI Chat Behavior
Edit `systemPrompt` in **Code.gs** `handleChat()` function.

---

## 🐛 TROUBLESHOOTING

### AI Chat Not Working
1. Check Gemini API key in Script Properties
2. Verify quota limits: [Google AI Studio](https://aistudio.google.com/app/apikey)
3. Check Apps Script execution logs

### Payment Links Not Generating
1. Verify Yoco Secret Key (must start with `sk_live_`)
2. Check Yoco account status
3. Review Apps Script logs for errors

### Discord Notifications Missing
1. Verify webhook URL is correct
2. Check webhook hasn't been deleted
3. Test with `testSetup()` function

### Forms Not Submitting
1. Check browser console for errors (F12)
2. Verify Apps Script Web App URL is correct
3. Ensure Apps Script is deployed with "Anyone" access

### Service Worker Issues
1. Clear cache: DevTools → Application → Clear storage
2. Unregister and re-register service worker
3. Hard refresh: Ctrl+Shift+R (Windows) or Cmd+Shift+R (Mac)

---

## 📱 MOBILE TESTING

### iOS (iPhone/iPad)
1. Open site in Safari
2. Tap Share button
3. "Add to Home Screen"
4. Test installed app

### Android
1. Open site in Chrome
2. Tap menu (3 dots)
3. "Add to Home Screen"
4. Test installed app

---

## 🚀 GO LIVE CHECKLIST

### Before Launch
- [ ] All API keys configured and tested
- [ ] Yoco account verified and live
- [ ] Test each demo flow end-to-end
- [ ] Verify Discord notifications working
- [ ] Check email delivery
- [ ] Test on mobile devices
- [ ] Update contact information everywhere
- [ ] Backup Google Sheet

### Marketing
- [ ] Share website URL: `https://oriondevcore.github.io/website/`
- [ ] Create QR codes for each demo
- [ ] Social media posts ready
- [ ] Email signature updated
- [ ] Business cards printed

---

## 📈 ANALYTICS (Optional Enhancement)

Add Google Analytics to track:
- Page views
- Demo form submissions
- Conversion rates
- User flow

Add before `</head>` in all HTML files:
```html
<!-- Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
</script>
```

---

## 🔐 SECURITY NOTES

✅ **What's Secure:**
- All API keys stored server-side (Apps Script Properties)
- HTTPS enforced by GitHub Pages
- Yoco handles all payment processing (PCI compliant)
- POPIA compliant data handling

⚠️ **Important:**
- Never commit API keys to GitHub
- Keep Yoco secret keys private
- Regularly rotate API keys
- Monitor Discord for suspicious activity

---

## 📞 SUPPORT

**Graham Schubach**  
📱 WhatsApp/Call: +27 72 497 1810  
📧 Email: graham@oriondevcore.com  
🌐 Website: www.oriondevcore.com  
💻 GitHub: github.com/Oriondevcore

---

## 📄 LICENSE

© 2026 Orion Dev Core. All rights reserved.

Built with ❤️ in KwaZulu-Natal, South Africa  
**AI Amplifies. I Create.** ⚡

---

## 🎉 YOU'RE READY TO LAUNCH!

Your complete PWA ecosystem is ready. Every piece is connected:
- ✅ Frontend hosted on GitHub Pages
- ✅ Backend powered by Google Apps Script
- ✅ Payments via Yoco
- ✅ Real-time notifications via Discord
- ✅ AI chat with Gemini
- ✅ Data storage in Google Sheets

**Go change South African business automation! 🚀⚡** 
