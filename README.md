# fetch-insideairbnb-data

Python tool that scrapes the [Inside Airbnb](https://insideairbnb.com/get-the-data/) data page and bulk-downloads the `listings.csv.gz` file for every city listed.

## Features

- Parses the download page with BeautifulSoup and groups files by city heading
- Resumable: compares local file size to the remote `Content-Length` and skips complete files
- Streamed downloads (1 MB chunks) with a polite delay between requests
- Optional `CITY_FILTER` and `MAX_FILES` settings for partial pulls

## Usage

```bash
pip install -r requirements.txt
jupyter notebook data.ipynb
```

Set `CITY_FILTER` (for example `"New York City"`) or `MAX_FILES` in the first cell to limit the download. Files land in `inside_airbnb_data/<City>/listings.csv.gz`.

## Data

The data (~2 GB across 100+ cities) is not committed. Re-run the notebook to fetch it. Data is published by Inside Airbnb under its own license; see their site for terms.
