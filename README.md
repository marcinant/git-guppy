# git-guppy [![NPM version](https://badge.fury.io/js/git-guppy.png)](http://badge.fury.io/js/git-guppy)

> Simple git-hook integration for your gulp workflows.

guppy streamlines and extends your git-hooks by integrating them with your 
[gulp](http://gulpjs.com) workflow. Git-hooks can now be managed through 
[npm](https://npmjs.org), allowing them to automatically be installed and 
updated. And because they integrate with gulp, it's easy to modify the workflow 
and even combine hooks with your other gulp tasks.

guppy leverages these powerful existing systems as its backbone, allowing guppy
(and therefore your git-hooks) to remain as simple and lightweight as possible
through interfaces you're already familiar with.

## Install
Install with [npm](npmjs.org):

```bash
npm i git-guppy --save-dev
```

## Usage

### Git integration

*Automatic!* 

The actual scripts that git will run to trigger guppy's hooks will be automatically
installed to your `.git/hooks/` directory. These are just a wrapper for invoking 
the gulp tasks that guppy registers.

You can install *guppy-hooks* via `npm` just like any other package. *More details
soon*

### gulp integration

guppy uses [lazypipe](https://github.com/OverZealous/lazypipe) to create pipelines
for git hooks. By requiring guppy into your `gulpfile.js`, you can easily integrate
gulp workflows as part of your git-hooks.

When git triggers a hook, guppy initializes the pipeline with the relevant files.

The `stream` method allows you to tap into pipelines.

```js
guppy.stream('pre-commit')
  .pipe(jshint)
  .pipe(jshint.reporter, stylish);
```

After setting up your pipelines, initialize guppy to register the guppy hooks as
gulp tasks.

```js
guppy.init(gulp);
```

Once registered, you can specify task dependencies for guppy hooks. If the hook 
is triggered, gulp will run its dependencies first.

> This interface will be improved in the future.

```js
guppy.tasks['pre-commit'].dep.push('foo');
```

## Writing guppy-hooks

*coming soon*

## Author

**Kevin Lanni**
 
+ [github/therealklanni](https://github.com/therealklanni)
+ [twitter/therealklanni](http://twitter.com/therealklanni) 

## License
Copyright (c) 2014 Kevin Lanni, contributors.  
Released under the MIT license

***

_This file was generated by [gulp-verb](https://github.com/assemble/gulp-verb) on August 10, 2014._
