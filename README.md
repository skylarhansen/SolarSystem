 # Solar System

### Level 0

Students will work with table views, learn about protocols, and implement the UITableViewDataSource and UITableViewDelegate protocols to build a Solar System directory.

Students who complete this project independently are able to:

* instantiate and place a UITableView on the screen
* work with UITableViewControllers
* implement a master-detail interface
* implement the UITableViewDataSource protocol
* use the UITableViewDelegate protocol methods to respond to user interaction
* instantiate and place UIImages on the screen
* use a Model Object Controller to access model objects

## Guide

### Master List View

Build a view that lists the planets. You will use a UITableViewController and implement the UITableViewDataSource protocol methods. Note than one could use a UIViewController with a UITableView placed on it, but UITableViewController implements a full screen UITableView by default, and comes with other benefits discussed in the lesson.

The UITableViewController subclass template comes with a lot of boilerplate and commented code. For readability, please remove all unused boilerplate from your code. 

1. Add a UITableViewController as your root view controller in Main.storyboard and embed it into a UINavigationController
2. Create a PlanetListViewController file as a subclass of UITableViewController and set the class of your root view controller scene
3. Implement the UITableViewDataSource methods using the PlanetController.planets array
    * note: Pay attention to your `reuseIdentifier` in the Storyboard scene and in your `dequeueReusableCell(withIdentifier:for:)` function call
4. Set up your cells to display the name, image, and index of the planet 
    * note: Look at the included properties and various styles of a UITableViewCell
    * note: Experiment with the content modes on the cell's UIImageView to display the image in different ways


### Detail View

Build a view that displays the details of a planet. Display an image of the planet and include planet data for distance, day length, and diameter. This view will be reused for each planet. 

1. Add a new scene to Main.storyboard
2. Create a `PlanetDetailViewController` file as a subclass of UIViewController and set the class of your detail view scene
3. Add a UIImageView and UILabels to display the data
    * note: Experiment with Autolayout automatic constraints or UIStackViews to create an appealing detail view
4. Create outlets from the UIImageView and UILabels to your `PlanetDetailViewController` class
5. Add a new function called `updateViews` that checks for a planet and updates the view controller's title, UIImageView and UILabels with the planet's data
    * note: This is an extremely common design pattern. Commit it to memory. If you have a detail view or table view cell template that displays data, use an 'update' method that checks for model data and updates the view elements with the correct data.
6. Call the `updateViews()` function in your `viewDidLoad()`.
7. Add an optional `planet` computed property that calls `updateViews()` whenever it gets set. This will be set by the Master List View when performing the segue

You can test your view and the `updateViews()` function by setting the detail view as the initial view controller and by setting `planet` to `PlanetController.planets[0]` in the `viewDidLoad()`. Be sure to reverse those changes when you are done checking that the view works or you may have undesired behavior when you are finished with the app.

### Segue

Create a segue between your List View and Detail View that will pass the selected planet to the detail view for display.

1. Control drag from your prototype cell in the List View to the Detail View to create a segue
2. Select the segue and give it an identifier
    * note: As a matter of best practice, the identifier should describe what the segue does, for example `toPlanetDetail`
3. Add the `prepare(for segue: UIStoryboardSegue, sender: Any?)` function to your PlanetListViewController class
    * note: Remember that `prepare(for segue: UIStoryboardSegue, sender: Any?)` will get called on all segues triggered from the current scene and accompanying view controller class
4. Implement the `prepare(for segue: UIStoryboardSegue, sender: Any?)` method by checking for the correct segue identifier, capturing an instance of the `PlanetDetailViewController`, capturing an instance of the selected planet, and setting the `planet` property of the `PlanetDetailViewController`
    * note: Look at UITableView documentation to find a way to capture the indexPath of the selected row
    * note: Remember, the `PlanetDetailViewController` will use the `planet` property to update itself when it loads to display to the user

### Black Diamonds

* Add additional model data to the Planet class, update the PlanetController to include it, and update the PlanetDetailViewController to display it
* Add an image of the entire Solar System as a header view to the Planet List Table View
* Create a Unit or UITest that verifies the number of cells in the PlanetListViewController
* Create a Unit or UITest that verifies the values of PlanetController.planets

### Tests

## Contributions

Please refer to CONTRIBUTING.md.

## Copyright

© DevMountain LLC, 2015. Unauthorized use and/or duplication of this material without express and written permission from DevMountain, LLC is strictly prohibited. Excerpts and links may be used, provided that full and clear credit is given to DevMountain with appropriate and specific direction to the original content.
