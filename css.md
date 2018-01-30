## Output CSS Style guide

Output studios adheres to SMACCS methodology, https://smacss.com/.

We have made the following changes, which may differ from those outlined in the SMACCS docs.

* Module names are to be capitalised in their filename. This is to allow consistency with how modules are named in their react instances.
  * File names are also written with a preceding underscore a la _\_Module.scss_
* The corresponding html file, and the js file if it exists, should be named the same as the module.

Class Names will be capitalised if it refers to a component or a module.
Words should be hyphenated as opposed to camelCase or PascalCase
e.g `<div class="Image-Component">`

CSS classes that live inside of the component or module are to be lowercase and the developer is to make use if the nested nature of SASS to allow the cascading nature of CSS to apply and also to reduce the amount of code written.
e.g the following code

```
    <div class="Image-Component">
      <div class="image" >
        <img src="rkg.svg" />
      </div>
    </div>
```

Would use the following SASS

```
    .Image-Component {
      > .image {
        //some declaration: value;
      }
    }
```

This allows us to reuse generic classnames in different components or modules without conflicting CSS rules overriding each other.

We do not create utility classes, instead create a mixin for that utility that accepts a multiplier so that any value can be input.

```
    $unit: 8px;

    @mixin padding($where, $multiplier){
      if($where == "*") {
        padding: $multiplier * $unit;
      } else if ($where == "t") {
        padding-top: $multiplier * $unit
      } etc...  
    }
```

The `$unit` will always be defined in the designs or in the repo by the designer. There may be a `$unit` for small and medium breakpoints.  
Those breakpoints will be their own mixins preceded by the size 's-' or
'm-'.

```
    @mixin s-padding($where, $multiplier) {
      ...
    }
```

Folder structure for scss is as follows

```
Root
  scss  
    ui
      _Module.scss
    layout
      _grid.scss
    mixins
      _padding.scss
    style.scss  
```

style.scss imports all the scss files and is compiled to css through a node-sass script in the package.json
