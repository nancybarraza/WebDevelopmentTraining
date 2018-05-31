# JS Web-Apps Development.
## Table of contents
1. [Introduction](#introduction)
1. [Cross-Browser compatibility](#cross-browser-compatibility)
1. [Webpack](#webpack)
1. [CSS Pre-Processors](#css-pre-processors)
1. [JS Frameworks](#js-frameworks)


## Intro
A web application or web app is a client-server software application in which the client (or user interface) runs in a web browser.

The main differences between a website and a web app:

* The website is a complete product which can run in your browser. The web application can be a part of a site
* Functions of a web application are much complex than functions of a website. A website shows collected data and information     while web application maintains the whole website
* A site is a source of information while web application works interactively
* A website worked on a web browser and a web app runs and used on a computer
* The site is readily ascertainable through any operating system and device, only by using URL. But the web app should be downloaded and installed first for proper work.

The benefits of a web application:

1. Web applications run on multiple platforms without paying attention to OS or device as long as the browser is compatible
1. Eliminate any compatibility issues by access to the same versions by all users
1. Web applications are not installed on the hard drive, thus removing space limitations. Also, web applications reduce software piracy in subscription-based versions
1. Reducing the costs for both the business and the end user as there are less support and maintenance required by the company and lower requirements for the end user’s computer
1. Different online apps and other programs provide the same functionality as the desktop versions. However, they easily accessible from anywhere and have broader reach because of working on multiple platforms.

### Frontend
One of the things that customers look for in a web app is a user-friendly UI and flexible at the same time. Developers need to have strong skills in development tools and front-end techniques. Plus, they need to have the solid understanding of the best practices with regards to the front end of the web app.

### Backend
Backend specialists should provide a highly scalable web app to ensure the performance of the web app is optimized. With a fast and stable backend, the web app will allow your business to grow.

## Cross-Browser Compatibility

Cross-Browser compatibility is the capability of a website or web app to respond to the browser needs and improve the user's accessibility.

The development team must focus on the user's preferences, to know this, they can review the statics about the popular browsers. 
Our favorite browser is not the best to test our web apps, as we are not our users.

Latest global stats show that Chrome, Safari, and UC browsers are the top 3 browsers in 2018, but again, this statistics is a little misleading because in different areas people prefer different browsers, so focus your app compatibility in the data of your target.

There are some tools to make a web app cross-browser compilant:

* [Normalize.css](https://necolas.github.io/normalize.css/) Normalize all the CSS styles into all browsers.
* [W3C Markup Validation Service](https://validator.w3.org/) Validate your code.
* [Google Analytics](https://analytics.google.com/analytics/web/#/report-home/a8681823w46374149p46615848) GA allows you know your audience, so you can check which browser uses your users.
* [Webpack](https://webpack.github.io/) Webpack allows you modularize your bundles and reduce the impact of downloading, also, compile the JS to improve the compatibility cross-browsing.
* [Angular](https://angular.io/), [Vue](https://vuejs.org/) Using a JS Framework or Library will reduce the JS incompatibility.
* [Cross-Browse Testing](https://crossbrowsertesting.com/) Using testing tools will help you to find issues and fix.


## Webpack

Webpack is a module builder.  A tool wherein you use a configuration to explain to the builder how to load specific things. It does not run on your page; it runs during your development.

It will help to modularize the assets and static dependencies and libraries to reduce the loading times using chunks and modules. It allows to the browser identify the order of dependencies to load on each module first.

You can use Webpack via npm or yarn; it is up to you what to use.

### What is a loader?
A loader is a kind of task in other build tools like the grunt,  and provide a powerful way to handle the front-end build steps. Allows for preprocessing files as you `require()` or "load" into the application. 

There exist many types of loaders, the most common ones are: 

* Babel-Loader: 
    Help to generate the scripts in ECMA5 to help with cross-browsing compatibility.
* HTML-Loader:
    Process the HTML to generate the static files without compatibility issues.
* Style-Loader:
    Parse the styles bypass javascript to generate and render the elements without compatibility issues.
* SASS-Loader:
    Parse SASS into CSS. 
* File-Loader:
    Loads Files via static assets to help with lazy-serving.
* URL-Loader:
    Loads Files via static assets to help with lazy-serving.

### Basic Setup for Webpack.
```
const path = require('path'),
      webpack = require('webpack'),
      CleanWebpackPlugin = require('clean-webpack-plugin'),
      HtmlWebpackPlugin = require('html-webpack-plugin'),
      ExtractTextPlugin = require('extract-text-webpack-plugin');

const extractPlugin = new ExtractTextPlugin({ filename: './assets/css/app.css' });

const config = {

  // absolute path for project root
  context: path.resolve(__dirname, 'src'),

  entry: {
    // relative path declaration
    app: './app.js'
  },

  output: {
    // absolute path declaration
    path: path.resolve(__dirname, 'dist'),
    filename: './assets/js/[name].bundle.js'
  },

  module: {
    rules: [

      // babel-loader with 'env' preset
      { test: /\.js$/, include: /src/, exclude: /node_modules/, use: { loader: "babel-loader", options: { presets: ['env'] } } },
      // html-loader
      { test: /\.html$/, use: ['html-loader'] },
      // sass-loader with sourceMap activated
      {
        test: /\.scss$/,
        include: [path.resolve(__dirname, 'src', 'assets', 'scss')],
        use: extractPlugin.extract({
          use: [
            {
              loader: 'css-loader',
              options: {
                sourceMap: true
              }
            },
            {
              loader: 'sass-loader',
              options: {
                sourceMap: true
              }
            }
          ],
          fallback: 'style-loader'
        })
      },
      // file-loader(for images)
      { test: /\.(jpg|png|gif|svg)$/, use: [ { loader: 'file-loader', options: { name: '[name].[ext]', outputPath: './assets/media/' } } ] },
      // file-loader(for fonts)
      { test: /\.(woff|woff2|eot|ttf|otf)$/, use: ['file-loader'] }

    ]
  },

  plugins: [
    // cleaning up only 'dist' folder
    new CleanWebpackPlugin(['dist']),
    new HtmlWebpackPlugin({
      template: 'index.html'
    }),
    // extract-text-webpack-plugin instance
    extractPlugin
  ],

  devServer: {
    // static files served from here
    contentBase: path.resolve(__dirname, "./dist/assets/media"),
    compress: true,
    // open app in localhost:2000
    port: 2000,
    stats: 'errors-only',
    open: true
  },
  devtool: 'inline-source-map'
};

module.exports = config;
```

** Note: Using Angular-cli you **MUST** run the command `ng eject` to eject the Webpack settings into an external file. 

To get a better understanding of Webpack, you can view the documentation here: [Webpack Official](https://webpack.github.io/) and about [Loaders](https://github.com/webpack/docs/wiki/loaders).

## CSS Pre-Processors. 

To improve writing CSS, there were different approaches such as separating definitions into smaller files and importing them into one central file. This approach helped to deal with components but, did not solve code repetitions and maintainability problems. Another method was early implementations of object-oriented CSS. 

Having multiple classes increased re-usability but decreased the maintainability.

Pre-processors, with their advanced features, helped to achieve writing reusable, maintainable and extensible codes in CSS. By using a pre-processor, you can quickly increase your productivity, and decrease the number of lines you are writing in a project; you also can extend CSS with variables, operators, interpolations, functions, mixins and many more other usable assets. 

* SASS - SCSS:  Sass (Syntactically Awesome Style Sheets) is an extension of CSS that enables you to use things like variables, nested rules, inline imports and more. It also helps to keep things organized and allows you to create style sheets faster.

    ```
    .accordion {
      $accordion-header-color: $primary-color;
      $accordion-padding: 1em;
      
      @extend %module;
      @include transition(all 0.3s ease-out);
      background: $accordion-header-color;
      padding: $accordion-padding;
    }
    ```

*  LESS:  Less (which stands for Leaner Style Sheets) is a backward-compatible language extension for CSS. 

    ```
    @the-border: 1px;
    @base-color: #111;
    @red: #842210;
     
    #concrete_header {
      color: @base-color * 3;
      border-left: @the-border;
      border-right: @the-border * 3;
    }
    #concrete_footer { 
      color: @base-color + #003300;
    }
    ```

* Stylus:  stylus is a dynamic stylesheet preprocessor language that is compiling into Cascading Style Sheets. Sass and LESS influence its design. 
    
    ```
    // Defaults
    
    gridColumnCount ?= 12
    gridColumnWidth ?= 60
    gridPadding     ?= 20
    
    // Grid, row, cell
    
    .l-grid
      width unit(gridColumnCount * (gridColumnWidth + gridPadding), px)
      margin 0 auto
    
    ```

### Which to use?
The most popular pre-processor in web development across the world is SASS or SCSS. So if you want to create reusable and maintainable components, use SASS, but at the end, it is up to you.

![scss-graph](https://blog.keycdn.com/blog/wp-content/uploads/2015/09/sass-vs-less-poll.webp)


## JS Frameworks

JavaScript web frameworks are pretty popular among web-apps developers. They serve as a skeleton for single page apps, allow developers to worry less about code structure or maintenance while focusing on the creation of complex interface elements, and expand opportunities for JS and plain HTML.

![js-frameworks-graph](https://cdn-images-1.medium.com/max/1600/1*ADuCd_GcORWlpCzTASmkxQ.png)

###The advantages of using JavaScript frameworks:

* **Efficiency** — projects that used to take months and hundreds of lines of code now can be achieved much faster with well-structured prebuilt patterns and functions.
* **Safety** — top javascript frameworks have security arrangements and large communities where members and users also act as testers support them.
* **Cost** — most of the frameworks are open source and free. Since they help programmers to build custom solutions faster, the ultimate price for web app will be lower.

### So, Which to choose?

#### Angular (Formerly known as Angular2)

Comes with a long list of features that enable building everything, ranging from web to desktop and mobile. The framework is developed with TypeScript from Microsoft with an eye to making JavaScript more agile and attractive for large enterprises. ng2 features a component-based architecture, improved DI (dependency injection), efficient logging service, inter-component communications and more.  It is are a better option for enterprise-based applications or strict programming environments with high standards for code readability.

#### Vue.js

Vue 2.0 release was in 2016, and it took the best from Ember, React and Angular, putting all that into a handy package. It is proved to be faster and leaner, comparing to React and Angular 2.0.

Vue.js is a better choice for quick development of cross-platform solutions. It can become a firm basis for high-end single page applications (SPAs) and beneficial solution to those cases when performance is ahead of good code organization or app structure.


#### Conclusion:

Angular uses TypeScript and is ideal for programmers with a solid Object-Oriented Programming (OOP) background who need detailed guidance and structure, while Vue is relatively simple to pick up and integrate for a small team of core developers to agile apps development.
