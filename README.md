# Final Project Data Management: COVID-19 Analysis

## Project Description

This project aims to analyze COVID-19 data based on continents over time using PyMongoDB. The data used is sourced from [Kaggle](https://www.kaggle.com/code/michau96/covid-19-continents-in-relation-to-time/input). The project includes basic operations on a MongoDB database such as storing, reading, updating, and deleting data.

## Features

- Import and process COVID-19 dataset from a CSV file.
- Store data into a MongoDB database.
- Read data sorted by confirmed cases.
- Update incorrect data entries.
- Delete erroneous data to prevent duplication.

## Installation

### Prerequisites

Ensure that you have Python and pip installed on your system. You will also need to have MongoDB installed and running on localhost.

### Installing Dependencies

1. Clone this repository:
```
git clone https://github.com/notyouriiz/covid19-analysis.git
cd covid19-analysis
```


2. Install the required dependencies:
```
pip install pandas pymongo
```


3. Make sure MongoDB is running on localhost at port 27017.

## Usage

1. **Import Modules**
```
import pandas as pd
import pymongo
import json
```


2. **Connect to MongoDB and Load Dataset**
```
client = pymongo.MongoClient("mongodb://localhost:27017")
Report = pd.read_csv("covid19_data.csv")
```


3. **Create Database and Collection**
```
db = client["dbCovid19"]
collection = db["Covid19_report"]
collection.insert_many(data)
```


4. **Read Data**
```
for doc in collection.find({}).sort("Confirmed", pymongo.ASCENDING):
print(doc)
```


5. **Update Data**
```
collection.update_one({"Province": "Shanghai", "Confirmed": 20.0}, {"$set": {"Confirmed": 22.0}})
```


6. **Delete Data**
```
result = collection.delete_one({"Province": "Shanghai", "Last Update": "1/22/2020 17:00", "Confirmed": 22.0})
```


## Notes

The data used in this project is in CSV format and is processed into a DataFrame using Pandas before being stored in the MongoDB database with PyMongo.

## License

This project does not have a specific license, but you are free to use this code for educational or research purposes.

## Acknowledgments

Special thanks to [Kaggle](https://www.kaggle.com/) for providing the dataset and the Python community for their ongoing support in open-source development.

