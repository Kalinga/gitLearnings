#### Client Key generation

`ssh-keygen`  # Don't give any passphrase

`cd ~/.ssh`
`sudo cp id_rsa.pub <server location>`


#### git user configurations
git config --global user.name "xxx yyy"
git config --global user.email "your_email@example.com"
git config --global core.editor emacs

#### Update the server repo with local contents
Create a directory on the client system `/home/rky4kor/dev/hello-world`

Create a git local repo

    `git init`
    `touch README.md helloworld.cpp helloworld.h`
    `git add .`
    `git remote add origin git@gitserver:/opt/git/hello-world.git`
    `git commit -m "Initial Commit for Hello World"`
    `git push origin master`

#### Create a clone
`git clone  git@gitserver:/opt/git/hello-world.git`

#### Remote details and working with them
See the remote locations:  `git remote -v`

Add a new remote:  `git remote add kpython https://github.com/Kalinga/pythonLearning.git`

To Fetch the details `git fetch kpython`

#### Other softwares
`sudo apt-get install gitk` 

`sudo apt-get install git gui`