# Data-Collection-Analysis-Model-Development

## List.am Real Estate Rentals Category Predictive Model Development

### Project Overview

This project aims to collect, cleanse, analyze, and model real estate data to gain valuable insights into the housing market. The core focus lies in residential properties such as apartments and houses.

### Key Steps and Explanations

#### Web Scraping

**Implementation:** The project utilizes asynchronous web scraping with aiohttp, asyncio, and BeautifulSoup to efficiently extract real estate listings from a target website. Custom functions like `scrape_page` and `fetch` handle the detailed data extraction and retrieval process.

**Data Extraction:** The scraper meticulously gathers essential details, including:
- Price
- Location
- Property Type (apartment, house)
- Descriptive Text
- Number of Rooms
- Square Footage (Area)
- Additional relevant attributes

#### Data Cleaning

**Data Loading:** The scraped data, stored in JSON format, is imported into a pandas DataFrame for seamless manipulation.

**Quality Assurance:** The cleaning process begins with a thorough check for missing values and potential duplicates. Strategies like `df.fillna(0)` and `df.drop_duplicates()` are applied to ensure data integrity.

#### Feature Engineering

**Insightful Feature Creation:** To enhance the analytical power of the dataset, new features are derived from the existing data:
- Property Type Inference: A function like `classify_property` intelligently categorizes listings into 'apartment', 'house', or other types based on their descriptions.
- Renovation Status: The description text is parsed to identify whether a property has undergone renovations.
- Area Calculations: Square footage is extracted from the description.
- Pricing: Numeric price is isolated, cleaned, and potentially converted between currencies if necessary.
- Room Estimation: When not explicitly listed, the number of rooms is estimated using square footage and property type.
- Family Size Suitability: Calculations determine the ideal number of occupants for each property.
- Single Occupancy Indicator: A flag is generated to identify properties best suited for single residents.

#### Data Transformation

**Consistency and Compatibility:**
- Missing values are consistently filled to avoid errors during analysis and modeling.
- Data types are carefully adjusted – for example, ensuring 'Num_Rooms' is represented as an integer. This prepares the data for seamless use in various statistical and machine learning techniques.

#### Data Encoding

**Machine Learning Ready:** Categorical variables (e.g., 'Location', 'Property_Type') are transformed using one-hot encoding. This step is crucial for making the dataset compatible with most machine-learning algorithms.

#### Data Reduction

**Streamlining the Model:** The code examines the dataset for:
- Features with extremely low variance that might provide little predictive value.
- Highly correlated features where redundancy could impact model performance.

**Techniques:** Strategies like thresholding variances or principal component analysis (PCA) might be employed to address these issues and optimize the feature space.

#### Handling Class Imbalance

**Balanced Representation:** If specific target outcomes (e.g., property price ranges) are disproportionately represented, techniques like undersampling (e.g., RandomUnderSampler) or oversampling can be employed to create a more balanced dataset. This helps prevent model bias.

#### Text Preprocessing

**Unlocking Textual Insights:** The 'Description' column holds valuable information. Using natural language processing (NLP):
- Tokenization: Descriptions are broken into individual words.
- Stop Word Removal: Common, less meaningful words are filtered out.
- Stemming/Lemmatization: Words are reduced to their root forms for better analysis.

**Applications:** This preprocessed text can be used for sentiment analysis, topic modeling, or as additional features in predictive models.
