!!! info ""

    ### Basic commands

    ```bash
    #initiate git
    git init
    
    #pull your repo branch, master, main, etc..
    git pull <github repo link> <branch>
    
    #get current status for all changes
    git status

    #config those before commiting
    git config --global user.email no-reply@github.com
    git config --global user.name potatoehead

    #commit all changes before pushing and add a comment
    git commit -a -m "comment"
    
    #push all updates to your branch, master, main, etc..
    git push origin <branch>
    
    #git add a new file to repo, you will need to cmmint and push afterwards
    git add "XX"
    
    #remove a file from repo, you will need to cmmint and push afterwards
    git rem "XX"

    #configuring the remote repo, this way you can call origin instead of the full repo link
    git remote add origin https://github.com/584F525F/584F525F.github.io/

    #print the current configured remote repo
    git remote -v

    #clear cache, re-add everything and commit then push
    git rm -r --cached .
    git add .
    git commit -am 'git cache cleared'
    git push

    #revert back last commit
    git reset HEAD^ --hard
    
    ```
