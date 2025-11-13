# 🔄 How to Commit and Redeploy on Render

Complete guide to updating your deployed Stock Assistant Web application.

---

## 🚀 Quick Process

1. **Make changes** to your code
2. **Commit** changes to Git
3. **Push** to GitHub
4. **Render auto-deploys** (or manually trigger)

---

## 📝 Step-by-Step: Commit and Push

### Step 1: Navigate to Your Project

```bash
cd /Users/maneeshmukundan/projects/agents/1_foundations/stockassistantweb
```

### Step 2: Check What Changed

```bash
git status
```

This shows you which files were modified.

### Step 3: Add Changes

```bash
# Add all changes
git add .

# Or add specific files
git add stock_assistant_web.py
git add requirements.txt
```

### Step 4: Commit Changes

```bash
git commit -m "Description of your changes"
```

**Good commit messages:**
- `"Add investment disclaimer to UI"`
- `"Fix: Update API error handling"`
- `"Update dependencies in requirements.txt"`
- `"Improve stock analysis responses"`

### Step 5: Push to GitHub

```bash
git push origin main
```

---

## 🔄 Render Auto-Deployment

### Automatic Deployment (Default)

**Render automatically redeploys when you push to GitHub!**

1. Push your changes: `git push origin main`
2. Render detects the push (usually within seconds)
3. Render automatically:
   - Pulls the latest code
   - Runs your build command
   - Restarts your service
4. Your app is updated! (takes 1-3 minutes)

**You'll see:**
- Build status in Render dashboard
- "Deploying..." → "Live" status
- New deployment in "Events" tab

---

## 🎯 Manual Redeploy (If Needed)

Sometimes you want to redeploy without code changes:

### Option 1: Via Render Dashboard

1. Go to your Render dashboard
2. Click on your service (`stock-assistant`)
3. Go to **"Manual Deploy"** tab
4. Click **"Deploy latest commit"**
5. Wait for deployment to complete

### Option 2: Via Render CLI (Advanced)

```bash
# Install Render CLI (if not installed)
npm install -g render-cli

# Login
render login

# Deploy
render deploy
```

---

## 📊 Monitor Deployment

### View Deployment Status

1. Go to Render dashboard
2. Click your service
3. Check **"Events"** tab:
   - See all deployments
   - View build logs
   - Check deployment status

### View Logs

1. Go to **"Logs"** tab
2. See real-time logs:
   - Build process
   - Application startup
   - Runtime errors
   - API calls

### Check Metrics

1. Go to **"Metrics"** tab
2. Monitor:
   - CPU usage
   - Memory usage
   - Request count
   - Response times

---

## 🔍 Common Scenarios

### Scenario 1: Update Code

```bash
# 1. Make your changes
# Edit stock_assistant_web.py, etc.

# 2. Commit and push
git add .
git commit -m "Update: Add new feature"
git push origin main

# 3. Render auto-deploys (wait 1-3 minutes)
# 4. Check Render dashboard for status
```

### Scenario 2: Update Environment Variables

1. Go to Render dashboard
2. Click your service → **"Environment"** tab
3. Add/update variables
4. Click **"Save Changes"**
5. Render automatically redeploys

**No Git commit needed!**

### Scenario 3: Rollback to Previous Version

1. Go to Render dashboard
2. Click your service → **"Events"** tab
3. Find the previous deployment
4. Click **"..."** → **"Redeploy this commit"**

### Scenario 4: Update Dependencies

```bash
# 1. Update requirements.txt
# Add new packages, update versions

# 2. Commit and push
git add requirements.txt
git commit -m "Update: Add new dependencies"
git push origin main

# 3. Render rebuilds with new dependencies
```

---

## ⚡ Quick Commands Reference

```bash
# Check status
git status

# Add all changes
git add .

# Commit
git commit -m "Your message here"

# Push to GitHub (triggers auto-deploy)
git push origin main

# View recent commits
git log --oneline -5

# Check remote
git remote -v
```

---

## 🆘 Troubleshooting

### Problem: Changes Not Deploying

**Check:**
1. Did you push to the correct branch? (`main`)
2. Is Render connected to the right GitHub repo?
3. Check Render dashboard → "Events" tab for errors
4. Verify your GitHub repository has the latest commit

**Solution:**
```bash
# Verify you're on main branch
git branch

# Check if changes are pushed
git log origin/main --oneline -1

# Force push if needed (be careful!)
git push origin main --force
```

### Problem: Build Fails After Push

**Check:**
1. Go to Render → "Logs" tab
2. Look for error messages
3. Common issues:
   - Syntax errors in code
   - Missing dependencies
   - Import errors
   - Environment variables not set

**Solution:**
- Fix the error locally first
- Test locally: `python stock_assistant_web.py`
- Commit fix and push again

### Problem: App Not Updating

**Check:**
1. Render dashboard → "Events" tab
2. Is deployment stuck or failed?
3. Check "Logs" for errors

**Solution:**
- Manually trigger redeploy
- Check if Root Directory is correct (should be empty)
- Verify Start Command is correct

---

## ✅ Best Practices

1. **Test Locally First**
   ```bash
   python stock_assistant_web.py
   ```
   Make sure it works before pushing!

2. **Use Descriptive Commit Messages**
   - Clear, specific messages
   - Explain what changed and why

3. **Check Render Dashboard After Push**
   - Verify deployment started
   - Monitor for errors
   - Confirm it went "Live"

4. **Keep Dependencies Updated**
   - Regularly update `requirements.txt`
   - Test compatibility before deploying

5. **Monitor Logs**
   - Check logs after deployment
   - Look for warnings or errors
   - Verify app is working correctly

---

## 📋 Complete Workflow Example

```bash
# 1. Make changes to your code
# (Edit stock_assistant_web.py, etc.)

# 2. Test locally
python stock_assistant_web.py
# Test in browser at http://localhost:7860

# 3. Commit changes
cd /Users/maneeshmukundan/projects/agents/1_foundations/stockassistantweb
git add .
git commit -m "Add investment disclaimer"

# 4. Push to GitHub
git push origin main

# 5. Monitor Render
# - Go to Render dashboard
# - Watch "Events" tab
# - Wait for "Live" status (1-3 minutes)

# 6. Test deployed app
# - Visit your Render URL
# - Verify changes are live
```

---

## 🔗 Quick Links

- **Your Repository:** https://github.com/maneeshmukundan1379/stockassistantweb
- **Render Dashboard:** https://dashboard.render.com
- **Your Service:** Check Render dashboard for your service URL

---

## 💡 Pro Tips

1. **Use Git Tags for Versions**
   ```bash
   git tag -a v1.0.0 -m "Version 1.0.0"
   git push origin v1.0.0
   ```

2. **Create a Deployment Script**
   ```bash
   # deploy.sh
   git add .
   git commit -m "$1"
   git push origin main
   echo "Deployment triggered! Check Render dashboard."
   ```

3. **Set Up GitHub Actions** (Advanced)
   - Automate testing before deployment
   - Run linting/formatting
   - Auto-deploy on successful tests

---

**Remember:** Render automatically redeploys when you push to GitHub. Just commit, push, and wait! 🚀

