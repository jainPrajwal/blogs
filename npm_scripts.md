# npm scripts
<!-- Use git push --set-upstream origin Assignment2<branchname> to push a branch to github -->
  In __package .json__ 
  
  "scss":"node-sass -o css/ css/" is added while after installing sass compiler by writing the command  
  ```
  npm install --save-dev node-sass
  ```
  --save-dev means its a developer dependancy.
  node-sass -o css/ css/ means that the output file that is the converted .css files (-o css/) lies in css folder and the source file also lies in the css folder.
  All the scss file will be taken by node-sass node module and it will convert it to css files
  Everytime a scss file is updated we need to compile it by running the command npm run scss
  Thus we have a module names onchange.This module watches for a change in the files in our project folder and if they are change sit will automatically complete the desired task.
  So for eg we have scss file and it has just been updated ..So it will AUTOMATICALLY Recomplie it.
  We already have such script in our project folder.We just need to add WATCH over files.
  There is another module which is used for same purpose.
  *Parallel shell* is another node module which allows to run multiple shells simultaneously and thus the name PAraallel shell.
  Thus multiple npm scripts could be run
  Command : 
  ```
  npm install --save-dev onchange parallelshell
  ```
  "watch:scss":"onchange \"css/*.scss\" -- npm run scss" 
  means keep a eatch on all scss files in css folder If any of them then trigger the following script
  npm run scss
  Yes this one..Because this npm script is going to run the scss code.
 "watch-all":"parallelshell \"npm run watch:scss\" \"npm run lite\" "
  Allows Running 2 scripts simultaneously
  Now after doing npm start will start the 2 scripts simultaneously.
  
  >NPM SCRIPTS PART 2

  *Step 1 npm install --save-dev rimraf*
  It is a modue which helps clean the folder.
  Our folders name in which we are going to put all the files comboned,together is dist(meaning 
  distribution folder)

  IN __PACKAGE.JSON__

  "clean":"rimraf dist"
  
  *Step 2 Copying files.*
```
  npm -g install copyfiles
  ```
  helps copy files from one folder to another.

  IN __PACKAGE.JSON__

  "copyfiles -f node_modules/font-awesome/fonts/* dist/fonts"
  NOW WE COME IN COMMAND PROPMT
  ```
  npm run copyfonts
  ```
  A folder named dist is created witha subfolder fonts which has all the font files.
  npm run clean
  Deleted the dist folder

  *Step 4 Install a node modulenamed imagemin-cli * 
  
  which is a cli for imagemin module.
  The imagemin module takes a set of image files and compress them as much as possible but still be rendered properly.
  This way we reduce the data required by the browser to download.
  ADD DIST TO GITIGNORE

  IN __PACKAGE.JSON__

  "imagemin":"imagemin img/* -o dist/img"
  img/* => source -o=>output dist/img => destination
  It means take all files from img folder minimize it and paste it in dist/img folder.

  *Step 5 Preparing the dist folder *

 ** ON COMMAND PROPMT**
 ```
  npm install --save-dev usemin-cli cssmin uglifyjs htmlmin
  
  ```
  usemin-cli concatenates all js files to one single js file all css code to 1file and all html code to 1 file.
  But internally it requires uglifyjs and htmlmin to work out.
  But uglifyjs was deprecated.So I installed uglify-js which is a modifies version.
  IN INDEX.HTML,CONTACTUS.HTML AND ABOUTUS.HTML
  Before \<link> and \<script> tags we write \<!-- build:css dist/main.css --> \<link> tags \<!-- endbuild --> \<!-- build:js dist/main.js --> \<script> tags \<!-- endbuild --> 

  IN __PACKAGE.JSON__

  "usemin":"usemin contactus.html -d dist --htmlmin -o dist/contactus.html && aboutus.html -d dist --htmlmin -o  dist/aboutus.html && index.html -d dist --htmlmin -o dist/index.html"
  "build":"npm run clean && npm run copyfonts && npm run imagemin && npm run usemin"
  
So only using 1 command everything will take place on its own and that one command is
```
  npm run build
```
  And thats all about NPM SCRIPTS PART 2
  
  
