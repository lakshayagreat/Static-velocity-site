# 🏎️ Velocity - Supercars & Superbikes Static Website

A modern, responsive static website for showcasing supercars and superbikes, designed to be hosted on AWS S3.

## 📁 Project Structure

```
testing website/
├── index.html          # Main HTML file
├── style.css           # Stylesheet
├── images/             # All image assets (SVG format)
│   ├── car1.svg
│   ├── car2.svg
│   ├── car3.svg
│   ├── bike1.svg
│   ├── bike2.svg
│   ├── bike3.svg
│   └── gallery1-6.svg
└── README.md           # This file
```

## 🚀 How to Run Locally (Before S3)

### Option 1: Open Directly in Browser (Easiest)
1. Navigate to the `testing website` folder
2. Double-click `index.html`
3. It will open in your default browser

### Option 2: Using VS Code Live Server (Recommended)
1. Open the folder in VS Code
2. Install the "Live Server" extension (by Ritwick Dey)
3. Right-click on `index.html` → "Open with Live Server"
4. Browser auto-refreshes when you make changes

### Option 3: Using Python (If Installed)
```bash
cd "testing website"
python -m http.server 8000
```
Then open: `http://localhost:8000`

### Option 4: Using Node.js
```bash
npx http-server
```

## ☁️ How to Deploy to AWS S3

### Step 1: Create an S3 Bucket
1. Go to AWS Console → S3
2. Click "Create bucket"
3. Enter a unique bucket name (e.g., `my-velocity-website-2026`)
4. Uncheck "Block all public access" (for website hosting)
5. Acknowledge the warning
6. Click "Create bucket"

### Step 2: Enable Static Website Hosting
1. Go to your bucket → Properties
2. Scroll to "Static website hosting" → Edit
3. Select "Enable"
4. Set Index document: `index.html`
5. Optional: Set Error document: `error.html`
6. Save changes
7. Note the **Bucket website endpoint** URL

### Step 3: Upload Files
1. Go to your bucket → Objects tab
2. Click "Upload"
3. Add files:
   - `index.html`
   - `style.css`
   - All images from the `images/` folder
4. Click "Upload"

### Step 4: Make Files Public
**Option A: Using Bucket Policy (Recommended)**
1. Go to Permissions → Bucket Policy → Edit
2. Paste this policy (replace `YOUR-BUCKET-NAME`):

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::YOUR-BUCKET-NAME/*"
        }
    ]
}
```
3. Save changes

### Step 5: Access Your Website
Open the **Bucket website endpoint** URL from Step 2 in your browser. Your website is live! 🎉

## 🎨 Customization Tips

- **Change colors:** Edit `style.css` → look for `#ff2d55` (the accent red) and replace with your color
- **Add cars/bikes:** Copy a card in `index.html` and update the content
- **Replace images:** Swap SVG files in `images/` with your own JPG/PNG files
- **Edit text:** All text content is in `index.html`

## 📝 Notes

- Images are SVG placeholders - replace with real photos for production
- The site is fully responsive (mobile, tablet, desktop)
- No build process needed - pure HTML/CSS
- Works perfectly on S3 static hosting

## 🛠️ Tech Stack

- HTML5
- CSS3 (Grid, Flexbox, Animations)
- SVG (for images)

---

Made with ❤️ for learning AWS S3 hosting
