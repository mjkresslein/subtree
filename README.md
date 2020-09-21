# subtree
### **Pull the repo of subtree-d repos**
````
git clone git@github.com:mjkresslein/subtree.git
````
### **Update a specific remote of one of the subtrees**
````
git pull  -s subtree --no-commit <remotename> <branch>
````
example:
````
git pull -s subtree --no-commit screen master
````
### **Use other git commands normally for updating the remote branch of the main repo**
````
git commit -m <message>
````
````
git push origin
````
### **Other Useful commands**
#### **listing remotes**
    git remote -v
#### **Adding a new repo as a subtree**
````
git remote add -f <remotename> <repo url/ssh>
````
````
git merge -s ours --no-commit --allow-unrelated-histories <remotename>/<branch>
```` 
````
git read-tree --prefix=<foldername>/ -u <remotename>/<branch>
````
````
git commit -m "subtree merged in <remotename>"
````
In the above <remotename> refers to a name you give the remote repository you're adding as a subtree to this one. Specify which <branch> of the remote repository to sync in this repository. Also name the folder using <foldername> specify where in the folder structure you want the remote repository to sync to.

example:
````
git remote add -f mydocker git@github.com:mjkresslein/MyBaseDocker.git
````
````
    Updating mydocker
     Enter passphrase for key '/Users/mkresslein/.ssh/id_rsa':
     warning: no common commits
     remote: Enumerating objects: 3, done.
     remote: Counting objects: 100% (3/3), done.
     remote: Total 3 (delta 0), reused 3 (delta 0), pack-reused 0
     Unpacking objects: 100% (3/3), done.
     From github.com:mjkresslein/MyBaseDocker
      * [new branch]      master     -> mydocker/master`
````
````
git merge -s ours --no-commit --allow-unrelated-histories mydocker/master
````
````
    Automatic merge went well; stopped before committing as requested
````
````
git read-tree --prefix=mydocker/ -u mydocker/master
git commit -m "subtree merged in mydocker"
````
````
    [master 1ad2474] subtree merged in mydocker
````
