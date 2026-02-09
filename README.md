# GymRack-RankedSearch

## Overview

**Gym Rack is an interactive ranked-search website by Sarah Benkoussa**

This app distinguishes itself by offering a specialized service that ranks gyms based on human reviews web-scraped from Yelp, focusing on keywords that users input into a search bar. This tailored approach allows users to find gyms that excel in particular areas, such as cleanliness, equipment quality, or customer service. While there are numerous review aggregators and fitness apps available, few sites offer a similar combination of real-time, keyword-driven analysis with a focus exclusively on gym facilities. This method provides an advantage over traditional rating systems, which often do not account for the nuances of user feedback on specific aspects of gym services.

The first prototype involved a simple boolean search, where results were returned if they included exact words in a given query. The second prototype improved upon this by introducing a vector space model. I implemented cosine similarity along with SVD for a text-mining component. This converted both the query and documents (where each document included a gym’s name, description, and set of reviews) into vectors that could be compared in the same vector space. These techniques allowed me to search and retrieve ranked results based on a query. Information retrieval (IR) and text mining were addressed by cosine similarity and SVD. This site also intruduces a social aspect by using real yelp reviews in the dataset.

To further improve the project, I provided more visibility/information on how/why certain gyms are being ranked higher than others. To address this and give users a better understanding of results, I include a similarity % with each result, and ordered results based on descending similarity scores. This gives viewers more insight into similarity metrics and why gyms are being ranked or shown. Each search result also highlights a relevant Yelp review based on the query for the user.

## Key Concepts

- **Boolean Search:** was used in the preliminary prototype/proof of concept.
- **Basic text pre-processing:** (regex, tokenizing, stemming, deduplication, etc.) used to convert queries and documents into appropriate format.
- **Inverted Index:** used to facilitate more efficient full-text searches.
- **TF-IDF:** used as a weighting factor to help understand the relevance of a document to a user's search query.
- **Cosine:** similarity measure used for our information retrieval (IR) aspect of the project
- **Term-document matrix:** used to represent the relationship between terms and documents, which was needed for SVD.
- **SVD:** addressed the text-mining aspect of the project by allowing us to perform more advanced dimensionality reduction, information extraction, and noise reduction.

## Query Examples

Users input their query in the search bar and receive real-time results generated as they type. Each gym listed in the results can be clicked on, which opens the respective gym's website in a new tab.

### Query 1

**Input:** “clean boxing peace”

**Output:**

![Image](/backend/static/images/GR-query1.png)

*Newest iteration provides more explainability of results: similarity score and relevant reviews. The results are also now ranked by similarity. We see in this example that the old “boolean search” could only find one place fitting the description, while our new search can offer multiple options as well as ones that are more peaceful.*

### Query 2

**Input:** “I am looking for a gym that has a strong powerlifting focused coaching staff”

**Output:**

![Image](/backend/static/images/GR-query2.png)

*Newest iteration includes relevant reviews that involve words from the query input. Here we see that the old version struggled with sentence style query which the newest version accommodates for by using cosine similarity and SVD.*

### Query 3

**Input:** “lessons for zumba and pilates”

**Output:**

![Image](/backend/static/images/GR-query3.png)

*A gym search system should include all kinds of fitness, so the newest iteration now allows users to search different fitness types apart from weight training. In the newest version, this query's relevant reviews tend to include the word “pilates.”*

## Running locally

- Ensure that you have Python version 3.10 or above installed on your machine (ideally in a virtual environment). Some of the libraries and code used in the template are only compatible with Python versions 3.10 and above.
  
### Step 1: Set up a virtual environment

Create a virtual environment in Python.

Run `python -m venv <virtual_env_name>` in your project directory to create a new virtual environment, remember to change <virtual_env_name> to your preferred environment name.

### Step 2: Install dependencies

You need to install dependencies by running `python -m pip install -r requirements.txt` in the backend folder.

### Step 3: Modify init.json file

This project gives an init.json file with the scraped yelp data to see how app.py file reads data from the json file.
You could change data in this file along with the search code, but do not delete or change the name of the file. However, you can also create more json files for your own project.

## Command to run project locally

```flask run --host=0.0.0.0 --port=5000```

## Debugging Some Basic Errors

- After the build, wait a few seconds as the server will still be loading, especially for larger applications with a lot of setup
- Dockerfiles should generally not be edited.
- Sometimes, if a deployment doesn't work, checking the console will tell you what error it is. If it's a 401, then logging in and out should fix it.
- If it isn't a 401, first try checking the logs or container status. Check if the containers are alive or not, which could cause issues. If the containers are down, try stopping and starting them.
- If data isn't important, destroying and then cloning and re-building containers will usually fix the issue (assuming there's no logical error).
