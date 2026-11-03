# fetch-insideairbnb-data

A Python tool that bulk downloads the `listings.csv.gz` file for every city on [Inside Airbnb](https://insideairbnb.com/get-the-data/). It was built as the data collection step for the [Airbnb price prediction project](https://github.com/ethanbrownecon/Final-Project-Airbnb-Price-Prediction-Geospatial-Analysis).

## Why it exists

Inside Airbnb publishes one file per city, and pulling more than 100 of them by hand is slow and easy to get wrong. This notebook automates the download so a multi market dataset can be rebuilt on demand.

## Features

- Parses the download page with BeautifulSoup and groups files by city.
- Resumable: compares local file size to the remote `Content-Length` and skips complete files.
- Streams downloads in 1 MB chunks with a polite delay between requests.
- Optional `CITY_FILTER` and `MAX_FILES` settings for partial pulls.

## Usage

```bash
pip install -r requirements.txt
jupyter notebook data.ipynb
```

Set `CITY_FILTER` (for example `"New York City"`) or `MAX_FILES` in the first cell to limit the download. Files are saved to `inside_airbnb_data/<City>/listings.csv.gz`.

## Data

The data, about 2 GB across more than 100 cities, is not committed. Re-run the notebook to fetch it. Inside Airbnb publishes the data under its own license, so check its site for terms.
