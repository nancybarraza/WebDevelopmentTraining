# JS Web-Apps Development.
## Table of contents
1. [Introduction](#introduction)
1. [Cross-Browser compatibility](#cross-browser-compatibility)
	* [What is it?](#what-is-it)
	* [Why we need it?](#why-we-need-it)
	* [Does worth build apps for IE?](#does-worth-build-apps-for-ie)
	* [Fundamentals of cross-browser development](#fundamentals-of-cross-browser-development)
1. [Tasks Runners](#tasks-runners)
    * [Webpack](#webpack)
   		* [Basic Setup](#basic-setup)
   		* [Common Loaders](#common-loaders)
1. [UI/UX Basic fundamentals](#ui-ux-basics)
1. [Styling methods](#styling-methods)
	* [CSS vs SCSS](#css-vs-scss)
	* [SCSS vs Less](#scss-vs-less)
1. [JS Frameworks](#js-frameworks)
	* [Vanilla JS vs TypeScript](#vanilla-js-vs-typescript)
		* [Pros and cons of each](#pros-and-cons-of-each)
	* [Angular vs Vue](#angular-vs-vue)
		* [When use angular?](#when-use-angular)
		* [When use Vue?](#when-use-vue)
		* [Is one better than other?](#is-one-better-than-other)


## Intro
A web application or web app is a client–server software application in which the client (or user interface) runs in a web browser.

Here are the main differences between a website and a web app:

* The website is a complete product which can be seen on your browser. The web application can be a part of a website
* Functions of a web application are much complex than functions of a website. A website just shows collected data and information 	while web application maintains the whole website
* A website is a source of information while web application works interactively
* A website works on a web browser and a web app runs and used on a computer
* The website is easily ascertainable through any operating system and device, only by using URL. But the web app should be downloaded and installed first for proper work.

The benefits of a web application
1. Web applications run on multiple platforms without paying attention to OS or device as long as the browser is compatible
1. Any compatibility issues are eliminated by access the same versions by all users
1. Web applications are not installed on the hard drive, thus eliminating space limitations. Also, web applications reduce software piracy in subscription-based versions
1. The costs for both the business and the end user are reduced as there are less support and maintenance required by the business and lower requirements for the end user’s computer
1. Different online apps and other programs provide the same functionality as the desktop versions. However, they easily accessible from anywhere and have broader reach because of working across multiple platforms.

###Frontend
One of the things that customers look for in a web app is an user-friendly UI and flexible at the same time. Developers need to have strong skills in development tools and frontend techniques. Plus, they need to have the solid understanding of the best practices with regards to the front end of the web app.

###Backend
Backend specialists should provide a highly scalable web app to ensure the performance of the web app is optimized. With a fast and stable backend, the web app will allow your business to grow.

## Cross-Browser Compatibility

## Material Links
1. [What is cross-browser and why we need it](https://medium.com/@sarahelson81/what-is-cross-browser-compatibility-and-why-we-need-it-b41423c3501a)
2. [Differences between UI and UX](https://careerfoundry.com/en/blog/ux-design/the-difference-between-ux-and-ui-design-a-laymans-guide)
3. [UX Crash Course: 31 Fundamentals](http://thehipperelement.com/post/75476711614/ux-crash-course-31-fundamentals)
4. [Angular vs Vue](https://itnext.io/angular-5-vs-react-vs-vue-6b976a3f9172)
5. [Angular vs vue 2](http://cuelogic.com/blog/angular-vs-react-vs-vue-a-2018-comparison/)
6. [CSS vs SCSS](https://responsivedesign.is/articles/difference-between-sass-and-scss/)
7. [SCSS vs Less](https://marksheet.io/sass-scss-less.html)
8. [SCSS vs CSS](https://www.quora.com/What-is-the-difference-between-CSS-SASS-and-SCSS)
9. [TypeScript vs JavaScript](https://stackify.com/typescript-vs-javascript-migrate/)
10. [TypeScript vs JavaScript 2](https://hackernoon.com/typescript-vs-javascript-b568bc4a4e58)
11. [Learn TypeScript or keep with Vanilla?](https://www.quora.com/Should-I-learn-TypeScript-Flow-or-stick-with-vanilla-JS-Would-they-make-me-better-at-all-If-so-which-one)