# How to Update emilyreardon.org

Your site is plain HTML files served directly from GitHub. No build tools, no frameworks.
The only file you ever need to edit to update projects is **projects.html**.

---

## Your working folder

Always work from:
```
~/Documents/GitHub/emilyreardon.github.io/
```
(The alias on your Desktop opens this folder.)

---

## To add or update a project

### Step 1 — Update the Google Sheet
Add or edit the row in your Portfolio Site ProjectsCSV spreadsheet.
This is your source of truth — keep it up to date.

### Step 2 — Open projects.html in a text editor
Open `~/Documents/GitHub/emilyreardon.github.io/projects.html` in TextEdit
(or any code editor like VS Code if you have it).

### Step 3 — Find the projects list
Use Find (Cmd+F) to search for `const projects = [`
You'll see a list of project blocks that look like this:

```
{
  id:          "PER_000",
  type:        "personal",
  title:       "Your Project Title",
  year:        "2026",
  tools:       "Tool 1, Tool 2, Tool 3",
  rationale:   "The why behind the work.",
  description: "What the work actually is.",
  role:        "Your role.",
  videoPaths:  null,
  imagePaths:  null,
  gifPaths:    null
},
```

**To edit an existing project:** find its title with Cmd+F, then change the text
between the quote marks on any line. Don't change anything else.

**To add a new project:** copy one complete block (from `{` to `},`),
paste it right after the opening `const projects = [` line,
and fill in your information.

### Step 4 — Fill in the media field

Only one of videoPaths / imagePaths / gifPaths should have a value; set the others to `null`.

- **Single image or two images:**
  ```
  imagePaths:  ["images/personal/YourFileName"],
  ```
  No file extension needed — the site tries .jpg, .png, etc. automatically.

- **Video (.mp4):**
  ```
  videoPaths:  ["images/personal/Your Video File.mp4"],
  ```

- **Multiple GIFs (shown as a grid):**
  ```
  gifPaths:    [
    "images/personal/file1.gif",
    "images/personal/file2.gif"
  ],
  ```

### Step 5 — Copy your media file into the repo
Drop the image/video/gif into:
```
~/Documents/GitHub/emilyreardon.github.io/images/personal/
```
or
```
~/Documents/GitHub/emilyreardon.github.io/images/professional/
```

### Step 6 — Commit and push
Open Terminal and run:

```bash
cd ~/Documents/GitHub/emilyreardon.github.io
git add projects.html images/
git commit -m "add [project name]"
git push
```

Wait about 60 seconds, then refresh emilyreardon.org.

---

## To edit any other page

Same process — open the file, edit the text, save, commit, push.

- `about.html` — About page
- `writing.html` — Writing page
- `teaching.html` — Teaching page
- `index.html` — Homepage

---

## With AI help (Cowork)

If you'd rather not edit HTML directly, open Cowork, say:
*"Update my projects page — here's the new CSV"* and drag in your exported CSV.
Claude will make the edit and give you the commit command to run.

To export the CSV: in Google Sheets go to **File → Download → Comma Separated Values (.csv)**

---

## If something breaks

1. Check the GitHub Pages deployment at:
   `https://github.com/emilyreardon/emilyreardon.github.io/settings/pages`
   Source should be: **Deploy from a branch / main / / (root)**

2. To undo your last change:
   ```bash
   cd ~/Documents/GitHub/emilyreardon.github.io
   git revert HEAD
   git push
   ```
