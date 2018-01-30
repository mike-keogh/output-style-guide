##Output CSS Style guide

Output studios adheres to SMACCS methodology, https://smacss.com/ .
We have made the following changes

* Module names are to be capitalised in their filename. This is to allow consistency with how modules are named in their react instances.
  * File names are also written with a preceding underscore a la _.\_Module.scss_
* The corresponding html file, and the js file if it exists, should be named the same as the module.

Class Names will be capitalised if it refers to a component or a module.
Words should be hyphenated as opposed to camelCase or PascalCase
e.g `<div class="Image-Component">`

CSS classes that live inside of the component or module are to be lowercase and the developer is to make use if the nested nature of SASS to allow the cascading nature of CSS to apply and also to reduce the amount of code written.
e.g the following code

```<div class="Image-Component">
    <div class="image" >
      <img src="rkg.svg" />
    </div>
   </div>
```

Would use the following SASS

```.Image-Component {
  > .image {
    //some declaration: value;
  }
}
```

This allows us to reuse generic classnames in different components or modules without conflicting CSS rules overriding each other.
