---
layout: default
title: "GitHub Setup"
nav_order: 2
permalink: /git/
---
# Github Setup

Please do not use a public github fork of this repository! We do not want solutions to be public. You should work in your own private repo.
We recommended creating a mirrored private repository with multiple remotes. The following steps go over how to achieve this.

The easiest (but not recommended) way is to download a zip from GitHub and make a private repository from that. The main disadvantage with this is that whenever there is an update to the base code, you will have to re-download the zip and manually merge the differences into your code. This is a pain, and you already have a lot to do in 15462/662, so instead, let `git` take care of this cumbersome "merging-updates" task:

1. Clone Scotty3D normally
    - `git clone https://github.com/CMU-Graphics/Scotty3D.git`

2. Create a new private repository (e.g. `MyScotty3D`)
    - Do not initialize this repository - keep it completely empty.
    - Let's say your repository is now hosted here: `https://github.com/your_id/MyScotty3D.git`

3. Ensure that you understand the concept of `remote`s in git.
    - When you clone a git repository, the default remote is named 'origin' and set to the URL you cloned from.
    - We will set the `origin` of our local clone to point to `MyScotty3D.git`, but also have a remote called `sourcerepo` for the public `Scotty3D` repository.

4. Now go back to your clone of Scotty3D. This is how we add the private remote:
    - Since we cloned from the `CMU-Graphics/Scotty3D.git` repository, the current value of `origin` should be `https://github.com/CMU-Graphics/Scotty3D.git`
        - You can check this using `git remote -v`, which should show:
            ```
            origin      https://github.com/CMU-Graphics/Scotty3D.git (fetch)
            origin      https://github.com/CMU-Graphics/Scotty3D.git (push)
            ```
    - Rename `origin` to `sourcerepo`:
        - `git remote rename origin sourcerepo`
    - Add a new remote called `origin`:
        - `git remote add origin https://github.com/your_id/MyScotty3D.git`
    - We can now push the starter code to our private copy:
        - `git push origin -u main`

5. Congratulations! you have successfully _mirrored_ a git repository with all past commits intact. 

Now, let's see why this setup may be useful: say we start doing an assignment and commit regularly to our private repo (our `origin`). Then the 15-462 staff push some new changes to the Scotty3D skeleton code that we want to pull in. But, we don't want to mess up the changes we've added to our private copy. Here's where git comes to the rescue:

1. Commit all local changes to your `origin`.
2. Run `git pull sourcerepo main` - this pulls all the changes from `sourcerepo` into your local copy.
    - If there are files with changes in both `origin` and `sourcerepo`, git will attempt to automatically merge the updates. Git may create a "merge" commit for this.
    - Unfortunately, there may be conflicts. Git will handle as many merges as it can, then then tell you which files have conflicts that need manual resolution. You can resolve the conflicts in your text editor and create a new commit to complete the `merge` process.
3. After you have completed the merge, you now have all the updates locally. Push to your private origin to publish changes there too:
    - `git push origin main`

