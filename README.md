
![Tool Logo](Intro-Open-Refine.jpg)


# Introduction to Open Refine
OpenRefine is an open-source desktop application for data cleanup and transformation to other formats, an activity commonly known as data wrangling. It is similar to spreadsheet applications, and can handle spreadsheet file formats such as CSV, but it behaves more like a database.

----

## Setup Instructions
In preparation for this module, you will need to download and unzip the Open Refine package. The steps to do this are:

* Go to the [downloads page for Open Refine](https://openrefine.org/download.html)
* Click the Highlighted text that represents your operating system (If you are using windows and are unsure if you have java, choose the option that comes with Java)
* Save the file to your computer in a location that you have access to
* Unzip the file using your preferred zipping tool (right click on the folder and choose the program to unzip with like 7zip or WinZip)
(Optional) Make a shortcut on your desktop by opening the folder, right clicking openrefine.exe (blue gem symbol) and clicking "create shortcut" (you may need to move the new shortcut to your desktop manually depending on your operating system)

You will also need to download the dataset for the workshop by clicking [HERE](https://github.com/BrockDSL/Step-by-Step-guide-to-Open-Refine/blob/master/Open%20Refine%20Data%20Set.csv)

----
## What are Data Types?

Data type is an attribute associated with a piece of data that tells a computer system how to interpret its value. Understanding data types ensures that data is collected in the preferred format and the value of each property is as expected. Please click on the headings below to expand the title and know more about the different data types.

<iframe src="https://h5pstudio.ecampusontario.ca/h5p/42564/embed" width="993" height="537" frameborder="0" allowfullscreen="allowfullscreen"></iframe><script src="https://h5pstudio.ecampusontario.ca/modules/contrib/h5p/vendor/h5p/h5p-core/js/h5p-resizer.js" charset="UTF-8"></script>
----

## Take quiz to understand your knowledge of Data Types. 

<iframe src="https://h5pstudio.ecampusontario.ca/h5p/42567/embed" width="993" height="449" frameborder="0" allowfullscreen="allowfullscreen"></iframe><script src="https://h5pstudio.ecampusontario.ca/modules/contrib/h5p/vendor/h5p/h5p-core/js/h5p-resizer.js" charset="UTF-8"></script>

----

**Step 1: Create a project**

1.	In your browser for the OpenRefine tab, choose to create a project from and select “This Computer” under the **Get data from** heading. 
2.	Choose the file “Open Refine Data Set” that we downloaded during setup instructions and Click on Next. 

![Exploratory Analysis](1.jpg)

3.	Check the following boxes: “Attempt to parse cell text into numbers” and “Trim leading and trailing whitespace from strings” and click “Create Project”.

![Exploratory Analysis](1.1.jpg)

4.	You will see your project has been created. 

![Exploratory Analysis](1.2.jpg)

**Step 2: Remove Column**

Now we can see that the CSV format data has been converted into a table. But there are columns from the original data that we do not need, for example, the “COMMUTE_DISTANCE” element. We can delete that column by clicking the small triangle at the column name and choosing “Edit column” -> “Remove this column”.

![Exploratory Analysis](2.jpg)

**Step 3: Check duplicates**

1.	OpenRefine makes it very easy to check duplicates based on columns. Go to the “Customer Name” Column.  
2.	Click on the small triangle at the column name. Use “Facet” -> “Customized facets” -> “Duplicates facet”, we could see in the left-hand panel, that there are 7 duplicate items ( true)  in the “Customer Name” column. 
3.	Click on **true** to see the duplicates. 

![Exploratory Analysis](3.jpg)

4.	We will not be using duplicate data, so click on false. You will see 22 rows. We will be using these 22 rows for our further learning. 

![Exploratory Analysis](3.2.jpg)

**Step 4: Add columns and split string**

Now we will add another column using the “Customer Name” column. We would extract the first name and last name of the customer. To do that, we use the “General Refine Expression Language (GREL)” to implement splitting. Please follow the below-mentioned steps to add columns using split string:-

1.	Go to the “Customer Name” Column. Click on the small triangle at the column name. Use “Edit Column” -> “Add column based on this column”.
2.	A dialogue box will appear. Under the new column name, type: **Customer First Name**. 
3.	Make sure, on error is set to blank.
4.	Under the expression type: <mark> split(value,'')[0]</mark>
5.	Press “OK”
6.	You will see the new column name, **Customer First Name** is added right next to the “Customer Name” column. 

![Exploratory Analysis](4.jpg)

7.	Repeat steps 1 and 2, but for the new column name, type: **Customer Last Name**. 
8.	Under the expression type: <mark> split(value,' ')[1]</mark>
9.	Press “OK”
10.	You will see the new column name, **Customer Last Name** is added right next to the “Customer Name” column. 

![Exploratory Analysis](4.2.jpg)

11.	Now remove the column “ Customer Name”. 

![Exploratory Analysis](4.3.jpg)

**Step 5: Common transforms**

1.	Go to column “Province”, Click on the small triangle at the column name.
2.	OpenRefine allows for easy transformation by providing a set of functionalities under “Edit cell” -> “Common transforms”.
3.	Select **to uppercase** to make all the provinces in the capital. 

![Exploratory Analysis](5.jpg)

**Step 6: Delete rows with blank cells**

1.	We may want to remove the “bad values” or the “outliers”. 
2.	Go to the “Customer First Name” Column.  
3.	Click on the small triangle at the column name. Use “Facet” -> “Customized facets” -> “Facet by blank”, we could see a panel on the left-hand side, with a true and false value.  
4.	Click on **true** to see the rows with empty values. 
5.	We will not be using the empty data, so click on false. You will see 21 rows. 

![Exploratory Analysis](6.jpg)

** Step 7: Manually edit cell value**

OpenRefine’s automatic data cleaning and transform functionalities have been very useful so far. However, there are still places that need manual editing.

1.	Go to the column “VEHICLEMAKE”. You will see many values have * TRUCK/VAN* along with its brand, which does not make sense. So, we will manually remove the *TRUCK/VAN* from each cell. 
2.	We can edit individual cell values by moving the cursor to the cell to be edited and clicking “edit”. Remove TRUCK/VAN and press “Apply”. We do this until every cell is satisfactory.

![Exploratory Analysis](7.jpg)

**Step 8: Exploratory Analysis**

We could use OpenRefine to do some basic exploratory analysis. For example, we are interested in examining the year in which most vehicle belongs. Please follow the steps below for exploratory analysis. 
1.	Go to the “VEHICLEYEAR” Column. Click on the small triangle at the column name. Use “Sort”
2.	A dialogue box will appear, select **numbers** under sort cell values as and make sure the smallest first box is checked. 
3.	Press “OK”
4.	Go to the “VEHICLEYEAR” Column.  
5.	Click on the small triangle at the column name. Use “Facet” -> “Numeric Facet” to filter the records.

![Exploratory Analysis](8.jpg)

** Step 9: Export and share**

Finally, we have transformed a CSV format messy data into a nice table. We can export the resulting table into a variety of formats including Excel and use the “Permalink” in the left-upper part to share the workspace with others.

----

## Follow Up Material
Add in names of books, links to websites, or any other reccomendations for follow up materials that could represent the "Next Step" in an attendees learning after the workshop.  helpful links like the Programming Historians or W3Schools are good examples.

----
  
**End notes**
This is where you mention the DSL, MDGL, or Research Lifecycle department and put in contact information.  An example of what this might look like is:

**This workshop is brought to you by the Brock University Digital Scholarship Lab.  For a listing of our upcoming workshops go to [Experience BU](https://experiencebu.brocku.ca/organization/dsl) if you are a Brock affiliate or [Eventbrite page](https://www.eventbrite.ca/o/brock-university-digital-scholarship-lab-21661627350) for external attendees.  For additional inquiries, contact [DSL@Brocku.ca](mailto:DSL@Brocku.ca)**


