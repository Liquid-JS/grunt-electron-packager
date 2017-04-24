# grunt-electron-packager 

Grunt task to create packages [Electron](http://electron.atom.io) using  [`electron-packager`](https://github.com/maxogden/electron-packager)
This is mostly intended for those that have an existing grunt setup and want to integrate Electron app packaging.
It allows you to create custom options.
This uses the installed version of electron-packager.

## Install

```
$ npm install grunt-electron-packager --save-dev
```

## Usage

```js
const os = require('os');
require('load-grunt-tasks')(grunt); // npm install --save-dev load-grunt-tasks

  grunt.initConfig({
    'electron-packager': {
      build: {
        options:{
          platform        : os.platform(),
          arch            : os.arch(),
          dir             : './app',
          out             : './build',
          icon            : './app/recursos/icon',
          name            : 'nameBuild',
          ignore          : 'bower.json',
          electronVersion : '1.6.1', // set version of electron
          asar      : true,
          overwrite : true
        }
      },
      buildCustom: {
        options: function (name,platform,arch) {
          return {
            platform ,
            arch,
            dir       : './app',
            out       : './build',
            icon      : './app/recursos/icon',
            name,
            ignore    : 'bower.json',
            asar      : true,
            overwrite : true
          }
        }
      }
    }
  });
  grunt.loadNpmTasks('grunt-electron-packager');
  grunt.registerTask('default', [
    'electron-packager:build',
    'electron-packager:buildCustom:buildCustomName:win32:all'
  ]);
```

## devDependencies

These dependencies must be installed.

```
$ npm install grunt --save-dev
$ npm install load-grunt-tasks --save-dev
$ npm install electron --save-dev
$ npm install electron-packager --save-dev
```

## Options

See the `electron-packager` [options](https://github.com/maxogden/electron-packager#usage).

## License

MIT © [Marani Matias Ezequiel](maranimatias@gmail.com)
