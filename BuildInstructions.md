# Build Instructions

The purpose of this repository is to bootstrap a Meteor app using the Mantra coding standards. Typical usage would be to fork the repository on GitHub and then clone it as a base for a new Meteor app.

```sh
git clone https://github.com/<your-github-user>/Mantra-Boilerplate.git
```

However, perhaps you want to build this from scratch, or at least know how it was done. Here is the process:

### Install Meteor

If you don't have Meteor installed yet, follow these steps:

```sh
curl https://install.meteor.com/ | sh
meteor create Mantra-Boilerplate
cd Mantra-Boilerplate
meteor update --release 1.3-modules-beta.4
rm -rf *
```

If you do have Meteor installed then it is a bit simpler:

```sh
meteor create --release 1.3-modules-beta.4 Mantra-Boilerplate
cd Mantra-Boilerplate
rm -rf *
```

### Setup Mantra Environment

#### Initialize as a package for NPM

If you haven't installed Node.js, do so:

This creates a basic `packages.json` file. Look the file over, you may want to edit it. It might actually be better to automate this step as part of a `git clone` since it picks up some of its values from the application context.

```sh
npm init -f
```

https://voice.kadira.io/getting-started-with-meteor-1-3-and-react-15e071e41cd1#.94ktpy6ni
https://medium.com/@borellvi/meteor-meets-npm-a5cc48d90abe#.844wsyn9s

#### Install & Configure Babel 6

The Meteor runtime gets its version of Babel though the ecmascript package that is part of Meteor. This version of Babel is used for running unit tests.

Babel 6 does not come with any transformations enabled, so presets and plugins must be installed.

[Meteor 1.3 appears to have ES2015 support out of the box. The Mantra sample app, uses these, not sure if they are installed to support unit tests of if they are needed by Mantra in some way.]

```sh
npm install --save-dev babel-core
npm install --save-dev babel-polyfill
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

```sh
npm install --save react
npm install --save react-dom
```

### Configure Tools

#### ESLint

If you don't have ESLint installed you can install it globally with:

```sh
npm install -g eslint
```

Then setup the config file with:

```sh
eslint --init
```

You may also want to install ESLint support for your text editor. For Atom you can:

```sh
apm install linter-eslint
``` 

https://atom.io/packages/linter-eslint
