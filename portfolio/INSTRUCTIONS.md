# Portfolio Content Update Instructions
## How to update your portfolio, resume, and download files — without writing any code

---

## The Core Concept: One File Controls Everything

All your resume and portfolio content lives in ONE file:

```
content/resume-data.json
```

When you change anything in that file, the following all update automatically:
- Portfolio website (all sections)
- Resume page (resume.html)
- Skills section
- Experience timeline
- Project cards
- Certifications
- Education & Achievements
- Contact information

---

## How to Update Content (Step-by-Step)

### Step 1: Open the file
Open `content/resume-data.json` in any text editor:
- **Windows**: Notepad, Notepad++, or VS Code
- **Mac**: TextEdit (plain text mode), or VS Code
- **Online**: Edit directly on GitHub if hosted there

### Step 2: Find the section you want to change
The file is organized into clear sections. Use Ctrl+F (or Cmd+F) to search.

### Step 3: Save the file
Save and refresh your browser. Changes appear immediately.

---

## Common Update Scenarios

---

### ✏️ Update Your Name, Title, or Contact Info

Find the `"profile"` section at the top:

```json
"profile": {
  "name": "Pavan Kalyan Gollapalli",
  "title": "Senior Data Engineer",
  "email": "your@email.com",
  "phone": "+91-9885094547",
  "linkedin": "https://linkedin.com/in/YOUR-SLUG-HERE",
  "github": "https://github.com/YOUR-USERNAME-HERE"
}
```

**Change any value between the quote marks.** Do not remove the quotes or commas.

---

### ✏️ Update Your LinkedIn or GitHub URL

Same `"profile"` section:

```json
"linkedin": "https://linkedin.com/in/pavan-kalyan-gollapalli",
"github": "https://github.com/pavankalyan"
```

Replace the URL between the quote marks. Keep the `https://` prefix.

---

### ✏️ Update the Professional Summary

Find `"summary"`:

```json
"summary": "Senior Data Engineer with 4+ years..."
```

Replace the text between the quote marks. Keep it on one line.

---

### ✏️ Add a New Skill

Find `"skills"`. Each skill group looks like:

```json
{
  "category": "Languages & Scripting",
  "items": ["Python", "PySpark", "Spark SQL", "SQL", "Shell Scripting"]
}
```

**To add a skill to an existing group:** Add it inside the square brackets, separated by a comma:
```json
"items": ["Python", "PySpark", "Spark SQL", "SQL", "Shell Scripting", "Scala"]
```

**To add a new skill group:** Copy and paste one of the existing blocks, change the `"category"` and `"items"`:
```json
{
  "category": "New Category",
  "items": ["Skill 1", "Skill 2"]
},
```
⚠️ Make sure to add a comma after the `}` if it's not the last group.

---

### ✏️ Add a New Job / Update Work Experience

Find `"experience"`. Each job looks like:

```json
{
  "id": "company-year",
  "company": "Company Name",
  "role": "Your Role",
  "location": "Hyderabad, India",
  "startDate": "Month YYYY",
  "endDate": "Present",
  "type": "Full-time",
  "project": "Project name — brief description",
  "bullets": [
    "First bullet point describing your work and impact.",
    "Second bullet point with metrics and results."
  ],
  "tags": ["Skill1", "Skill2", "Skill3"]
}
```

**To add a new job:** Copy the entire block above (from `{` to `}`), paste it at the TOP of the `"experience"` array (most recent first), and update all the fields.

**To update bullets:** Change the text between the quote marks inside `"bullets": [ ]`.

---

### ✏️ Add a New Project

Find `"projects"`. Each project looks like:

```json
{
  "id": "unique-project-id",
  "title": "Project Title",
  "company": "Company Name",
  "year": "2025",
  "description": "What you built and the impact it had.",
  "tech": ["PySpark", "FastAPI", "AWS S3"],
  "metrics": ["500K+ records/day", "99.9% uptime"],
  "githubUrl": "https://github.com/you/project",
  "liveUrl": ""
}
```

Copy and paste a block, update the fields.
- Leave `"githubUrl"` and `"liveUrl"` as `""` if you don't have links yet.
- The `"id"` must be unique (use lowercase with hyphens, e.g., `"kafka-streaming-project"`).

---

### ✏️ Add a New Certification

Find `"certifications"`:

```json
{
  "title": "AWS Certified Solutions Architect",
  "issuer": "Amazon Web Services",
  "year": "2025",
  "badgeUrl": "",
  "verifyUrl": "https://aws.amazon.com/verification/..."
}
```

Add a comma after the last `}` in the existing list, then paste the new block.

---

### ✏️ Update Your Profile Photo

1. Save your photo as `profile.jpg`
2. Place it in the `public/images/` folder
3. In `resume-data.json`, confirm the path is: `"profilePhoto": "/images/profile.jpg"`

---

### ✏️ Update Your Downloadable Resume Files

**Every time you update your Word or PDF resume:**

1. Save the PDF as `resume.pdf`
2. Save the Word file as `resume.docx`
3. Place both files in the `public/resume/` folder
4. Overwrite the old files

The download buttons on the portfolio automatically point to these paths:
```json
"resumePdf": "/resume/resume.pdf",
"resumeDocx": "/resume/resume.docx"
```

---

## File Structure Overview

```
portfolio/
│
├── index.html              ← Main portfolio website (DO NOT EDIT for content)
├── resume.html             ← Printable resume page (DO NOT EDIT for content)
│
├── content/
│   └── resume-data.json    ← ✅ EDIT THIS FILE ONLY for all content updates
│
├── public/
│   ├── resume/
│   │   ├── resume.pdf      ← Replace with your latest PDF resume
│   │   └── resume.docx     ← Replace with your latest Word resume
│   └── images/
│       └── profile.jpg     ← Replace with your photo
│
└── INSTRUCTIONS.md         ← This file
```

---

## How to Run Locally (Preview on Your Computer)

You need a simple local server because the HTML files fetch `resume-data.json`.

**Option A — Python (no install required on Mac/Linux):**
```bash
cd portfolio
python3 -m http.server 8080
```
Then open: http://localhost:8080

**Option B — Node.js:**
```bash
npx serve .
```

**Option C — VS Code:**
Install the "Live Server" extension → right-click `index.html` → "Open with Live Server"

---

## How to Deploy (Make It Live on the Internet)

### Option 1: GitHub Pages (Free)
1. Create a GitHub account at github.com
2. Create a new repository called `portfolio`
3. Upload all files from the `portfolio/` folder
4. Go to Settings → Pages → Source: main branch → `/root`
5. Your site will be live at: `https://yourusername.github.io/portfolio`

### Option 2: Netlify (Free, easier)
1. Go to netlify.com and sign up
2. Drag and drop the entire `portfolio/` folder onto Netlify
3. Your site is live instantly with a URL like `https://random-name.netlify.app`
4. To update: drag and drop again, or connect to GitHub for auto-deploy

### Option 3: Vercel (Free)
1. Go to vercel.com
2. Connect your GitHub repository
3. Auto-deploys on every commit

---

## JSON Editing Rules (Important!)

To avoid breaking the file, follow these rules:

| Rule | Example |
|------|---------|
| Strings go in double quotes | `"value"` not `'value'` |
| Numbers have no quotes | `72` not `"72"` |
| Lists use square brackets | `["item1", "item2"]` |
| Objects use curly braces | `{ "key": "value" }` |
| Items separated by commas | `"a", "b", "c"` (no trailing comma on last item) |

**To validate your JSON:** Paste it at https://jsonlint.com — it will show you exactly which line has an error.

---

## 5-Minute Update Checklist

When you get a new job or want to refresh your portfolio:

- [ ] Open `content/resume-data.json`
- [ ] Update `"profile"` if name/contact/links changed
- [ ] Add new job at the TOP of `"experience"`
- [ ] Add new projects to `"projects"`
- [ ] Add new certifications to `"certifications"`
- [ ] Update `"summary"` to reflect new seniority
- [ ] Save the file and refresh browser
- [ ] Export new PDF resume and copy to `public/resume/resume.pdf`
- [ ] Copy updated Word resume to `public/resume/resume.docx`
- [ ] Push to GitHub / re-deploy to Netlify

Total time: under 5 minutes for a full update. ✅

---

## ATS Score Tracking

Your current ATS scores are stored in the file for reference:

```json
"atsScores": {
  "original": 72,
  "optimized": 87,
  "interviewReadiness": 82,
  "recruiterAppeal": 84,
  "shortlistProbability": "72–78%"
}
```

These are reference values only and don't appear on the public site.

---

*Generated by Claude · Anthropic | For personal use only. All resume data is confidential.*
