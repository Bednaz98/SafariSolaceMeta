# Safari Solace Meta

## Overview

This repo is a meta repo linking to and explaining in general terms an overview of a front-end application project titled **Safari Solace**. This project was created as a proof of concept and practice using and combining several technologies. The project composes of 5 main parts:

1.  **A back end docker container**
2.  **Safari Solace IT**
3.  **Safari Solace Pal**
4.  **Safari Solace Helper**
5.  **styling tools**

## Project components

The main focus of this project was to create a collection of single-page applications that would be compatible as a website with a URL while being downloadable on Android and IOS. Each of these applications would serve as a different online platform for a fictional company _Safari Solace_, which is offering a vacation resort to possible clients. Safari Solace needs three main tools to help this company runs:

1. Admin tools (_Safari Solace IT_)
   - For creating users
   - Updating user passwords
2. Downloadable Application for clients (_Safari Solace Pal_)
   - Allows vacationers to login with a reservation
   - Allow users to request room service offerings
     - view request progress
     - cancel orders
3. Downloadable application for employees (_Safari Solace Helper_)
   - Allows employees to clock in and out of work
   - Allows employees to view customer service offering request
     - update the progress of each request as "Processing" or "Completed"

The _Styling Tools_ repo was created as a way to view all components at a glance and make changes in real-time. This was done to test how the component library behaved and affected formatting while designing the UI outside of the main projects.

The Backend was created and provided as a docker container that was hosted on Azure. This backend interacted with a Postgres database for the server's endpoint to pull different information from (employee information, service request details, etc...).

## Integration Process

The Safari Solace IT, Pal, Helper, and Styling tools were all created using Expo which pools together several community packages that is commonly used together. One issue that came with trying to create three applications at once was keeping a consistent styling across all three applications.

### Styling Tools

To address this styling issue, a new component library was created and tested using the Styling project. The component library is a collection of components wrappers. Each wrapper was pre-pended to the front of each component in the library as a convention. Within each component, the return JSX elements were normal React Native elements wrapped in views. Within each wrapper component, all values needed to have the React Native elements work were passed in as props. The only exception was anything that could affect visual appearances.

A styling configuration page was created that defined several enums and _'styling functions'_ that were used to return specific values. A "theme" enum was implemented within a context provider. The context hook was then used in each styling function to retrieve this theme enum and used in a switch case to return values needed for each theme. In this way, styling attributes such as shadow radius, padding, margin, and others were consistent for all elements within the library component.

For some components where more detailed stylistic choices needed to be made, a similar approach of creating an enum and a styling function was used. For instance, in the text component, there was an enum called _' text type'_ that was used to determine if the text component should be either a title, header, or general text. From there several functions returned the appropriate font size, font family, and alignment. When using the text component, all one needs to do is pass in the text type as a prop and the component will handle the rest of the styling.

To keep a consistent color palette for each theme, an enum was created to identify what the color would be needed to be applied to. A handful of examples are text title, text header, text general, inner modal, primary color, secondary color, etc... This color palette could be returned based on 1 switch statement. From there, this switch statement was nested in a theme switch statement to swap which color palette to choose from for each theme.

In this way, all that had to be done was set up the return values in all styling functions and these changes would be reflected in all parts of the application. From there this component library was added as a submodule (using git) within the other project. All components behaved the same way and only the configuration file needed to be changed.

### why use this styling?

1. The first reason was to have control over all styling in isolation. In the styling project, one can view all components at a glance and see their interactions and overall design.
2. A design was made to keep the same styling consistent for all 3 projects. If a single stylistic change was made, by using the component wrappers, no code had to be altered elsewhere in the code.
3. Early on there was a question about whether or not to use React or React Native for each project. Expo has build-in capabilities for building on both mobile and web simultaneously. Be using this wrapper system, if any project needed to use React, all that would have to be done would be to copy the whole project to a React-only project and only change the wrapper returns to use React components rather than using React Native components. This would in theory save time and effort. Using Expo was perfectly fine and this problem did not need to be addressed.

### Redux or Provider?

Most people on the team had little experience with Redux. Rather than using it, the team opted to use the Provider system that was introduced to React after Redux was created. By storing all common state variables and their associated set functions within a single provider, the need for redux was eliminated entirely. For any complicated state management, a state handler class was created. An interface was created with the primary functions that the whole team would need to interact with (more where added as necessary). For complicated state manipulation, have a separate class handler all data keep all components shorter, cleaner, and more readable. This also isolated the state management from the component making debugging easier to work with.

### HTTP calls

In a similar structure above, instead of having components directly making HTTP calls, this was moved to an HTTP handler. For some projects, several handlers were created to manage HTTP calls. This again helped isolate any issues and made components easier to read. It also allowed for more modular code and less code re-writing. several times code implementation needed to be changed between a mock server and a "real" server. Having an HTTP handler helped made this seamless.

## Contributor

Team leader [Joshua Bednaz](https://github.com/Bednaz98)

Designer [Kris Bothmer](https://github.com/akromatikus)

Developer [John Patrick](https://github.com/jpcollandra)

Developer [Brandon Zander](https://github.com/sdsmt05)

## License
