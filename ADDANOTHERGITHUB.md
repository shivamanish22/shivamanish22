# add another github account in system with existing one

# Generate ssh key and add it on github
1). generate sha256 key using below command 
   ```sh
   ssh-keygen -f /home/<user_name>/.ssh/drf_ed25519 -t ed25519 -C "<name/email>"
   ```
2). Read generated sha256 key and add it on github
 - After above command sha256 key will be generated on `.ssh` folder with file name `drf_ed25519` 
 - you also can change this file name during generation 
 - to read sha256 key use below command 
   ```sh
   cat ~/.ssh/<file_name accoring to above drf_ed25519.pub>
   ```
 - copy sha256 key and go to github and find setting section 
    - in Setting have a `SSH and GPG keys` menu
    - add here your copied sha256 key

3). Add generated sha256 in ssh using below command 
   ```sh
   ssh-add ~/.ssh/<generted file name as above drf_ed25519>
   ```

# Colne project and app all github command
1). Always remember to communicate to github use below before any git command
  ```sh
  GIT_SSH_COMMAND="ssh -i ~/.ssh/<file_name as baove drf_ed25519>"
  ```
2). Clone project 
 - copy `SSH` url from github
 - Go to desired directory where want to clone and run below command with above prefix
   ```sh
   GIT_SSH_COMMAND="ssh -i ~/.ssh/<file_name as baove drf_ed25519>" git clone <SSH url>
   ```

# git config setup
1). Go to cloned project directory and open in terminal
 - Set user name in git config using below comman 
  ```sh
  git config user.name "<git_usr_name>"
  ```
 - Set User email using below command 
  ```sh
  git config user.email "<Email>"
  ```
2). Now ready to use git command with above prefix as some given below (when communicate with github)
 ```sh
 GIT_SSH_COMMAND="ssh -i ~/.ssh/<file_name as baove drf_ed25519>" git push origin main
 ```
 ```sh
 GIT_SSH_COMMAND="ssh -i ~/.ssh/<file_name as baove drf_ed25519>" git pull origin main
 ```
# Set Alias for avoid always use prefix before git comman
1). Open bashrc using below command (using `vim` or `nano`)
 ```sh
 nano ~/.bashrc 
 ```
2). In bashrc add below alias and save exist 
 ```sh
 alias git2='GIT_SSH_COMMAND="ssh -i ~/.ssh/<file_name as baove drf_ed25519>" git'
 ```
3). Now Instead of using `"ssh -i ~/.ssh/<file_name as baove drf_ed25519>" git` can use `git2` as below 
 ```sh
git2 push origin main
 ```
 ```sh
 git2 pull origin main
 ```