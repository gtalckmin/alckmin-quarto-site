# Deployment Instructions

## Step 1: Create GitHub Repository

1. Go to https://github.com/new
2. Repository name: `alckmin-quarto-site`
3. Description: `Personal academic website built with Quarto`
4. Make it **Public** (required for free GitHub Pages)
5. Don't initialize with README (we already have one)
6. Click "Create repository"

## Step 2: Push to GitHub

```bash
cd /home/gtalckmin/alckmin-quarto-site

# Add remote repository (replace with your GitHub username)
git remote add origin https://github.com/gtalckmin/alckmin-quarto-site.git

# Push to GitHub
git branch -M main
git push -u origin main
```

## Step 3: Enable GitHub Pages

1. Go to your repository on GitHub
2. Click **Settings** tab
3. Scroll to **Pages** section (left sidebar)
4. Under **Source**, select **GitHub Actions**
5. The workflow will run automatically on next push

## Step 4: Access Your Site

Your site will be available at:
`https://gtalckmin.github.io/alckmin-quarto-site`

## Step 5: Custom Domain (Optional)

If you have a custom domain:

1. In repository settings → Pages
2. Add your custom domain
3. Create a CNAME file in the root:

```bash
echo "yourdomain.com" > CNAME
git add CNAME
git commit -m "Add custom domain"
git push
```

## Maintenance

### Adding New Blog Posts

1. Create new file: `posts/your-post-title/index.qmd`
2. Add frontmatter with title, date, categories, tags
3. Write content with embedded R code if needed
4. Commit and push - site rebuilds automatically

### Updating Content

1. Edit any `.qmd` file
2. Commit and push changes
3. GitHub Actions will rebuild and deploy automatically

### Local Development

```bash
# Preview locally
quarto preview

# Build locally
quarto render

# Check for issues
quarto check
```

## Troubleshooting

### Build Failures
- Check GitHub Actions logs for specific errors
- Ensure R packages are installed (add to workflow if needed)
- Validate YAML frontmatter in posts

### Styling Issues
- Edit `custom.scss` for theme customization
- Modify `styles.css` for additional styling
- Check Bootstrap documentation for classes

### R Code Issues
- Test locally with `quarto render`
- Ensure required packages are listed in workflow
- Use `#| eval: false` to skip problematic code blocks
