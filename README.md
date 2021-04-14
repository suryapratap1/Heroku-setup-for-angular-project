### Heroku-setup-for-angular-project


Open package.json under your parent directory and insert following line to scriptstag:

"scripts": {
  ...
  "heroku-postbuild": "cd ANGULAR_APP_FOLDER && npm install"
}

heroku-postbuild is a tag used only in Heroku environment. It runs specified command after Heroku builds your application. (Explanation on Heroku Devcenter)
Run ng build after the package is installed

Move to your angular app folder and open package.json (NOTE: this is ANGULAR APP package.json. Different from package.json at previous step). Insert following line to scriptstag:

"scripts": {
  ...
  "postinstall": "ng build --aot -prod"
}

#### Command in postinstall is executed after npm package is installed. Now, it’s time to build your angular application. You can check ng cli options here.
Modify devDependencies and dependencies

Keep your angular app’s package.jsonopen. Insert following packages to dependencies.

Angular CLI is running on heroku environment in which Angular CLI is not installed by default. So we have to install Angular CLI at production environment.

"@angular/cli": "^1.0.1",
"@angular/compiler-cli": "^2.3.1",
"typescript": "^2.0.3"

Remove following libraries from devDependencies. Since they are installed at production, we do not need to keep them in dev environment.

"@angular/compiler-cli"
"typescript"

Specify what node and npm version you want to use

Open package.jsonunder your project folder. Insert following lines:

"engines": {
  "node": "7.8.0",
  "npm": "4.6.1"
}

Without this, npm complains UNMET DEPENDENCIES when you push to heroku.
