## Svelte Presentation

React is one of many frameworks which could be used for web app development, here is a brief introduction to an alternative which is popular with developers.

Most of the information here is drawn from the [Svelte Website](https://svelte.dev/) and if this taster is appealing you should follow up by going through the full tutorial sequence on that site.

![Slide1](/presentation/src/assets/page1/images/Slide1.PNG)

Presentation front page with presenter names and appropriate theme.

![Slide2](/presentation/src/assets/page1/images/Slide2.PNG)

React initially seems like a single framework so it may initially look as though Svelte is a framework and SvelteKit is some kind of development environment.

However, Svelte is actually a compliler to javascript modules which produces a very small code footprint.  SvelteKit is the framework.

Come to think of it React is not sufficient on its own you customarily include React Dom and may need other elements such as React Router.

### Svelte

![Slide3](/presentation/src/assets/page1/images/Slide3.PNG)

The Svelte website has a good sequence of tutorials presented within an interactive online editor.

The four sections discuss basic and advanced Svelte and then basic and advanced SvelteKit framework.

I hope that by following quickly through the first few sections of the svelte tutorial and the first few of the basic SvelteKit we can gain enough awareness of the syntax to follow through the operation of the svelte demo application.

![Slide4](/presentation/src/assets/page1/images/Slide4.PNG)

First the svelte syntax.  The page has a script section and an html like section.

A script variable, name, can be passed as a property into the presentation section.  Since it is a string, string functions can be applied to it.

![Slide5](/presentation/src/assets/page1/images/Slide5.PNG)

Variables can also be included as properties in the attributes of an html element.

Where the variable name is chosen to match the attribute name a short form syntax can be used.

![Slide6](/presentation/src/assets/page1/images/Slide6.PNG)

Style tags placed in a file apply their style to the scope of the file.

![Slide7](/presentation/src/assets/page1/images/Slide7.PNG)

If a paragraph is imported into the page from a separate file, it does not pick up the style from the importing files style tags.

![Slide8](/presentation/src/assets/page1/images/Slide8.PNG)

Whilst React would try to interpret `<strong/>` as JSX, svelte does not interpret this by default so the result of line 5 is to print the text literally.

The inclusion on line 6 of @html causes the html to be interpreted and produce bold text.

![Slide9](/presentation/src/assets/page1/images/Slide9.PNG)

This script provides a counter defined outside a function which increments it.   No need to use hooks at this point.

The button element has an on attribute for mouse click which will call the increment function when the mouse is clicked.

Line 11 is a standard javascript short format if then else structure which ensures that if the count is exactly 1 the button will display the singular term of 'time'.

![Slide10](/presentation/src/assets/page1/images/Slide10.PNG)

The $: syntax introduces a reactive variable which will result in an update of the display when it is changed.  This maintains the value of doubled as count * 2.  Note that the $: syntax is not needed in the display line 15.

![Slide11](/presentation/src/assets/page1/images/Slide11.PNG)

The last basic example reviewed here is the array example.  The svelte syntax does not introduce much new, but this is a good reminder of some javascript syntax.

... spreads the array elements out and then another element is added.  This makes numbers in line 5 change when the addNumber function is called.
Some syntax variations which might look ok would not cause a change in a manner which would trigger a change in display through the reactive variable 'sum'.

A reducer is a function which acts on an array to evaluate a single numerical result, in this case the sum of array elements.

A join produces a string representation of the array whith a selected delimiter.

![Slide12](/presentation/src/assets/page1/images/Slide12.PNG)

To learn more you should continue to work through the svelte tutorial examples yourself, but for now jump forward to get an introduction to the SvelteKit syntax.

### SvelteKit

![Slide13](/presentation/src/assets/page1/images/Slide13.PNG)

The website lists some of the features provided by SvelteKit.  This includes routing (without needing a separate router) and server side rendering.  Svelte will need to run on a suitable server.  For development the Vite development server is appropriate.

The structure of the project directory includes a `src` folder with the app.html and a routes folder with at least on `+pages.svelte` file.

![Slide14](/presentation/src/assets/page1/images/Slide14.PNG)

The html file contains a `<div>` which displays %sveltekit.body% this is the location where the svelteKit output will be rendered.

There is no link required, the file which provides the output is the first `+page.svelte` in the routes folder.

![Slide15](/presentation/src/assets/page1/images/Slide15.PNG)

A second display page can be added within a nested folder within routes.  The name of the folder, 'about' will provide the adress for navigation.  So this is unlike a web page navigation there is not an http://filename call.

The routing syntax is simple and straightforward.

![Slide16](/presentation/src/assets/page1/images/Slide16.PNG)

It would not be efficient to include the same navigation code on every page which needed it so the code can be incorporated into a layout.

The `<slot/>` is the location on the layout where the content from the individual pages will be rendered.

![Slide17](/presentation/src/assets/page1/images/Slide17.PNG)

Hopefully that is enough to be able to read through a demo file running in a docker development container.

## Demo App

![Slide18](/presentation/src/assets/page1/images/Slide18.PNG)

Start Docker desktop.

Create and empty folder and then using CTRL + P ask the remote container plugin to open it in a container.  Follow the prompts to select a node plus typescript container and allow time for this to download content.

When the container is ready check the version of node.

Now create a svelte app using the latest svelte version.

Follow the choice which creates the demo app.

![Slide19](/presentation/src/assets/page1/images/Slide19.PNG)

Make choices to use Typescript syntax and to add the prettier code formatter.

![Slide20](/presentation/src/assets/page1/images/Slide20.PNG)

With no further options selected the project comes to completion.

There are a range of plug-ins for svelte which can be reviewed on github, however these are not required for the simple demonstration.

![Slide21](/presentation/src/assets/page1/images/Slide21.PNG)

The package json file reflects the available vite scripts and the dependancies.

![Slide22](/presentation/src/assets/page1/images/Slide22.PNG)

Change directory to the application folder and install the dependancies.

After a wait the project is ready to run on the vite server with npm run dev.

![Slide23](/presentation/src/assets/page1/images/Slide23.PNG)

The demo includes a navigation menu, a welcome image, some text and a counter.  These elements will be brought in from smaller files.

![Slide24](/presentation/src/assets/page1/images/Slide24.PNG)

The Sverdle demo game mimics the operation of the popular wordle site which gives the option to guess a five letter word.  Correctly guessed letters have a border added and correctly placed letters are highlighted.

Incorrectly guesse letters are grayed out on the alphabet display.

![Slide25](/presentation/src/assets/page1/images/Slide25.PNG)

An example game is played out here from the first guess of 'bread' to the final correct word 'icily'.  Because the source words are provided from the server there is nothing in the browser which could allow the player to cheat.

![Slide26](/presentation/src/assets/page1/images/Slide26.PNG)

Looking over the demo code the html has a place for sveltekit head and sveltekit body.  There is nothing of the displayed content here.

![Slide27](/presentation/src/assets/page1/images/Slide27.PNG)

The layout provides the common content for all pages which includes text imnported from Header.svelte.

The `<slot/>` in the main section is where individual page details will render.

![Slide28](/presentation/src/assets/page1/images/Slide28.PNG)

The home page is the first `+page.svelte` in the routes folder.

This includes the header information with the title 'home'.

The counter is read from the counter file.  There is no need for an import statement, just use the `<Counter />` element reference.

![Slide29](/presentation/src/assets/page1/images/Slide29.PNG)

The navigation bar is in the Header file which is called into the top of the layout for all pages in the app.

![Slide30](/presentation/src/assets/page1/images/Slide30.PNG)

As with React, the application can be built on Vite and previewed to check that it is working.  The use of a different port indicates that this is a build preview.

![Slide31](/presentation/src/assets/page1/images/Slide31.PNG)

Unlike react, the output is not an html/javascript file which can run from the live server.  

To deploy the user must first install an adapter and then edit the svelte.config.js file to mathch the deployment target, such as a node server in this example.


![Slide32](/presentation/src/assets/page1/images/Slide32.PNG)

A number of deployment targets exist and this does include a static HTML page where this is right for the application.

![Slide33](/presentation/src/assets/page1/images/Slide33.PNG)

Looking at use cases on the svelte website it is evident that well functioned applications can be produced.

![Slide34](/presentation/src/assets/page1/images/Slide34.PNG)

Here data visualisation is shown on a svelte page.

The companies are real and significant, but tend not to be the larger companies which are still using the commercially supported frameworks such as react.

![Slide35](/presentation/src/assets/page1/images/Slide35.PNG)

If you are willing to work with a system which is not as popular as the main players there is a benefit in code of server side rendering and a syntax which becomes comfortable to work with.

