# A3-hcds-hcc-bias
 Name: Ali Bektas <br>
 Date: 30 Nov 2020
 
 ### Goal
 ______________________________________
 
 The notebook in this repository contains the code to analyze bias in wikipedia articles about politicians. 
 
 ### Data sources: 
 
 - Wikipedia article data: https://figshare.com/articles/Untitled_Item/5513449
 - Population data: https://www.prb.org/international/indicator/population/table/
 - Wikimedia ORES API: https://www.mediawiki.org/wiki/ORES
 
 ### Resources used
 _____________________________________________
 
The environment dependencies can be installed via pip install -r requirements.txt. I recommend installing in a Conda environment running Python version 4.9.
 
https://www.python.org/downloads/release/python-373/

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
 
 > For some of article revision 
