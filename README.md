# PhotoRing

![Photoring live screenshot](/static/img/photoringLive.png)

PhotoRing is a tool that allows someone visualize and traverse a big repository of images across *all its dimensions*. It offers the user a sense of location within the dataset. A user can change dimensions, jump between sections and zoom in and out in order to see more or less photos.

You can see a live version of this app [here!](http://photoring.herokuapp.com)

## Getting Started
To get a copy of these project install git bash, open it from the command line and use 
```
$ git clone: https://github.com/daviddlaiton/photoringSQL
```

### Prerequisites

Firstly, you need to install nodeJS, the installer can be downloaded from: https://nodejs.org/es/
Be sure to select the install npm option and the addToPATH option during the installation process.

Secondly, you need to install MySQL server. The installing instruccions are in: https://dev.mysql.com/doc/refman/8.0/en/installing.html 
You only need the server, but installing additional software it's optional.

Finally, you need a SQL Client. It can be one of your preference.

Checklist:
```
NodeJS
MySQL Server
MySQL Client
```

### Database configuration

1. create an empty mySQL database with the name `photoring`. This can be done from the MySQL client.

	**Warning** Is important to name the database correctly, if don't it's necesary to change the information on the code.

2. Run the script named `create_tables.sql` on MySQL client. 

3. Insert the data (Available in `/dataset/photos.csv`) into the table the script created (`photos`) using the method you prefer. 

4. Run the script named `create_metadata_tables.sql`: This scripts create the necessary tables for the operation of Photoring.

5. Replace the configuration file `config.js` with the connection to the database you just created.

### How to run it

 All the necessary dependencies are already located in the  `node_modules` directory. Open a terminal in the directory of the proyect and run the following commands:

```
npm start
``` 
o
```
node server.js
```

The server should have started listening at http://localhost:8087. If you want to change the listening port of the server, go to the `config.js` configuration file.


## How to use it



### Video on how to use Photoring 

Spanish [here](https://www.youtube.com/watch?v=PArgtZ5IpsU).

### Explanation

<img align="center;" width="200" height="200" src="/docs/msmonroe.png">

Images have metadata. For the image above, it looks like this:

* Title: Marilyn Monroe, actress, New York
* Identifier: 275101-28281
* Date: May 1957
* Authors: Richard Avendon
* Nationality: (American, 1923–2004)
* Camera: Canon-360ks
* Print: Gelatin silver print, printed 1989,
7 15/16 x 7 13/16" (20.2 x 19.8 cm)
* … And many more characteristics.

Photoring takes the characteristics of every photo/image in a collection and associates them with a dimension. For the image above, *Title*,  *Date*, *Authors*, *Nationality*, etc, all are going to become dimensions. You can traverse the dataset by any of these dimensions.

![Photoring screenshot with coloured boxes showing the 3 panels: Sections panel, action panels and visualization panel](/docs/photoringLiveBoxes.png)


When you open Photoring, it selects a dimension from the metadata of the photos randomly and then brings a batch of photos in the order given by that dimension. The batch is centered around a particular photo that appears in the middle of the Photo visualization panel (Box 3). When we say that the user moves through the dataset, we mean the current photo at the center of the visualization changes and therefore, all photos around it. 

In the image above you can see 3 different colored boxes:

1. Box 1: Dimension sections panel: This panel shows the dimensions sections that the current dimensions has. A section is a group of photos that share a dimension value. (e.g Hamlet and Macbeth share the dimension value *Shakespeare* in the author dimension)

2. Box 2: Actions panel: It has the following sequence of buttons:
	1. Previous Dimension
	2. Next Dimension
	3. Previous Section
	4. Previous Photo
	5. Next Photo
	6. Next Section
	7. Zoom out
	8. Zoom in

3. Box 3. Visualization panel: Panel in which photos/images are showed according to the current zoom level. Photos that belong to the same section have the same background color. As mentioned earlier. Photos are displayed in order, from top to bottom, according to the order associated with the current dimension. A user can also change the current 