# grunt-backbone-typescript-accessor-generator

> Generates backbone models with typed subclasses for useing Backbone.js with TypeScript and its type system

## Getting Started
models are declared as YAML, such as

```YAML
Todo:
  content: string
  done: optional bool
  person: A

A:
  name: readonly string
```

and generates code in the form of

```typescript
class Model extends Backbone.Model {
  get_member() : member_type { return this.get('member'); }
  set_member(val : member_type) : void { this.set('member', val); }
  fromJSON(json) : {...}
}
```

members declared `optional` do not raise an exception if missing from a json loaded in fromJSON.
members declared `readonly` do not have set_member generated.


## Grunt plugin
This plugin requires Grunt `~0.4.1`

If you haven't used [Grunt](http://gruntjs.com/) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

```shell
npm install grunt-backbone-typescript-accessor-generator --save-dev
```

Once the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-backbone-typescript-accessor-generator');
```

## The "backbone_typescript_accessor_generator" task

### Overview
In your project's Gruntfile, add a section named `backbone_typescript_accessor_generator` to the data object passed into `grunt.initConfig()`.

```js
grunt.initConfig({
  backbone_typescript_accessor_generator: {
    options: {
      // Task-specific options go here.
    },
    your_target: {
      // Target-specific file lists and/or options go here.
    },
  },
})
```

### Options

#### options.separator
Type: `String`
Default value: `',  '`

A string value that is used to do something with whatever.

#### options.punctuation
Type: `String`
Default value: `'.'`

A string value that is used to do something else with whatever else.

### Usage Examples

#### Default Options
In this example, the default options are used to do something with whatever. So if the `testing` file has the content `Testing` and the `123` file had the content `1 2 3`, the generated result would be `Testing, 1 2 3.`

```js
grunt.initConfig({
  backbone_typescript_accessor_generator: {
    options: {},
    files: {
      'dest/default_options': ['src/testing', 'src/123'],
    },
  },
})
```

#### Custom Options
In this example, custom options are used to do something else with whatever else. So if the `testing` file has the content `Testing` and the `123` file had the content `1 2 3`, the generated result in this case would be `Testing: 1 2 3 !!!`

```js
grunt.initConfig({
  backbone_typescript_accessor_generator: {
    options: {
      separator: ': ',
      punctuation: ' !!!',
    },
    files: {
      'dest/default_options': ['src/testing', 'src/123'],
    },
  },
})
```

## Contributing
In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests for any new or changed functionality. Lint and test your code using [Grunt](http://gruntjs.com/).

## Release History
_(Nothing yet)_


---

Copyright 2013 Palantir Technologies

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.