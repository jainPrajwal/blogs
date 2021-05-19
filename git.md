# git:simple explanation for a beginner.

## An Overview
What it basically does is saves different versions of your file.

Like when you write a program,you change the file number of times.
Git helps us to save(in better words 'track') those changes.Thats it.

Imagine you and your team is working on same file on a college project which is index.html
<!-- Now your project head tells you guys to submit your project within 3 days. -->
So..You guys are all set to 'type' the already coded file that you have with you.
You both log in with a common id but on different machines and start editing the same file simultaneosly.
You would be like "Hey!From Where did this rascal piece of code is coming from..I never wrote it!!Let me delete this"
And your friend be like "Why this shitty piece of code is getting deleted always..Coding is such a frustrating?Why did they even invent this???"

And the Uparwala be watching and thinking "In naadan balkon ko git nai pata!!"

Okay..Coming back!
What do you think will happen?
Yes!file is changed from both ends and gets corrupt.

And this is only you and your friend!Imagine tech giants like flipkart where hundreds of developers are working together!How would they manage all these changes to the same file?

<b>And thats where Git comes into picture!</b>

Now lets see some terms and terminologies.
>What is a repository?

Just a fancy name for folder.

There are some commands you need toknow if you are using the CLI version.
>There is something known as __add__.

This is how the command is
```
git add <file_name>
```
What this command does is adds all your changes to an intermediate agent.
Yes they arent yet given in right hands.
By running this command you only give that file which you have just changed to that middle man.
That middle man in fancy terms is known as stagging area.
Now how to move it safely into right hands and save changes.

For that lets meet this guy.

>There is something known as <b>commit</b>

Remember I told you that git saves different versions of your file.
How?Well _commit_ is the answer for that.
For now , see _commit_ as _save changes_.
Replace _commit_ word with _save changes_.
You can also imagine it like a game checkpoint.
You are on a mission in GTA and you know there are checkpoints..So if you are killed somehow,you would not need to start all the way from beginning.Your latest checkpoint is where you start from.

The command runs like this:
<!-- By the way git uses CLI as well as GUI. -->
<!-- CLI is doing something with the help of commands. -->
```
git commit -m "Initial commit"
```
-m stands for message.
You change the file every now and then.
You run and you see Oh! ';' is missing,
Again you run Oh!I missed a brace!!
Sometimes you add ,sometimes you delete.
So only saving changes is useless until you get to know what changes have you made!
And hence you have a message associated with every commit.
Isnt that simple?
>Every commit has an unique id associated with it.

>Push and Pull.

First lets answer this.

Where to push? To your Github Account

From where to pull? From your Github Account.

What to pull?Repositories

What to push?Folder containing the files you are working on(index.html)

Now man?What is this Github now?



Imagine Github is Google Photos.
<!-- index.html as index.jpg in which you are looking damn hot.But say,the background needs to be changed.index.jpg could be enhanced. -->
Right now,the image/file  is in your phone(any local machine).

You __PUSH__(_Upload_) it to __GITHUB__(_google photos_).
And the command is:
```
git push  
```
But you need to go through the <a href="https://docs.github.com/en/free-pro-team@latest/github/getting-started-with-github">initial setup</a> before running the command.

And there are some files that you want to __PULL__(_download_) that you had earlier uploaded to your account and are not there in your local machine right now.

So you __PULL__(_download_) the desired repo from your github account by 
```
git pull
```
<!-- (I would tell the command at the end.First lets understand the concept.) -->
<!-- You get a link of your photo.You send it to your friend. 
He uses that link.
Now he obviously has to download that into his phone and then only can he enhance the photo.
So he __FORKS__.
Here comes a little twist.
With github we cant directly download someone else's repo.
First we have to fork it.It simply means create duplicate copy of that repo in your github account.
After that duplicate copy is created,then you can clone it (__DOWNLOAD__) it to your local machine.
I hope it is clear.
>Difference between clone and pull

>Cloning is <b style="color:cyan;">downloading the forked repo</b> from your github account to your local machine.(downloading)

>Pulling means <b style="color:cyan;">downloading your own repo</b> from your github account after being changed by some one.(may be yousrslef!)
Now your fellow friend enhances your photo..Applies some beautiful filters and __PUSH__(uploads) it to his repo.
But he needs to send you the enhaced image file.Isnt it?
So what he does is creates a new Pull Request saying Hey!Prajwal I have enhanced your photo.Why dont you see it?And merge those changes. -->

If you have read this till here..Do give it a like and tell me in comments if you really understood or not!
Feel free to correct me if I have went wrong somewhere!