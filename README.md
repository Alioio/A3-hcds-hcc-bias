# Analysis of bias in Wikimedia politician data

 Name: Ali Bektaş <br>
 Date: 30 Nov 2020
 
 ### Goal
 ______________________________________
 
 The notebook in this repository contains the code to analyze existing bias in wikipedia articles about politicians. 
 
 ### Data sources: 
 
 - Wikipedia article data: https://figshare.com/articles/Untitled_Item/5513449
 - Population data: <a href="https://github.com/FUB-HCC/hcds-winter-2020/tree/main/assignments/A3_Bias/_data">_data folder of the assignments GitHub Repo</a>. Is originally drawn and edited from: https://www.prb.org/international/indicator/population/table/
 - Wikimedia ORES API: https://www.mediawiki.org/wiki/ORES
 
 ### Resources used
 _____________________________________________
 
The environment dependencies can be installed via pip install -r requirements.txt. I recommend installing in a Conda environment running Python version 3.7.

Documentation for Python can be found here: https://docs.python.org/3.7/
Documentation for Jupyter Notebook can be found here: https://jupyter.org/documentation

The following Python packages were used and their documentation can be found here: 

<ul>
 <li><a href="https://example.com">os</a></li>
 <li><a href="https://pandas.pydata.org/">pandas</a></li>
 <li><a href="https://numpy.org/doc/">numpy</a></li>
 <li><a href="https://altair-viz.github.io/">altair</a></li>
 </ul>

### The Objective Revision Evaluation Service <a href="https://www.mediawiki.org/wiki/ORES">(ORES)</a>

This API will be used to estimate the quality of the given Wikipedia article in the specific revision and to 
categorize it to one of the following categories: 
<ol>
<li> FA - Featured article
<li> GA - Good article
<li> B - B-class article
<li> C - C-class article
<li> Start - Start-class article
<li> Stub - Stub-class article
 </ol>
 
 > Some of article revision ORES API is not able to classify and returns an error. This is mainly due to that the API cannot find the the revision.For these articles 
 the quality column contains the enrty *Revision not found*
 
 ### Files created
 ------------------------------------
 
 This notbook creates two CSV file after processing as part of this analysis. 
 This files are located in the *\data_clean* folder in this repository. 
 
 Articles from some countries could not be anlysed because data from two different sources had to be merged in order to make 
 the analysis. The wikipedia and ORES data and the population data. There were countries wich were present in only one 
 of the two datasources. Therefore these countries had to be removed and were excluded from the analysis. These articles are listed 
 in the file *countries-no_match.csv*. Articles which were considered in the analysis are listed in the file *politicians_by_country.csv*.
 
 <ul>
 <li>\data_clean\politicians_by_country.csv <t> This file contains information about all articles where the 
 <li> \data_clean\countries-no_match.csv <t> This file lists all articles which were excluded for the analysis.
 </ul>
 
 <br>
 
 |  **name** | **datatype**  | **description**  |
|---|---|---|
|  page |  str | Name of the Wikipedia article  |
|  country | str  | The country the article is referenced to  |
|  rev_id | int64  |  The revision id of the article which is passed to the ORES API for retrieving the quality prediction |
|  quality | str  | The predicted quality of the article  |
|  population | float64  | Population of the country. (*partly in millions/ partly in thousands*)  |
|  region | str  | Region the the artile is referenced to  |

License
-------------------------------------------------

This assignment code is released under the MIT license. Data Source Licenses:

<ul>
 <li> Wikipedia data:  Figshare -CC BY 4.0
 <li> Population data: From assignments _data folder. Unspecified.
  <li> ORES API: licensed under CC
 </ul>
 
 Results
 ------------------------------------------
 
 
 Started with showing the top 10 countries articles per population. Here the distortion caused by the missalignment of the units 
 in which the population is represented in the population dataset is very significant.
 
![countries_top_10.png](https://github.com/Alioio/A3-hcds-hcc-bias/blob/main/data_clean/visualizations/countries_top_10.png)

Then continued with the bottom ten countries:

![countries_bot_10.png](https://github.com/Alioio/A3-hcds-hcc-bias/blob/main/data_clean/visualizations/countries_bot_10.png)

In the next step the propotion of total articles and articles rated with good quality is compared across countries. 
For the top 10... 

![countries_quality.png](https://github.com/Alioio/A3-hcds-hcc-bias/blob/main/data_clean/visualizations/countries_quality.png)

|region |	proption: population / #of politician articles |
|---|-----|
|	AFRICA	| 3.792972 |
|	LATIN AMERICA AND THE CARIBBEAN	|1.081425 |
|	OCEANIA	| 0.035234 |
|	ASIA	 | 23.732029 |
|	EUROPE	|29.282314 |
|	NORTHERN AMERICA |	0.510605 |

![regions_amount_articles.png](https://github.com/Alioio/A3-hcds-hcc-bias/blob/main/data_clean/visualizations/regions_amount_articles.png)

 |region |	total articles | high quality rated |total articles / high quality rated articles |
|---|-----|-----|-----|
|	AFRICA	                         | 6973.0 | 119.0 | 0.017066 |
|	LATIN AMERICA AND THE CARIBBEAN	|5347.0 | 76.0 | 0.014214 |
|	OCEANIA	                        | 3157.0 | 63.0| 0.019956 |
|	ASIA	                           | 11885.0 | 316.0| 0.026588	 |
|	EUROPE	                         |15994.0	 | 350.0 | 0.021883	 |
|	NORTHERN AMERICA                |	1950.0	 | 104.0	 | 0.053333	 |

![regions_quality.png](https://github.com/Alioio/A3-hcds-hcc-bias/blob/main/data_clean/visualizations/regions_quality.png)
