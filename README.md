# Socios Homebrew Formula 

### Homebrew Formula

The Homebrew tap/formula process is the combination of two GitHub repositories. 

 The First GitHub repo contains the functionality package (socios).

The second GitHub repo contains the homebrew formula with the ruby file (homebrew-socios).

### Step1: Creating Tag and Releases

<img src="https://i.ibb.co/hFjYH8J/image-0.png" width="600px">

We need to clone the First repository(socios) in a specific path. Using the below Git clone command

```bash
$ git clone https://github.com/SociOS-Linux/socios-setup.git
```

<img src="https://i.ibb.co/Jr1jtVk/image-1.png" width="600px">

Switch into that cloned repository folder(socios-setup) then we need to place the updated script packages in that folder(socios).

By using the git commands. We need to push the updated files to the First repository(socios-setup)

```bash
$ git status && git branch

$ git add .
```

<img src="https://i.ibb.co/FVV6dCb/image-2.png" width="600px">

```bash
$ git commit -am "socios-setup: Updated to the latest version <MAJOR.MINOR.PATCH>"
```

For every commit, we need to update the commit message.

<img src="https://i.ibb.co/3Y4RnFh/image-3.png" width="600px">

```
	$ git push -u origin main //  git push -u origin develop

	$ git tag v<MAJOR.MINOR.PATCH>

	$ git push origin v<MAJOR.MINOR.PATCH>
```

<img src="https://i.ibb.co/GP8z7yv/image-4.png" width="600px">

Once we push the tag into the First repository(socios-setup). Refresh the Repository once.

Then we can able to view the changes in the Releases option.

<img src="https://i.ibb.co/27Wv5ww/image-5.png" width="600px">

Now, Click on the latest update tag 

We can able to view the old releases here. Now we need to click on “Release”

<img src="https://i.ibb.co/B2qjR5b/image-6.png" width="600px">

Then we can able to access the “Tag” section. Click on Tag 

Here we can able to see the Updated build file with (zip, Tar.gz) formate

<img src="https://i.ibb.co/TPVDp0X/image-7.png" width="600px">

Now select the Release tab. Click on the Draft a new release button

<img src="https://i.ibb.co/VxQ5wW8/image-8.png" width="600px">

Next, we need to choose the “Tag” with (Latest version) and the target branch

<img src="https://i.ibb.co/TRZXp3T/image-9.png" width="600px">

Update the Release title with “Version Name” with Description 

<img src="https://i.ibb.co/yV3sLwV/image-10.png" width="600px">

Now un-check the pre-release and click on “Publish release”

<img src="https://i.ibb.co/kcD0FdH/image-11.png" width="600px">

Finally, We can able the see the latest release in the socios-setup repository

<img src="https://i.ibb.co/VtTY8D0/image-12.png" width="600px">

### Step2: Creating Homebrew Tap/Formula

Already we have a package zip and tar.gz file in our First repository(socios-setup)

Right-click the Filename(Source code (tar.gz)) - Now Copy the latest version of the tar.gz package file URL

<img src="https://i.ibb.co/X7Xq1h6/image-13.png" width="600px">

We can able to find the socios-setup package file based on it's tags <MAJOR.MINOR.PATCH> here:

https://github.com/SociOS-Linux/socios-setup/archive/refs/tags/v<MAJOR.MINOR.PATCH>.tar.gz

we need to copy the socios-setup package compressed tar.gz file link from the GitHub release.

Create the ruby file formula by running the below command in the terminal.

Syntax: brew create <package URL>

```bash
$ brew create https://github.com/SociOS-Linux/socios-setup/archive/refs/tags/v<MAJOR.MINOR.PATCH>tar.gz
```

Notes: If there is an existing version configured in mac Machine we need to untap the previous version.

```bash
$ brew uninstall socios-setup
$ brew untap  SociOS-Linux/socios-setup
```

<img src="https://i.ibb.co/6BNQ9Q7/image-14.png" width="600px">

The above command will generate the default formula file in a ruby format for our socios-setup packages

Once created homebrew editor will open - we need to exit the editor terminal (:wq)

Now the Updated formula is created in the below file location.

         /usr/local/Homebrew/Library/Taps/homebrew/homebrew-core/Formula/socios-setup.rb

#### Homebrew Directory list

          Homebrew package uses the below folder's path to configuration.

**Formula –** The package definition uses the path /usr/local/Homebrew/Library/Taps/homebrew/homebrew-core/Formula/socios.rb

**Keg -** The installation prefix of a Formula uses the path /usr/local/Cellar/socios-setup/v1.3.6

**Cellar -** All Kegs are installed in path /usr/local/Cellar

**Tap -** A Git repository of Formulae and/or commands uses the path /usr/local/Homebrew/Library/Taps/homebrew/homebrew-core

### Step3: Creating  Second Repository for Homebrew Formula/ Socios

Create a second repository(sociosbrew-tap) for the ruby formula. 

<img src="https://i.ibb.co/4YrsB1z/image-15.png" width="600px">

Then clone that repository in our local System using the below git clone command.

```bash
$ git clone https://github.com/SociOS-Linux/sociosbrew-tap.git
```

<img src="https://i.ibb.co/KXsSF2V/image-16.png" width="600px">

After we clone the repository - Switch to the sociosbrew-tap folder.

<img src="https://i.ibb.co/YfFwkbV/image-17.png" width="600px">

Now we need to update the socios-setup.rb file with some functions.

Copy the default socios-setup.rb file with cloned repository folder (sociosbrew-tap)

```bash
$ cp /usr/local/Homebrew/Library/Taps/homebrew/homebrew-core/Formula/socios-setup.rb .
```

Using nano command. We need to update the socios-setup.rb file using the below Line.

<img src="https://i.ibb.co/XDcDvLq/image-18.png" width="600px">
   
```   
Syntax:
     def install
              bin.install "socios-setup"
              prefix.install Dir["lib"]
     end
end
``` 
 
Then we need to commit the updated file to Second Repository (sociosbrew-tap)
 
Check the branch and status using the git commands.

```bash 
$ git status && git branch
```

<img src="https://i.ibb.co/xJxHXC6/image-19.png" width="600px">
 
Check the changes in the file using the below terminal
 
```
$ git diff 
``` 

It will show changes between commits, commit, and the working tree
 
<img src="https://i.ibb.co/9Yccs87/image-20.png" width="600px">
 
```bash
$ git add .
 
$ git commit -m “Socios: Updated version <tags>”
 
$ git push -u origin main / git push -u origin develop
``` 

<img src="https://i.ibb.co/FVd9059/image-21.png" width="600px">
 
Once committed the file we need to refresh the GitHub page 

<img src="https://i.ibb.co/mGfyQG9/image-22.png" width="600px">

Once completed the above procedures, we can able to download and use our socios-setup packages by using the below commands.

Then we can check the functions of Socios using the below commands.
 
``` 
$ brew tap SociOS-Linux/socios-setup 
```

<img src="https://i.ibb.co/rMvsfxV/image-1.png" width="600px">
	
```bash
         $ brew install socios-setup

         $ socios-setup --version
```

<img src="https://i.ibb.co/yYT79YC/image-2.png" width="600px">

Steps to uninstall socios-setup
```
$ brew uninstall socios-setup
```
