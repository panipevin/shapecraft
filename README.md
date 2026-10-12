# Shapecraft: 3D printing cost calculator

A free cost calculator, quote tracker, dashboard and expense log for 3D printed parts. Your data is saved in your browser and, if you connect it, in your own Google Sheet.

## Files

| File | What it is | Goes to GitHub? |
|---|---|---|
| `index.html` | The whole website | Yes |
| `README.md` | These instructions | Yes |
| `Code.gs` | Google Sheet connector (contains your passcode) | **No.** Paste it into Apps Script only |

---

## Part 1: Connect a Google Sheet (your database)

1. Go to [sheets.google.com](https://sheets.google.com) and create a new blank sheet. Name it **Shapecraft Data**.
2. In the sheet, open **Extensions > Apps Script**.
3. Delete the sample code, then paste in everything from `Code.gs`.
4. At the top, change `change-this-passcode` to a passcode only you know. Click **Save**.
5. Click **Deploy > New deployment**. Click the gear icon and choose **Web app**.
   - **Execute as:** Me
   - **Who has access:** Anyone
6. Click **Deploy** and allow access when Google asks. (If you see "Google hasn't verified this app", click **Advanced**, then **Go to project**. It is your own script.)
7. Copy the **Web app URL**. It ends in `/exec`.
8. Open the website, go to the **Google Sheet** tab, paste the URL and your passcode, and press **Save and connect**.

Two tabs, **Quotes** and **Expenses**, are created in your sheet automatically. You can read them, sort them, or build charts from them. Don't edit the last column ("Data"), because the website reads it back.

If you change the script code later, use **Deploy > Manage deployments > Edit > New version** so the changes go live.

### How the sync works
- The website saves to your browser first, then sends everything to the sheet a moment later.
- When you open the site, it loads the latest data from the sheet.
- If you were offline, your changes are kept and sent next time.
- Last save wins. Don't edit on two devices at the same moment.

### Privacy
- The passcode and URL are stored only in the browser where you entered them. They are not in the website's code.
- The website is public, but nobody can see your data without your URL **and** passcode.
- Use a passcode that is not used anywhere else.

---

## Part 2: Put the website on GitHub (free hosting with GitHub Pages)

### Option A: In the browser (easiest)
1. Create a free account at [github.com](https://github.com).
2. Click **+ > New repository**.
   - Name: `shapecraft`
   - Visibility: **Public** (free GitHub Pages needs a public repository)
   - Click **Create repository**.
3. Click **uploading an existing file**, drag in `index.html` and `README.md`, and click **Commit changes**.
4. Go to **Settings > Pages**.
   - **Source:** Deploy from a branch
   - **Branch:** `main`, folder `/ (root)`
   - Click **Save**.
5. Wait one or two minutes. Your site will be live at:
   `https://YOUR-USERNAME.github.io/shapecraft/`

### Option B: With Git on your computer
```bash
git init
git add index.html README.md
git commit -m "Shapecraft calculator"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/shapecraft.git
git push -u origin main
```
Then do step 4 above.

### Updating the site later
Upload a new `index.html` to the repository (**Add file > Upload files**) and commit. The site updates within a minute or two.

### Your own domain (optional)
Buy a domain, then in **Settings > Pages > Custom domain** enter it and follow GitHub's DNS instructions.

---

## Notes
- Prices are in Indian rupees (₹). Defaults are starting values, so change them to your real costs.
- The calculator gives estimates. Check the numbers against your own costs before quoting a customer.
