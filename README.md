# British Airways Reviews Scraper

This Python script uses Scrapy and BeautifulSoup to scrape reviews of British Airways from [Airline Quality](https://www.airlinequality.com/airline-reviews/british-airways). 

## Overview

The script navigates through 38 pages, each containing 100 reviews, for a total of 3600 reviews. It scrapes the following information for each review:

- Date Published
- Rating Value
- Best Rating
- Header
- Author
- Review Body
- Recommendation
- Review Stats

The scraped data is then saved in a JSON file named `output.json`.

## Performance

The script is highly efficient, able to scrape all 3600 reviews in just under a minute.

## Usage

To run the script, simply run the jupyter notebook


Ensure that you have the necessary Python packages installed. You can install them using pip:

```bash
pip install -r requirements.txt
```

## Output

The output is a JSON file (`output.json`) with each review represented as a separate JSON object.

## Code

The main part of the script is the `ReviewsSpider` class, which defines how the scraping is done. It uses BeautifulSoup to parse the HTML and extract the necessary information.

The script also includes a main function that sets up and starts the Scrapy crawler process.

```python
if __name__ == "__main__":
    from scrapy.crawler import CrawlerProcess

    process = CrawlerProcess(settings={
        'USER_AGENT': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/58.0.3029.110 Safari/537.3',
        'FEED_FORMAT': 'json',
        'FEED_URI': 'output.json'
    })

    process.crawl(ReviewsSpider)
    process.start()
```

