# CPSC1517-1232 Exercise 3

> This exercise is part of a series of exercises to manage information on Renovations. In this exercise you will create a Blazor web application project. Reno Tracker is a site to keep up-to-date with your renovation projects.
>
> **This set is cumulative;** future exercises in this series will build upon previous exercises.

## Objective

Upon completion of this exercise, you will have demonstrated the ability to:

- use an existing class library of data models in a web application
- implement a data entry component with input validation
- implement a tablular report form a collection of data
- use a CSV file for data persistence (append data, read and display)

----

## Project/Solution Setup

You are to create a new ASP.NET Core **Blazor** Web Application project for this exercise. Create the project for .Net Core 8 and give your project the name **`RenoWebApp`**. Check with your instructor about specific settings/customizations for your Blazor project. Add the project to your existing solution of your prior exercises.

To ensure that your web application works, build and run your project. A browser window should open in a local hosted port.(Example https://localhost:5001 , your port may be different). 

The styling for your application is up to you. The default template for the `web app` project uses Bootstrap built in, but you can use any website styling you choose. (**Note:** Your instructor may offer specific guidance/restrictions with regard to styling.)

### Reference Your Existing Class Library

For your web application, add a project reference to the `RenoSystem` class library so that you can use its classes in your application. You will be making use of the `Wall`, `Opening` and `OpeningType` types. (***Note:** You will need to fix any outstanding errors from previous exercises for these data types.*)

### Add a `Data` Folder

Add a folder to your web application project and give it the name `Data`. You will need to place your CSV file into this folder. Create a text file called `TestData.csv` within this folder. In this file, you will need to enter the following sample CSV content as your initial set of data.

```csv
brd1_1A,340,260,#ffffff,130,160,Window,12
brd1_1B,302,260,#ffffff
brd1_1C,302,260,#ffffff
brd1_1D,340,260,#ffffff,60,200,Door,12
```

----

## Web Application Content

### Modify the Main Layout

Modify the main layout component to include your name, section number, and instructor's name as a `<footer>` on your website. This needs to be part of the main layout so that it appears on every page within the website.

### Update the Website Navigation

Add links for the following pages in your website's navigation. (Leave the current default links on the menu; you are simply adding to the existing navigation.)

- **`/RenoWalls`** with the link text "Walls"
- **`/RenoReport`** with the link text "Report"
- **`/About`** with the link text "About".

Create your own (or find an existing) image that you wish to use as a brand image (*logo*) for your navigation menu. If you are using an image that someone else created, make sure that you give credit to the individual on your `About` page.

> ***Tip:** Create placeholder pages for the new navigation links. You will need to modify the content of those pages as noted later in these specifications. Ensure each page has an appropriate page title (i.e.: the title in your browser tab) for its content.*

### Modify the Home Page

Modify the home page to include the following.

- The page title (i.e.: the title in your browser tab) for the site must be **`Reno Tracker`**.
- A header (`<h1>` tag) with the content: `Reno Tracker`.
- An image (e.g.: a larger version of your site's logo or some other image) as a "Hero" image for the site. Ensure the hero section of your site does not exceed 700 px in height.
- One to two paragraphs offering a welcome message and summary description of the site (use your own wording).

### The `/About` Page

In your `About.razor` component include the text `Exercise 3 - Jan 2024` in an `<h1>` tag. Following that, include this content (each with an appropriate `<h2>` header):

- **`Author: Your_name`** with your full name replacing the *`Your_name`* portion
- **`Section: A##`** with the *`A##`* being your section number (e.g.: `A01`)
- **`Instructor: Somme Body`** with your instructor's name (i.e.: replace *`Somme Body`* with the appropriate name)
- **`Known Bugs:`**
    - After this heading, include an un-ordered list of known bugs (items that are non-functional or incomplete) with respect to the requirements for this exercise.

### The `/RenoReport` Page

In your `RenoReport.razor` component, you are to display the records of renovation walls as read from the CSV file created earlier. Read the content into a collection of `Wall` objects and display the collection on the page in a tabular format (refer to the mockup image below). Remember to display an appropriate message if the collection is empty and offer a loading message while the data is being retrieved.

![RemoWallInfo Page](./WallReport.png)

![RemoWallInfo Bad Page](./WallReportBad.png)

### The `/RenoWalls` Page

In your `RenoWalls.razor` component, you are to provide the user the ability to add walls for the current renovation. Your page will need to append the user's input to your existing CSV file. The user's input is to be validated according to the internal behaviour of your `Wall` class (i.e.: you will need to catch any exceptions when instantiating `Wall` objects and display appropriate feedback to the user). When appending to the CSV file, use the `.ToString()` method of your `Wall` class to represent the data.

A mockup image of the required component is supplied. Your component does not need to have the same layout **but** must use the same variety of controls as the mockup for the page content. The following buttons should be included in your form.

- **Record** will validate the incoming data and save to the CSV file if correct.
- **Clear** will reset the fields to empty input state.
- **Go to Report** will transfer the user to the Wall Report page.

To provide guidance to the user during input, ensure your form includes the following.

- Indicate required fields with an asterisk - `*`
- Users are allowed to include a single opening for the wall; the entire section of input must be blank in order for it to be interpreted as "no opening"

![RenoInput Page](./RenoInput.png)

Be sure to validate the incoming data and display any errors as a single summary with a list of specific problems; each individual error must have a unique message so that the user knows exactly what input is incorrect (i.e.: do not generalize your error messages).

> ***Note:** You are allowed to modify your `Wall` and `Opening` classes' validation to reflect the error message formats below.

![RenoInputErrors Page](./RenoInputErrors.png)

----

## Evaluation

> ***NOTE:** Your code **must** compile. Solutions that do not compile will receive an automatic mark of zero (0).*
> 
> If you are unable to get a portion of the assignment to compile or work, you should:
> - Comment out the  portion of code
> - Identify the reason for the commented portion (such *as does not compile* or *does not work cause an abort*)

Your assignment will be marked based upon the following weights. See the [general rubric](../../README.md#generalized-marking-rubric) for details.


| Earned | Weight | Deliverable/Requirement | Comment |
| :----: | :----: | ----------------------- | ------------- |
|        |  1     | Inclusion of working class library |    |
|        |  1     | Site Layout |    |
|        |  1     | Site Navigation |    |
|        |  1     | Home Page |    |
|        |  1     | "About" page |    |
|        |  3     | `RenoReport` component |   |
|        | 10     | `RenoWalls` component |   |
|        | -4     | Other concerns and penalities<sup>†</sup> |   |
| ------ | ------ | --------- |  ------ |
|        | **18** | **Total Weight** | ------ |


> **†** - (max -4) Examples include, but not limited to: broken links, commits does not reflect incremental development, does not comiple, requirements not used, etc.

----

[Return to exercises](../README.md)

