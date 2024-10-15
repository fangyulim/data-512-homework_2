# data-512-homework_2
# DATA512_HW2
DATA 512 Homework 2: Considering Bias in Data

## Goal
  - The goal of this assignment is explore the concept of bias in data using Wikipedia articles of politicians around the world.     
  - The list of articles is determined in the politicians_by_country_AUG.2024.csv file.

## License:
 - [MediaWiki API](https://www.mediawiki.org/wiki/API:Main_page)
      - Creative Commons Attribution-ShareAlike 3.0 (CC-BY-SA 3.0) 
      - GNU Free Documentation License (GFDL) 
      - My dataset was created using the Wikimedia API, which is governed by their Terms of Use. By utilizing this data, you agree to comply with the attribution requirements specified by the CC-BY-SA license. Any adaptations or modifications of the dataset must be shared under a similar license. Care should be taken to respect user privacy and adhere to applicable data protection regulations. All interactions with the API should comply with its usage guidelines.

 - [politicians_by_country_AUG.2024.csv](politicians_by_country_AUG.2024.csv) 
      - Creative Commons (CC-BY license)

 - [population_by_country_AUG.2024.csv](population_by_country_AUG.2024.csv) 
      - Creative Commons (CC-BY license)
    
 - [wp_ores_liftwing_example.ipynb](wp_ores_liftwing_example.ipynb) 
      - This code example was developed by Dr. David W. McDonald for use in DATA 512, a course in the UW MS Data Science degree program. This code is provided under the [Creative Commons](https://creativecommons.org) [CC-BY license](https://creativecommons.org/licenses/by/4.0/). Revision 1.0 - August 15, 2023

 - [wp_page_info_example.ipynb](wp_page_info_example.ipynb) 
      - This code example was developed by Dr. David W. McDonald for use in DATA 512, a course in the UW MS Data Science degree program. This code is provided under the [Creative Commons](https://creativecommons.org) [CC-BY license](https://creativecommons.org/licenses/by/4.0/). Revision 1.2 - September 16, 2024
 
 - [Machine Learning/ LiftWing (ORES)](https://wikitech.wikimedia.org/wiki/Machine_Learning/LiftWing)
      - Creative Commons Attribution-ShareAlike 3.0 (CC-BY-SA 3.0) 
      - GNU Free Documentation License (GFDL) 
      - My dataset was created using the Wikimedia API, which is governed by their Terms of Use. By utilizing this data, you agree to comply with the attribution requirements specified by the CC-BY-SA license. Any adaptations or modifications of the dataset must be shared under a similar license. Care should be taken to respect user privacy and adhere to applicable data protection regulations. All interactions with the API should comply with its usage guidelines.

## Project Structure
project-main/ <br>
| <br>
|-- input_data/  
|   |-- [politicians_by_country_AUG.2024.csv](./input_data/politicians_by_country_AUG.2024.csv)  
|   |-- [population_by_country_AUG.2024.csv](./input_data/population_by_country_AUG.2024.csv)  
|-- intermediary_files/  
|   |-- [article_revisions.json](./intermediary_files/article_revisions.json)  
|   |-- [politicians_articles.json](./intermediary_files/polticians_articles.json)  
|   |-- [revision_p1.json](./intermediary_files/revision_p1.json)  
|   |-- [revision_p2.json](./intermediary_files/revision_p1.json)  
|   |-- [revision_p3.json](./intermediary_files/revision_p1.json)  
|   |-- [revision_p4.json](./intermediary_files/revision_p1.json)  
|-- module/  
|   |-- [DATA512_HW2_Analysis.ipynb](./module/DATA512_HW2_DataRetrieval.ipynb)  
|   |-- [DATA512_HW2_Analysis.ipynb](./module/DATA512_HW2_Analysis.ipynb)  
|-- output/  
|   |-- [wp_politicians_by_country.csv](./output/wp_politicians_by_country.csv)  
|   |-- [wp_countries-no_match.text](./output/wp_countries-no_match.txt)  
|-- reference_notebooks/  
|   |-- [wp_ores_liftwing_example.ipynb](./reference_notebooks/wp_ores_liftwing_example.ipynb)  
|   |-- [wp_page_info_example.ipynb](./reference_notebooks/wp_page_info_example.ipynb)  
|-- README.md  
|-- LICENSE  
|-- apikeys.zip   

## Intermediary files
  - [politicians_articles.json](./intermediary_files/polticians_articles.json) follow the following schema:
      It contains the page information for the articles of the politicians plus the country they represent. 

      **Schema**: 
        { "article_title" {"pageid": str,
                           "ns" : int,
                           "title": str,
                           "contentmodel": str,
                           "pagelanguage": str,
                           "pagelanguagedir": str,
                           "touched" : str,
                           "lastrevid": str,
                           "length": str,
                           "talkid": str,
                           "fullurl": str,
                           "editurl": str,
                           "canoicalurl": str,
                           "pages": str,
                           "Country": str}}
  - [article_revisions.json](./intermediary_files/article_revisions.json) , [revision_p1.json](./intermediary_files/revision_p1.json), [revision_p2.json](./intermediary_files/revision_p2.json), [revision_p3.json](./intermediary_files/revision_p3.json), [revision_p3.json](./intermediary_files/revision_p3.json) follow the same schema
      It contains the quality of the article

      **Schema** :
        where both lastrevid and quality and strings. 
        { "lastrevid" : "quality" }

## output files
  - [wp_countries-no_match.txt](./output/wp_countries-no_match.txt) 
      It contains the list of politcians that we did not obtain article reviews of
  - [wp_politcians_by_country.csv](./output/wp_politicians_by_country.csv)
      It contains the article title, country, revision_id, article_quality, population, and region.
      Headers: [article | title | country | revision_id | article_quality |  population | region]

## Issues/ To reproduce 
  - The API call takes a VERY long time. You might want to use a smaller subset
  - You will need to create your own record to store you API token before running the function to make an ORES API call. Please refer to the [DATA512_HW2_DataRetrieval.ipynb](./module/DATA512_HW2_DataRetrieval.ipynb) and [wp_ores_liftwing_example.ipynb](./reference_notebooks/wp_ores_liftwing_example.ipynb) for more information.
  - You will need a list of article titles. Please reference the [politicians_by_country_AUG.2024.csv](./input_data/politicians_by_country_AUG.2024.csv), or you might choose to scrape your own data. 
  - You might want to get more population data instead of using [population_by_country_AUG.2024.csv](./input_data/population_by_country_AUG.2024.csv)
  - In the current list of politicians, there are politicians who represent more than one country, I had the problem because I saved my data in dictionary format using article titles as keys, you might want to use a different key, or different data type.

## Installation Instructions
To run this project, you will need the following Python packages installed:
- json
- urllib.parse
- time 
- apikeys (please reference [wp_ores_liftwing_example.ipynb](./reference_notebooks/wp_ores_liftwing_example.ipynb) and [DATA512_HW2_DataRetrieval.ipynb](./module/DATA512_HW2_DataRetrieval.ipynb) for more information)

Python version: 3.11.9

## Reflections and Implications
From this assignment I learnt the importance of using try and except when making API calls. I also learned that it's better to run your code in chunks. You never know what will happen, your connection to the API call may be broken at any time and you wouldn't want to rerun everything as it takes too much time. 
Your data types are also important. I ran into the problem of missing articles as I had saved my data in a dictionary and had article titles as the keys. 

I was surprised that there were no articles about politicians in North America. I noticed that this was because there were no politicians from North America in the politicians_by_vountry_AUG.2024.csv file. I'm not sure why they were excluded because "American Politicians" was an option on the website where it was scrapped. On the other hand, even if there were American politicians, I believe we might not include it in our analysis due to inconsistent naming. I would assume these politicians to be labeled to be from "America", but in our population_by_country_AUG.2024.csv file, it was labeled as "United States", I can imagine some sources to label as "United States of America". A possible reason why I think American politicians were not included, is that the owner of the scrapped data used a different name for "America", likely "United States". Therefore, they did not get matching results. 

1. What biases did you expect to find in the data(before you started working with it), and why?
  - Wikipedia was founded in the United States and is open to contribution, and we were looking at articles in English for this assignment. With the primary user base being from Western countries, I had expected to find a lot more articles from Western politicians, and that the quality of these articles would be higher. I expected this as contributors may be more familiar with Western political contexts and issues resulting in higher quality articles. 

2. What (potential) sources of bias did you discover in the course of your data processing and analysis?
  - Not all the politicians that we observed are from the same period and population changes. Therefore, I question whether using the population information we have currently is an unbiased assessment to compare the quality of articles per capita. There is also a potential discrepancy in how countries are named, for example, South Korea could be named "South Korea" or "Korea (South)".

3. What might your results suggest about (English) Wikipedia as a data source?
  - (English) Wikipedia might not be the most reliable data source as it is open to contributors around the world. Everyone has different naming conventions and opinions thus the articles might inherit these opinions and biases. Users should read into the references provided if they want to ensure that they are obtaining the correct information. 