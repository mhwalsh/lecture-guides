### Working with git in groups

#### Do it all locally
1. pull master (```$: git pull```)
2. create a feature branch (``` $: git checkout -b <branch name>```)
3. make feature commits on feature branch
4. update local copy of the master (check out master and ```$: git pull```)
5. merge feature branch into master (if on master still ```$:git merge <branch name>```
6. Resolve any conflicts and commit the merge. (Come get help if you need it. It can be tricky at first).
7. push master to the remote as soon as possible (```$: git push```)


#### Do it remotely i.e. on github
1. pull master (```$: git pull```)
2. create a feature branch (``` $: git checkout -b <branch name>```)
3. make feature commits on feature branch
4. push feature branch to remote (```git push -u origin <branch name>```)
5. open a PR or Pull Request on github
6. If there are no conflict, merge with the UI "merge" button
7. To get a copy of the updated master locally do a pull (```$: git pull```)
8. If there are conflicts you will have to follow the local steps above starting at step 4. 


