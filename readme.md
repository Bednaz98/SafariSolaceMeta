# Safari Solace Meta

## Overview

This repo is a meta repo linking to and explaining general overview of a front end application project titled **Safari Solace**. This project was created as a proof of concept and practice using and combining several technologies. The project composes of 5 main parts:

1.  **A back end docker container**
2.  **Safari Solace IT**
3.  **Safari Solace Pal**
4.  **Safari Solace Helper**
5.  **styling tools**

## Project components

The main focus on this project was to create a collection of single page applications that would be compatible as a website with a url while being downloadable on Android and IOS. Each of these applications would server as a different online platform for a fictional company _Safari Solace_, which is offering a vacation resort to possible clients. Safari Solace needs three main tools to help this company runs:

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

The _Styling Tools_ repo was created as a way to view all components at a glance and make changes in real time. This was done to test how the component library behaved and effected formatting while design the UI outside of the main projects.

The Backend was created and provided as a docker container that was hosted on Azure. This backend interacted with a Postgres database for the server's end point to pull different information from (employee information, service request details, etc...).

## Integration Process

The Safari Solace IT, Pal, Helper and Styling tools where all created using Expo which pools together
