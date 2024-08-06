vscode
git pull (rebase)
git push --force

cancel rebase, abort
git rebase to main
git push force

## start project, clone project example subdirectory template

degit
pnpm create next-app new-next-app
pnpm dlx create-turbo@latest --example [example-name]
pnpm dlx degit https://github.com/payloadcms/payload-3.0-demo

## submodules

- use git
  make sure to configure user.name and user.email in git vscode
  git config --global user.email jigzpalillo@gmail.com
  git config --global user.name jigz

- use git submodules, use submodules
  vscode git clone recursive, switch all branches to main
  Submodule Guide, Add, Remove, archive/backup
  https://chrisjean.com/git-submodules-adding-using-removing-and-updating/
  https://gist.github.com/myusuf3/7f645819ded92bda6677
  https://blog.nrwl.io/dev-workflow-using-git-submodules-and-yarn-workspaces-14fd06c07964
  git commands guide, setup github repo
  https://www.freecodecamp.org/news/how-to-delete-a-git-branch-both-locally-and-remotely/
  https://www.theserverside.com/blog/Coffee-Talk-Java-News-Stories-and-Opinions/How-to-remove-git-submodules
  git submodule add https://github.com/jigz/zero-912b-3516-c3ce-2dc7 packages/zero-912b-3516-c3ce-2dc7
  To remove a submodule you need to:
  Delete the relevant section from the .gitmodules file.
  Stage the .gitmodules changes git add .gitmodules
  Delete the relevant section from .git/config.
  Run git rm --cached path_to_submodule (no trailing slash).
  Run rm -rf .git/modules/path_to_submodule (no trailing slash).
  Commit git commit -m "Removed submodule "
  Delete the now untracked submodule files rm -rf path_to_submodule

if vs code isn't displaying all the submodules, or it failed to detect all, update your vscode settings and do this, right click submodule directory and click open file history, then refetch the commits in source control
https://github.com/Kentzo/git-archive-all
https://newbedev.com/git-archive-export-with-submodules-git-archive-all-recursive
https://devconnected.com/how-to-add-and-update-git-submodules/#Add_a_Git_Submodule
