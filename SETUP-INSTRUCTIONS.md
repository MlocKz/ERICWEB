# Eric Renaud Landing Page - Setup Instructions

This guide will help you get the website live with an admin panel where Eric can manage properties and contact info.

---

## Step 1: Create a GitHub Account & Repository

1. Go to [github.com](https://github.com) and create a free account (if you don't have one)
2. Click the **+** icon in the top right → **New repository**
3. Name it something like `eric-renaud-realtor`
4. Make it **Public** (required for free Netlify hosting)
5. Click **Create repository**

### Upload the Files
1. On the repository page, click **uploading an existing file**
2. Drag and drop ALL files from the `landging page` folder:
   - `index.html`
   - `admin/` folder
   - `data/` folder
   - `images/` folder (when you add property images)
   - Any `.jpg` files (831-dawson-sold.jpg, 669-park-sold.jpg, etc.)
3. Click **Commit changes**

---

## Step 2: Deploy to Netlify

1. Go to [netlify.com](https://netlify.com) and sign up with your GitHub account
2. Click **Add new site** → **Import an existing project**
3. Choose **GitHub** and authorize Netlify
4. Select the repository you just created
5. Leave all settings as default and click **Deploy site**
6. Wait 1-2 minutes for deployment
7. Netlify will give you a URL like `https://random-name-12345.netlify.app`

### Set Up a Custom Domain (Optional)
1. In Netlify, go to **Domain settings**
2. Click **Add custom domain**
3. Follow the instructions to point your domain (e.g., `ericrenaud.ca`) to Netlify

---

## Step 3: Enable Netlify Identity (For Admin Login)

1. In your Netlify site dashboard, go to **Integrations** → **Identity**
2. Click **Enable Identity**
3. Under **Registration**, select **Invite only** (so only Eric can log in)
4. Click **Save**

### Enable Git Gateway
1. Still in Identity settings, scroll to **Services**
2. Click **Enable Git Gateway**
3. This allows the admin panel to save changes to GitHub

### Invite Eric as Admin
1. Go to **Identity** → **Invite users**
2. Enter Eric's email: `erenaudrealtor@gmail.com`
3. He'll receive an email to set up his password

---

## Step 4: Access the Admin Panel

1. Go to `https://your-site-name.netlify.app/admin`
2. Log in with the email/password from the invite
3. Eric can now:
   - **Add new properties** with photos and descriptions
   - **Edit existing properties**
   - **Update contact info** (email, phone, social links)
   - **Change the bio text**

---

## How to Add a New Property

1. Log into `/admin`
2. Click **Properties** in the sidebar
3. Click **New Property**
4. Fill in:
   - Address (e.g., "123 Main Street")
   - City (e.g., "Windsor, Ontario")
   - Upload a property image
   - Select Investment Type (Rental, Fixer Upper, etc.)
   - Select Strategy (Buy & Hold, Fix & Flip, etc.)
   - Write a description
   - Set Display Order (1 = first, 2 = second, etc.)
5. Click **Publish**
6. The site will automatically update in ~1 minute

---

## Updating the Properties List

When Eric adds a new property through the admin panel, it creates a new JSON file in `data/properties/`. 

**Important:** You also need to update the JavaScript to include the new file. In `index.html`, find this section:

```javascript
const propertyFiles = [
    'data/properties/831-dawson-road.json',
    'data/properties/669-park-street-west.json'
];
```

Add new property files to this array as they're created.

**Alternative (Simpler):** I can set up automatic property discovery if you'd prefer - just let me know.

---

## File Structure

```
landging page/
├── index.html              # Main website
├── admin/
│   ├── index.html          # Admin panel entry
│   └── config.yml          # CMS configuration
├── data/
│   ├── settings.json       # Contact info, social links
│   └── properties/
│       ├── 831-dawson-road.json
│       └── 669-park-street-west.json
├── images/                 # Upload property images here
└── *.jpg                   # Property photos
```

---

## Troubleshooting

### Admin panel shows blank page
- Make sure Git Gateway is enabled in Netlify Identity settings

### Login not working
- Check that Netlify Identity is enabled
- Make sure Eric accepted the invite email

### Changes not appearing
- Wait 1-2 minutes for Netlify to rebuild
- Hard refresh the page (Ctrl+Shift+R or Cmd+Shift+R)

### Properties not loading
- Check browser console for errors (F12 → Console)
- Make sure JSON files are valid (no trailing commas)

---

## Need Help?

The admin panel uses [Decap CMS](https://decapcms.org/) (formerly Netlify CMS) - their docs have more detailed info.

For Netlify hosting: [docs.netlify.com](https://docs.netlify.com)
