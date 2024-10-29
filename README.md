# AngularHuskyBu2

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 18.2.7.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The application will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via a platform of your choice. To use this command, you need to first add a package that implements end-to-end testing capabilities.

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI Overview and Command Reference](https://angular.dev/tools/cli) page.

## check format + validate code

- Eslint: .....
-

## commit message format

    - follow: @commitlint/config-angular
    - Format: type(scope): description
    	- Type is one of: build, ci, docs, feat, fix, perf, refactor, revert, style, test
    	- Scope is required and can be any string, such as a component, function, or task/bug ID
    	- Description is a string
    - Example of a correct message: feat(screen): update code

## Branch name format

    - pattern: "^(feat|fix|hotfix|release)\\/ID-\\d+(\\/[-a-zA-Z0-9]+)?$"
    	- Format: type/ID-<number>(/description)
    		- Type is one of: feat|fix|hotfix|release
    		- ID-<number>: is required
    		- (/description): is optional,
