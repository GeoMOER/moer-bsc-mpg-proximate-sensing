---
title: GitLab HowTo
header:
  image: "/assets/images/title/header.png"
  caption: 'Photo by [Lukas Goumbik, from Pixabay](https://pixabay.com/de/users/goumbik-3752482/?utm_source=link-attribution&utm_medium=referral&utm_campaign=image&utm_content=2055522){:target="_blank"}'
---


# How to Contribute
 
This guide explains how to add your work to the project website.
No prior experience with Git needed — just follow the steps.
 
---
 
## Before you start
 
Make sure you have done these once:
 
1. **Log into GitLab** in your browser via the [university portal](https://gitlab.uni-marburg.de/users/sign_in) - if the first option does not work, use the second
2. **Install Git** → [git-scm.com](https://git-scm.com)
3. **Set up your identity** — open a terminal and run:

   ```bash
   git config --global user.name "Your Name"
   git config --global user.email "your@uni-marburg.de"
   ```
4. **Set up SSH** so you can push without a password:
   ```bash
   ssh-keygen -t ed25519 -C "laptop"
   cat ~/.ssh/id_ed25519.pub
   ```
   Copy the output and add it in GitLab under:
   **Profile (on the upper right) → Preferences → Access → SSH keys  → Add new key**
   Test it:
   ```bash
   ssh -T git@gitlab.uni-marburg.de
   # Expected: Welcome to GitLab, @yourname!
   ```
 
---
 
## Step 1 — Clone the repo
 
Open a terminal in the path/ folder structure where you want to work from, there are different options:

- **VS Code (open source, needs to be installed):** open the project folder, then `Terminal → New Terminal` —
  it opens directly in the right place ✅
- **Windows:** navigate to the folder in Explorer, right-click →
  *Open in Terminal* (or *Git Bash Here* if you have Git installed)
- **macOS:** right-click the folder in Finder → *New Terminal at Folder*

run:
```bash
git clone git@gitlab.uni-marburg.de:lehre/sose-2026/proximity-sensing-of-biological-diversity/example.git
cd example
```
 
You now have a local copy of the project on your computer.
 
---
 
## Step 2 — Create your branch
 
Every person works on their own branch. This keeps your changes separate from everyone else's until you are ready.
 
```bash
git checkout main
git pull origin main
git checkout -b feature/yourname-taskid
``` 
Replace `yourname-taskid` with something like `anna-P3` or `ben-F1`.

-b creates a new branch called feature/yourname-taskid
checkout switches you to that branch immediately

> ⚠️ Always start from an up-to-date `main`. Running `git pull` first prevents headaches later.
 
---
 
## Step 3 — Add your content
 
Your two files go here:
 
| What | Where |
|------|-------|
| Your page | `_features/yourname-taskid.md` |
| Your code (if applicable) | `assets/code/yourname-taskid.py` |
| Your images | `assets/images/yourname-taskid-description.png` |
 
Copy `_features/example-feature.md`, rename it, and fill in your content.
 
---
 
## Step 4 — Save your work (commit & push)
 
Do this regularly — not just at the end!
 
```bash
git add .
git commit -m "feat: short description of what you did"
git push origin feature/yourname-taskid
```
 
Good commit messages:
- ✅ `feat: add PIR sensor wiring diagram`
- ✅ `docs: describe RGB analysis approach`
- ❌ `update` / `changes` / `asdf`
---
 
## Step 5 — Publish your work (Merge Request)
 
When your page is ready:
 
1. Go to your project on GitLab
2. Click **Merge Requests → New merge request**
3. Source branch: `feature/yourname-taskid` → Target: `main`
4. Give it a title and click **Create merge request**
5. Click **Merge** — your page is now part of the website 🎉
The website updates automatically within a few minutes.
You can watch the build under **CI/CD → Pipelines**.
 
---
 
## Daily workflow (after the first setup)
 
Every time you sit down to work:
 
```bash
git checkout main
git pull origin main
git checkout feature/yourname-taskid
git add .
git commit -m "feat: what you did today"
git push origin feature/yourname-taskid
```
 
---
 
## Something went wrong?
 
| Problem | Solution |
|---------|----------|
| `push` rejected | Run `git pull origin main` first, then push again |
| Accidentally edited the wrong file | `git checkout -- filename` to undo |
| Committed something wrong | `git revert HEAD` to safely undo the last commit |
| Pipeline is red | Check **CI/CD → Pipelines → click the red job** to see the error |
| Not sure what state you're in | `git status` — always a good first step |
 
---
 
## Writing your page
 
Your feature page is a Markdown file. Markdown is plain text with simple formatting symbols — no HTML needed.
 
### Text formatting
 
```markdown
# Big heading
## Smaller heading
### Even smaller
 
Normal paragraph text. Just write.
 
**bold**, *italic*, `code`
 
> This is a blockquote — good for notes or warnings
```
 
### Lists
 
```markdown
- bullet point
- another one
  - indented
 
1. numbered
2. list
```
 
### Links and images
 
```markdown
[Link text](https://example.com)
 
![Image description]({{ site.baseurl }}/assets/images/yourname-image.png)
```
 
> ⚠️ Always use `{{ site.baseurl }}/assets/images/` for images —
> other paths will break on the live site.
 
### Code blocks
 
Use triple backticks with the language name for syntax highlighting:
 
````markdown
```python
def hello():
    print("Hello!")
```
````
 
Supported: `python`, `bash`, `yaml`, `json`, `html`, `javascript` and many more.
 
### Tables
 
```markdown
| Column 1 | Column 2 |
|----------|----------|
| cell     | cell     |
| cell     | cell     |
```
 
---
 
## Adding images
 
1. Save your image in `assets/images/` — use a clear name like `anna-P3-wiring.png`
2. Reference it in your Markdown:
   ```markdown
   ![Wiring diagram]({{ site.baseurl }}/assets/images/anna-P3-wiring.png)
   ```
3. `git add assets/images/anna-P3-wiring.png` — don't forget to commit the image too!
**Supported formats:** `.png`, `.jpg`, `.gif`, `.svg`
 
**Keep file sizes reasonable** — compress photos before adding them.
Large images slow down the site and bloat the repo.
 
---
 
## Page structure
 
Every feature page starts with a **front matter block** — this tells Jekyll
the title and URL of your page:
 
```markdown
---
title: My Feature
description: One sentence summary shown on the features overview.
---
 
# My Feature
 
Content starts here...
```
 
> ⚠️ The `---` lines are required. Without them Jekyll ignores the file.
 
A good feature page typically covers:
 
| Section | What to write |
|---------|---------------|
| Intro | What does this feature do? One short paragraph. |
| Hardware | What components, which pins — include a wiring diagram |
| How it works | Explain the logic in plain language |
| Key Code | The most important snippet, with explanation |
| Full Source | Link to your `.py` file in `assets/code/` |
| Results | What did you observe? What worked, what didn't? |
| Time log | Rough breakdown: *research 3h, wiring 2h, coding 4h* |
 
---
 
## Git: what to remember
 
### Commit often, commit small
 
Don't save everything up for one big commit at the end.
Commit whenever you finish a meaningful chunk:
 
```bash
git add .
git commit -m "feat: add wiring diagram for PIR sensor"
# ... work more ...
git commit -m "docs: explain polling interval choice"
# ... work more ...
git commit -m "feat: add results section with RGB plots"
```
 
This gives you a safety net — you can always go back to any of these points.
 
### Before you push: pull first
 
If others have merged to `main` since you last pulled, your push will be rejected.
Always do:
 
```bash
git pull origin main
```
 
before pushing. 

If there is a conflict (two people edited the same line), Git will mark it in the file like this:
 
```
<<<<<<< HEAD
your version
=======
their version
>>>>>>> feature/someone-else
```
 
Just pick the right version, delete the marker lines, then commit again.
 
### Merge Request checklist
 
Before you click **Merge**, check:
 
- [ ] Your page renders correctly locally (`bundle exec jekyll serve`)
- [ ] All images show up (no broken image icons)
- [ ] Your code file is in `assets/code/`
- [ ] The link to your code file works
- [ ] Front matter has `title` and `description`
- [ ] Your time log is included
---
 
## Running the site locally
 
Before pushing, you can preview the site on your own computer.
This is much faster than waiting for the pipeline every time.
 
### One-time setup
 
You need Ruby installed:
 
- **Windows:** [rubyinstaller.org](https://rubyinstaller.org) — use the version that includes DevKit
- **macOS:** Ruby is pre-installed, or use `brew install ruby`
- **Linux:** `sudo apt install ruby-full`
Then install Jekyll and Bundler:
 
```bash
gem install bundler
```
 
And install the project's dependencies (run this once inside the repo folder):
 
```bash
bundle install
```
 
### Start the local server
 
```bash
bundle exec jekyll serve
```
 
Then open [http://localhost:4000](http://localhost:4000) in your browser.
 
The site **updates automatically** as you save files — no need to restart.
Just refresh the browser.
 
### Stop the server
 
`Ctrl + C` in the terminal.
 
> 💡 You don't need to run the server continuously.
> Start it when you want to check your page, stop it when you're done.
 
### Common issues
 
| Problem | Solution |
|---------|----------|
| `bundle: command not found` | Run `gem install bundler` first |
| Port 4000 already in use | `bundle exec jekyll serve --port 4001` |
| Page not updating | Save the file and hard-refresh the browser (`Ctrl+Shift+R`) |
| `_features` pages not showing | Check that front matter has `---` on both sides |
| vdollar_percent_expand: unknown key during clone |  Windows: HOME fix see below |

### Windows: HOME variable fix

If you see this error on Windows:
```
vdollar_percent_expand: unknown key %/
fatal: Could not read from remote repository.
```

Git has incorrectly expanded your HOME path (e.g. `C:\Users\%yourname%\.ssh` instead of `C:\Users\yourname\.ssh`).

**Fix — run these in PowerShell as Administrator:**

```powershell
[System.Environment]::SetEnvironmentVariable("HOME", "C:\Users\YOURNAME", "User")
```

```bash
git config --global core.sshCommand "C:/Windows/System32/OpenSSH/ssh.exe"
```

Replace `YOURNAME` with your actual Windows username. Then verify:

```powershell
echo $env:HOME
# Should print: C:\Users\YOURNAME
```

After that, `git clone` should work normally.