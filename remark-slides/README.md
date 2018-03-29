# Remark assets for slides management at Bluewind

Please include this repository as a submodule in your slides project
and enjoy using Markdown for easy preparation of HTML based slides
at Bluewind.

# Starting a new slides set

  - start a new repository for the slides project
  - include this repository as a submodule
  - create a few useful folders
  - copy a few useful files from this repository up to the new project
    and modify if needed according to the needs
  - edit an initial README.md for this new repository
  - start adding new slides or modifying existing slides (see below)

```bash
# commands in a bash shell
mkdir slides-set && cd $_
touch README.md
git init
git add . && git commit -m "new slides set"
git submodule add git@git.bwlocal.it:BWTEACH/remark-slides.git
mkdir assets && touch assets/.keepme
mkdir stuff && touch stuff/.keepme
mkdir pdf && touch pdf/.keepme
cp remark-slides/bwlogo.png assets
for file in remark-slides/*.example; do cp "$file" "$(basename "$file" .example)"; done
for file in remark-slides/.*.example; do cp "$file" "$(basename "$file" .example)"; done
nano README.md
```

  - create a repository in the official Bluewind Gitlab server and configure it for CI
  - modify how submodule(s) are referenced so that CI can manage them
  - add remote and pull repository

```bash
# commands in a bash shell
sed -i 's/git@git.bwlocal.it:/..\/..\//g' .gitmodules
git add . && git commit -m "new slides set ready to start"
git remote git@git.bwlocal.it:<PATH_TO_REPO>
git push origin master
```

  - now you can start adding slides

# Slides preparation and usage workflow

Please read the enclosed specific manual `remark-README.md.example`.

### Credits

- 2017 Stefano Costa, Bluewind
- https://github.com/gnab/remark/wiki
- http://tech.graze.com/2015/07/31/easily-create-slideshow-presentations-from-markdown-with-remark-js/
