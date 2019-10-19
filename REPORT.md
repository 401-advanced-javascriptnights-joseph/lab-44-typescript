# JS Framework Comparative Analysis

## Typescript + HTML

### Research Conducted By: Joseph Hangarter, Aileen Murphy, Brad Smialek

### Overall Score and Comments
#### Score (Out of 10): 7
#### General Comments
* More stricter form of Javascript
* 
Describe the stack (front-end only? full stack?), database, efficiency, etc. Describe the general usability and learnability

#### Pros
* Works like Javascript
* Item 2

#### Cons
* Item 1
* Item 2

### Ratings and Reviews
#### Documentation
* NPM users - `npm install -g typescript`
* Compiling your code - utilize a `.ts` extension and run `tsc module.ts`; The result will be a file `module.js` which contains the same JavaScript that you fed in
```
class Student {
    fullName: string;
    constructor(public firstName: string, public middleInitial: string, public lastName: string) {
        this.fullName = firstName + " " + middleInitial + " " + lastName;
    }
}

interface Person {
    firstName: string;
    lastName: string;
}

function greeter(person: Person) {
    return "Hello, " + person.firstName + " " + person.lastName;
}

let user = new Student("Jane", "M.", "User");

document.body.textContent = greeter(user);
```
* React & Webpack
  * Project Structure
```
proj/
├─ dist/
└─ src/
   └─ components/
```

* TypeScript files will start out in your src folder, run through the TypeScript compiler, then webpack, and end up in a main.js file in dist. Any components that we write will go in the src/components folder.

* Initialize Project - `npm init -y`
* Install Dependencies(shown below)
* Add a TypeScript configuration file
  * You’ll want to bring your TypeScript files together - both the code you’ll be writing as well as any necessary declaration files.

  * To do this, you’ll need to create a tsconfig.json which contains a list of your input files as well as all your compilation settings. Simply create a new file in your project root named tsconfig.json and fill it with the following contents:
```
{
    "compilerOptions": {
        "outDir": "./dist/",
        "sourceMap": true,
        "noImplicitAny": true,
        "module": "commonjs",
        "target": "es6",
        "jsx": "react"
    }
}
```

* A module with `.tsx` extension for react and typescript
* Create an index.tsx in src with the following source:
```import * as React from "react";
import * as ReactDOM from "react-dom";

import { Hello } from "./components/Hello";

ReactDOM.render(
    <Hello compiler="TypeScript" framework="React" />,
    document.getElementById("example")
);
```
* 
* Create a webpack configuration file:
``` 
module.exports = {
    mode: "production",

    // Enable sourcemaps for debugging webpack's output.
    devtool: "source-map",

    resolve: {
        // Add '.ts' and '.tsx' as resolvable extensions.
        extensions: [".ts", ".tsx"]
    },

    module: {
        rules: [
            {
                test: /\.ts(x?)$/,
                exclude: /node_modules/,
                use: [
                    {
                        loader: "ts-loader"
                    }
                ]
            },
            // All output '.js' files will have any sourcemaps re-processed by 'source-map-loader'.
            {
                enforce: "pre",
                test: /\.js$/,
                loader: "source-map-loader"
            }
        ]
    },

    // When importing a module whose path matches one of the following, just
    // assume a corresponding global variable exists and use that instead.
    // This is important because it allows us to avoid bundling all of our
    // dependencies, which allows browsers to cache those libraries between builds.
    externals: {
        "react": "React",
        "react-dom": "ReactDOM"
    }
};
```

* Putting it all together - npx webpack
Thoughts go here

#### Systems Requirements
* Dependencies: 
  * `npm install --save-dev webpack webpack-cli` - bundles your code and optionally all of its dependencies into a single .js file.
  * `npm install --save react react-dom` - 
  * `npm install --save-dev @types/react @types/react-dom` - That @types/ prefix means that we also want to get the declaration files for React and React-DOM. Usually when you import a path like "react", it will look inside of the react package itself; however, not all packages include declaration files, so TypeScript also looks in the @types/react package as well.
  * `npm install --save-dev typescript ts-loader source-map-loader` - Both of these dependencies will let TypeScript and webpack play well together. ts-loader helps Webpack compile your TypeScript code using the TypeScript’s standard configuration file named tsconfig.json. source-map-loader uses any sourcemap outputs from TypeScript to inform webpack when generating its own sourcemaps. This will allow you to debug your final output file as if you were debugging your original TypeScript source code.
Above and beyond 'node' and 'linux', what dependencies or core requirements exist for this framework?  Can it play at AWS/Heroku?  Does it require a certain database?

#### Ramp-Up Projections
How long would/should it take a team of mid-junior developers to become productive?

#### Community Support and Adoption levels
How popular is this framework? What big companies are running on it? How is it "seen" in the general JS community?  Is there an active community of developers supporting and growing it?


### Links and Resources
* [framework](https://www.typescriptlang.org/)
* [docs](https://www.typescriptlang.org/docs/home.html)
* [examples/tutorials](http://xyz.com)

### Code Demos
* [live/running application](http://xyz.com)
* [code repository](https://github.com/401-advanced-javascriptnights-joseph/lab-44-typescript)

### Operating Instructions
If someone were to download your repo (above), what steps do they need to take to run the application
* `npm start`
* Endpoint: `/foo/bar/`
  * Returns a JSON object with abc in it.
* Endpoint: `/bing/zing/`
  * Returns a JSON object with xyz in it.
