# Build Instructions

The purpose of this repository is to bootstrap a Meteor app using the Mantra coding standards. Typical usage would be to fork the repository on GitHub and then clone it as a base for a new Meteor app.

```sh
git clone https://github.com/<your-github-user>/Mantra-Boilerplate.git
```

However, perhaps you want to build this from scratch, or at least know how it was done. Here is the process:

### Install Meteor

```sh
meteor create --release 1.3-modules-beta.4 Mantra-Boilerplate
cd Mantra-Boilerplate
rm -rf *
```

### Setup Mantra Environment

#### Initialize as a package for NPM

This creates a basic `packages.json` file. Look the file over, you may want to edit it. It might actually be better to automate this step as part of a `git clone` since it picks up some of its values from the application context.

```sh
npm init -f
```

#### Install & Configure Babel 6

Babel 6 does not come with any transformations enabled, so presets and plugins must be installed.

[Meteor 1.3 appears to have ES2015 support out of the box. The Mantra sample app, uses these, not sure if they are installed to support unit tests of if they are needed by Mantra in some way.]

```sh
npm install --save-dev babel-core
npm install --save-dev babel-preset-es2015
npm install --save-dev babel-preset-react
npm install --save-dev babel-preset-stage-2
npm install --save-dev babel-plugin-react-require
echo '{ "presets": ["es2015", "react", "stage-2"] }' > .babelrc
echo '{ "plugins": ["react-require"] }' >> .babelrc
```

https://babeljs.io/blog/2015/10/31/setting-up-babel-6/
https://babeljs.io/docs/setup/#meteor
https://github.com/vslinko/babel-plugin-react-require

#### Install React

### Configure Tools

editorconfig
eslint
