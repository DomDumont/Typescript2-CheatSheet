# Typescript2-CheatSheet
My personal cheat sheet for Typescript 2 

## Exports

- everything can be exported

~~~
    export interface StringValidator
    export const numberRegexp
    export class ZipCodeValidator 
~~~
- exports can be renamed

~~~
export { ZipCodeValidator as mainValidator };
~~~

- You can export something without importing it on your own

~~~
export {ZipCodeValidator as RegExpBasedZipCodeValidator} from "./ZipCodeValidator";
~~~

## Imports

- You can import a single export

~~~
import { ZipCodeValidator } from "./ZipCodeValidator";
~~~
- you can rename an import

~~~
import { ZipCodeValidator as ZCV } from "./ZipCodeValidator";
~~~

- you can import an entire module

~~~
import * as validator from "./ZipCodeValidator";
let myValidator = new validator.ZipCodeValidator();
~~~

- take care of default export. Import is different and act as a rename. Below import num is the same thing as import default as num.

~~~
export default "123";

import num from "./OneTwoThree";
console.log(num); // "123"

~~~


## Properties getter/setter

~~~
private _timeInterval: number;

get timeInterval(): number {
    return this._timeInterval;
}
 
set timeInterval(value: number) {
    if (value === undefined) throw 'Please supply time interval';
    this._timeInterval = value;
}

~~~

## Instantiate interface

Instead of

    this.model = Object(); // initialize this to an empty object

Do this :

    this._models = <IModels> {};


## Singleton

~~~

private static instance: MyClassName;

static getInstance() {
        if (!MyClassName.instance) {
            MyClassName.instance = new MyClassName();
            // ... any one time initialization goes here ...
        }
        return MyClassName.instance;
    }

~~~
