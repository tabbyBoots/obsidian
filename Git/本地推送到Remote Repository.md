### [[Git]] [[push]]
### create a new repository on the command line

echo "# obsidian" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/tabbyBoots/obsidian.git
**git push -u origin main**
### [[Git]] 
### push an existing repository from the command line

git remote add origin https://github.com/tabbyBoots/obsidian.git
git branch -M main
**git push -u origin main**