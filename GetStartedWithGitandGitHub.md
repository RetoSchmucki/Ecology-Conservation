#### 1. Get Started with Git on your local computer

Once you have installed Git on your computer, either from the Y:drive at Y:/Approved Software/Git within CEH or from the [Git website](https://git-scm.com/), you will need to set-up your Git user.name and user.email. This is only to be done once when you start on a new machine or a new user account.

The most transparent way to do this is to use the command-line (e.g. ```Git Bash.exe```)

  ###### 1.1. Git configuration step:
  These info come from the [GitHub website](https://git-scm.com/book/en/v2/Customizing-Git-Git-Configuration)

  ```sh
   # In your console, configure your username and email, type

      git config --global user.name "John Doe"

      git config --global user.email johndoe@example.com
 ```
 - --global set the configuration for your user account on that computer
 - --system set the configuration for all user on account on that computer
 - --local  set the configuration for a specific project directory (repository)


  ###### 1.2. Initialize a project folder that you want Git to version control

  Let's do this from your console again, starting with a new project folder

  ```sh
  # Change to the directory you want to set your project (e.g. Documents)
  cd Documents

  git init "projectname"

  # This create a new folder named "projectname" (or whatever you name it) in your ~/User/You/Documents folder.
  # Navigate to the newly created folder and have a look what's in there with the ls command
  cd projectname
  ls
  ```
<a name="a1.3"></a>
###### 1.3 Populate your new Git project

Using your favourite text editor, create a file named README.md
with the something like ```## This is the projectname README file```.
use the extension .md to notify that it is a [Markdown](https://guides.github.com/features/mastering-markdown/) file.

###### 1.4 Add the newly create file to the version control system, **stage** it. From your console, open on in your ```projectname``` folder.

```sh
 git add .

 # the dot(.) stands for everything that has changed in this folder since last time you committed something

 # now add a little commit message to this snapshot
 git commit -m 'a short but informative message'
```

###### :smiley: Believe it or not but you just set a initial version of your project with Git. Well Done!


#### 2. Get Started with GitHub and enable your computer to send and retrieve version from a GitHub repository.

 Because interaction between your local Git and GitHub use the internet, the system will use encryption key to enable secure transaction between the server and your computer. Here we will use and SSH key to work with GitHub.
 This SSH key is specific to your computer and will need the corresponding public counterpart on the server to enable encryption and de-encryption.

 ###### 2.1 Generate an SSH key on your machine, using the command line ```Git Bash.exe```

 ```sh
 # check for existing ssh keys on your computer

 ls -al ~/.ssh

 # if already have and SSH key, you will get a list of them
 # look for the one named id_rsa and id_rsa.pub
 # if none you will get a error message

 # generate a rsa key using 4096 bit encryption and attached to your email
 ssh-keygen -t rsa -b 4096 -C "your_email@example.com"

 # test your ssh key
 eval "$(ssh-agent -s)"

 # you should get something like (the number varies)
  > Agent pid 7608

  ```
 ###### 2.2 Add your rsa SSH key to your GitHub account

To use the SSH key you created, you need to provide GitHub with the public counterpart of the key, here ```id_rsa.pub```.

From your console again ```Git Bash.exe```

```sh
 # copy and add your key (the .pub element) to your GitHub (or other) service
 clip < ~/.ssh/id_rsa.pub
```
 Now you have a copy of the id_rsa.pub SSH key attached to your clipboard and your are ready to add it to your GitHub account.


###### - Now go to your GitHub account and login https://github.com/
- move to settings https://github.com/settings/profile
- look for ```SSH and GPC key``` from the left-hand menu
- clic on the green button ```New SSH key```
- give it a name that is relevant to your machine (every key is specific to a computer)
- paste the id_rsa.pub key that is in your clipboard. This should result in a sequence of alpha-numerics ended with your email.

######Note: If you encounter problems, have a look at the [GitHub help page](https://help.github.com/articles/connecting-to-github-with-ssh/)


#### 3. Interact with Git and GitHub

To interact with GitHub, you first need to create a repository on your GitHub server.

###### 3.1 Create on GitHub and Clone on your local machine

- Create a new repository with the **+** sign found on top right, next to your profile picture.
- Once created, go to your repository (e.g. https://github.com/YourGitHubUserName/YourRepository)
- clic on the green button ```Clone or Download```
- make sure it says ***Clone with SSH*** and not ***HTTPS***, if the later clic on ```use SSH```.
- copy the url in that appears ```git@github.com:YourGitHubUserName/YourRepository.git```
- open your console ```Git Bash.exe```

```sh
# move to the directory you want to locate your project
cd Documents

# Clone your newly created repository
git clone git@github.com:YourGitHubUserName/YourRepository.git

# This will create a new project folder named YourRepository that is
# set-up with Git and contains a .git folder (possibly hidden)
```

###### 3.2 Add something and push your change to GitHub

Now you actually need to do some real work and add some content to your newly created project. Got to [1.3](#a1.3) above

Once you have added and committed your change(s), you need to push them to the GitHub repository

```sh
cd Documents/YourRepository

git push
```
Note that you might need to ```git pull``` before pushing to make sure that the head of your branch is not behind the one on GitHub.

Done! Happy Git :smiley:
