# sassy-css-landing-page
Responsive landing page demonstrating the use of SCSS!

# Crash course covering these topics 

  CSS preprocessors are a scripting lanugage, that extend regular CSS. 

  Advantages
  - Easier to maintain
  - Saves time and keeps code more organized.
  - Lot of features!

 ### Sass Variables
   Although we can use variables in regular CSS , we can also choose to use SASS. Because the generic CSS variables might be only supported in certain browsers, wheras SASS ensures this is supported everywhere ( since it translates it to regualr CSS)

 #### Sass Maps
 ```javascript
 $colors : (
    primary: #333,
    secondary: #f4f4f4f4
  );
 ```

 Helps us organizing the code , using a JS object sorta notation.
 #### Nesting
  Right now Nesting is not supported in CSS. 
  SASS gives you this!
  ```javascript
  body {
    height: 100%;
    font-family: Arial, Helvetica, sans-serif;
    margin: 0;
    padding:0;
    box-sizing: border-box;
    #bg {
      clip-path: polygon(100% 0, 100% 69%, 44% 100%, 0 100%, 0 0);
      background-color: map-get($colors,primary);
      width: 100%;
      height:100%;
      position: absolute;
      z-index: -1;
    }
  }
  ```
 #### Mixins
    Helpful with media queries. 
    Usually media queries are verbose and Mixins make this simple

    1) First we define a variable, which will define our pixel value breakpoint.
    2) Create a mixin using @mixin
    3) Use the mixin with @include

 #### Functions
  These are relatively new in the SASS world.
  You define a function, with arguments and then you return something back!
  ```javascript
    @function color($color-name) {
      @return map-get($colors,$color-name);
    }
  ```
     
 #### Sass & Media Queries

* Without SCSS
    ```javascript
    p {
      font-size: 16px;
    }

    @media (min-width: 768px) and (max-width: 1023px) {
      p {
        font-size: 18px;
      }
    }

    @media (min-width: 1024px) {
      p {
        font-size: 20px;
      }
    }

    ```
* With SCSS
    ```javascript
      // Declare Variables
      $tablet-width: 768px;
      $desktop-width: 1024px;


      // Declare mixins
      @mixin tablet {
        @media (min-width: #{$tablet-width}) and (max-width: #{$desktop-width - 1px}) {
          @content;
        }
      }

      @mixin desktop {
        @media (min-width: #{$desktop-width}) {
          @content;
        }
      }

      // Use mixins on elements
      p {
        font-size: 16px;

        @include tablet {
          font-size: 18px;
        }

        @include desktop {
          font-size: 20px;
        }
      }
    ```
 
 #### Math .
  You can also do math inside!

  #### Imports!
  Fortunately SASS has the @import rule. @import allows you to modularize your code making it easier to maintain by importing smaller SASS files. The difference between this and the CSS @import rule is that all imported SCSS files will be merged together into a single CSS file, so in the end, only a single HTTP call will be requested because you will be serving a unique CSS file to the web server.
  
  ```javascript
    @ import "source/font-awesome";
    @ import "source/slick";
    @ import "framework/bootstrap";  
    @ import "my-custom-theme";       
  ```


# Notes

* Two ways to use SASS in a project 
   - Go the package.json (npm init )+ webpack route
   - Use visual studio sass compiler ( use an extension as a hack to live pre-compile SASS)

* SASS is compiled into CSS.
* In our SASS File we could use SASS , but also regular CSS.
* use www.caniuse.com to compare features of different browsers.
* 3 diff pre processors : Stylus , less ,sass
* Main diff between SASS and SCSS : SCSS is newer version of SASS, and the syntax has indentation, similar to regular css.