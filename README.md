Extract "Everything Added to Food in the United States" Database
======================================

## General Description ##

`extractEAFUS.py` will pull the HTML file for the FDA's [EAFUS database](http://www.accessdata.fda.gov/scripts/fcn/fcnNavigation.cfm?rpt=eafusListing) and parse it into a paired down HTML file and into a pipe delimited (`|`) text representation.  Credit to the FDA for the database.

What is the [EAFUS](http://www.fda.gov/Food/IngredientsPackagingLabeling/ucm115326.htm)?

It's a list of 3000+ substances that are legally allowed to be added to foods in the United States.  These substances were either directly approved by the FDA or are affirmed by the FDA to be "generally	recognized as safe" ([GRAS](http://www.fda.gov/food/ingredientspackaginglabeling/gras/default.htm)). The table from the EAFUS website contains only five fields from the complete FDA database (PAFA).  They are:

- doctype - Status of toxicology information available
- docnum - PAFA database number for printed information on substance
- mainterm - name of substance
- cas rn or other code - registry number for the substance
- regnum - FDA regulation numbers where the substance appears 
		
## Running the code ##

It should be cross-platform compatible with python 2.7 and up.  One additional software dependency: [BeautifulSoup4](http://www.crummy.com/software/BeautifulSoup/), which can be installed by `pip install bs4` (provided you have pip).

The pulling of data from the eafus site is based on HTML elements and CSS styling.  This software could easily break if the FDA changes its HTML or CSS, so for the sake of providing a source of the data, the repo includes the output of the code: `eafus_20_06_2014.txt` and `eafus_20_06_2014.html`.  Both were pulled down on 06/20/2014.

## Using the data ##

As a small example of what you could do with the data, I've added a python script to generate a fake food label in `/GenerateFoodLabel`.  It takes the text file of the eafus database, grabs a bunch of random additives, throws them into an HTML page and then converts that to a pdf.  Resulting in something like:

![Fake label](./GenerateFoodLabel/index.png) 

I used the code in [rendersketchgame](https://github.com/mikewesthad/rendersketchgame) to create an endless aisle of food additives:

![Eafus Aisle](https://raw.githubusercontent.com/mikewesthad/rendersketchgame/master/06_21_2014/eafusAisle.png)
