# ancient-places-eda
A data analysis project into historical sites across the globe using data from Pleiades

## Scribbles 

A few data sources are places and names. Names refer to a specific temporal settlement at a broader geographic location, whereas places refer to an historic, excavated site. For example, Jericho is a broader location but has 20+ different names representing different settlements emerging on the same site throughout history or associated references in historical documents. Jericho the site is referred to by 20+ names including Tall as-Sultan, Tell el-Sultan, Hierichous, Jericho etc.
As below, the link between the two datasets is the placeID or pid (in names sheet(with longer link name)) and simply id in the places sheet.

 ![image](https://github.com/user-attachments/assets/a735fcce-51e1-49a6-bf7a-8dd2d028836e)
![image](https://github.com/user-attachments/assets/d6406985-6173-4850-a8e8-f4c75db617ec)

As a many to one relationship exists between pid to id - I will use a field in the names sheet as my primary key to start with - there is already a field that appears to fill this, 'uid' which I take to mean unique id. In order to ensure this is a good fit, I will ensure this identifer is unique to each entry and is not repeated. Using a countif and then applying a filter, I was able to see that a number of uids did appear twice in the data. Ideally I want to remove these duplicates if it means I lose no data in the process of doing so. 

![image](https://github.com/user-attachments/assets/0d2b8b04-75b5-48ec-b89e-08a4622c90e1)

Unfortunately, because the entries were not exact duplicates, with some representing different habitation periods, I will need to discount uid as a unique identifer - this may have worked for the original purpose of the data, but is something I will change in the product. Ensuring a truly unique identifier for each entry is a learning I have made since my previous project. I will create a new identifer column in the names sheet when completing ETL on the data - I did the same check on the places sheet and fortunately id was a truly unique identifer and will serve as the primary key for the places dataset.

I now need to rationalise which data I need in each sheet and then I will use power query to prepare my data.
* MinDate: Date of earliest speculated inhabitation (-ve dates reflect BC/BCE)
* MaxDate: Date of latest speculated inhabitation (some sites are currently inhabited and may be marked as 2100, 2000 or other - I will look to standardise this during
* pid: Unique identifer for place/archealogical site (needs to parsed from the end of the id given in the original names sheet
* nid: Unique identifer for differing names of sites/also reflects different iterations of same/similar settlements - will need to create this myself
* location_precision: precise, rough, unlocated - some entries are left blank, I will mark these as unknown.
* transliterated_name: an existing field, offering the name as it best known.


I had spent much of the early stages of this project at the places level. Using Power BI, I was able to geomap the places - using time filters to see how patterns of expansion occurred (fertile crescent very clear to see).




When parsing out primary type, some listings show as church and others as church-2. I don't know why this is. I assume it is a grouping standard adopted by the original composers of the data.
