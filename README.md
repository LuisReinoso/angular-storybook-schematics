# angular-storybook-schematics

Angular schematics which automatically adds new components created with `ng generate component` to the [Storybook](https://storybook.js.org/).

A modified and updated version of [kimamula's version](https://github.com/kimamula/ngx-schematics-for-storybook)

All credits goes to [kimamula](https://github.com/kimamula)

[![NPM version][npm-image]][npm-url]

## Configure

To use @schematics/angular-storybook as the default collection in your Angular CLI project, add it to your angular.json:

```sh
ng config cli.defaultCollection  @schematics/angular-storybook
```

The @schematics/angular-storybook extend the default @schematics/angular collection. If you want to set defaults for schematics such as generating components with scss file, you must change the schematics package name from @schematics/angular to @schematics/angular-storybook in angular.json:

```json
"schematics": {
  " @schematics/angular-storybook:component": {
    "styleext": "scss"
  }
}
```

## Usage

```sh
# if you use  @schematics/angular-storybook as the default collection
$ ng generate component bar
CREATE src/app/bar/bar.component.scss (0 bytes)
CREATE src/app/bar/bar.component.html (22 bytes)
CREATE src/app/bar/bar.component.spec.ts (607 bytes)
CREATE src/app/bar/bar.component.ts (258 bytes)
CREATE src/app/bar/bar.stories.ts (376 bytes)

# if you do not use  @schematics/angular-storybook as the default collection
$ ng generate @schematics/angular-storybook:component bar
```

In addition to the ordinary [`ng generate component`](https://github.com/angular/angular-cli/wiki/generate-component), the above command generates a `.stories.ts` file for the created component.

All the options for the ordinary `ng generate component` is available, as well as:

- `--noStory`
  - Skips creating a story for the created component
- `--useTemplate`
  - Uses a template string (e.g. `` template: `<app-foo></app-foo>` ``) instead of a component class (e.g. `component: FooComponent`) in the storybook
- `--tagAsLabel`
  - Uses a tag string (e.g. `<app-foo>`) as a label instead of a component class name (e.g. `FooComponent`) in the storybook
- `--replacePath`
  - Replaces the path of the story with a stringified array of `{ from: string, to: string }` which is to be used as `path.replace(new RegExp(from), to)`
