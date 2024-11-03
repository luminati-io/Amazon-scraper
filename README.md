## Table of Contents

- [Free Amazon Scraper](#free-amazon-scraper)
   - [Prerequisites](#prerequisites)
   - [Quick Setup](#quick-setup)
   - [How to Scrape Amazon Data](#how-to-scrape-amazon-data)
   - [Output](#output)
- [Challenges When Scraping Amazon Data](#challenges-when-scraping-amazon-data)
- [Solution: Bright Data Amazon Scraper API](#solution-bright-data-amazon-scraper-api)
- [Amazon Scraper API in Action](#amazon-scraper-api-in-action)
   - [Customize Data Collection with API Parameters](#customize-data-collection-with-api-parameters)
   - [Amazon Product Data](#amazon-product-data)
   - [Amazon Reviews Data](#amazon-reviews-data)
   - [Amazon Products Search](#amazon-products-search)
   - [Amazon Sellers Info](#amazon-sellers-info)
   - [Amazon Products by Best Sellers](#amazon-products-by-best-sellers)
   - [Amazon Products by Category URL](#amazon-products-by-category-url)
   - [Amazon Products by Keyword](#amazon-products-by-keyword)
   - [Amazon Products Global Dataset](#amazon-products-global-dataset)
   - [Amazon Products Global Dataset - Discover by Category URL](#amazon-products-global-dataset---discover-by-category-url)
   - [Amazon Products Global Dataset - Discover by Keywords](#amazon-products-global-dataset---discover-by-keywords)


## Free Amazon Scraper
Use this free tool to extract Amazon product data directly from search results pages. Easily retrieve product titles, prices, ratings, reviews, and more with just a few simple steps.

### Prerequisites
- Python 3.11 or higher.
- Install the necessary dependencies (see steps below).

### Quick Setup
1. Open your terminal and navigate to this project’s directory.
2. Run the following command to install dependencies:
   
    ```bash
    pip install -r requirements.txt
    ```

### How to Scrape Amazon Data
To start scraping Amazon data, simply provide a search query. You can also specify the Amazon domain and the number of pages you want to scrape.

#### Command:
```bash
python main.py "<your_search_query>" --domain="<amazon_domain>" --pages=<number_of_pages>
```
- `<your_search_query>`: The search keywords (e.g., "coffee maker").
- `<amazon_domain>`: The Amazon domain you want to scrape (default: `com` for Amazon US).
- `<number_of_pages>`: Number of pages to scrape (optional, defaults to scraping all available pages).

#### Example:
To scrape data for "coffee maker" on the Amazon US domain and scrape the first 3 pages of results.
Here's the command:
```bash
python main.py "coffee maker" --domain="com" --pages=3
```
### Output
After scraping, the extracted data will be saved as `amazon_data.csv` in the project directory. The CSV file will include the following details:
- **Name:** Product title.
- **Current Price:** Product price (empty if out of stock).
- **Rating:** Average customer rating.
- **Reviews:** Total number of customer reviews.
- **ASIN:** Amazon Standard Identification Number.
- **Link:** Direct URL to the product page on Amazon.

Here's how the data will look:

<img width="700" alt="bright-data-amazon_csv_data" src="https://github.com/user-attachments/assets/1346f6f4-f85b-4708-b28b-f255166de907">

## Challenges When Scraping Amazon Data
Scraping Amazon data isn't always straightforward. Here are a few challenges that you might encounter:
1. **Advanced Anti-Bot Measures:** Amazon uses CAPTCHAs, invisible bot detection techniques, and behavioral analysis (like tracking mouse movements) to block bots.
2. **Frequent Page Structure Updates:** Amazon frequently changes its HTML structure, IDs, and class names, making it necessary to regular updates to scrapers to align with the new page layout.
3. **High Resource Consumption:** Scraping JavaScript-heavy pages with tools like Playwright or Selenium can consume significant system resources. Handling dynamic content and running multiple browser instances can slow down performance, especially when scraping large amounts of data.

Below is an example of what happens when Amazon detects automated scraping attempts:

<img src="https://github.com/user-attachments/assets/9e6061c7-ed1c-4296-afd4-0df385e06b2e" alt="Amazon Blocked" width="700"/>

As shown above, Amazon blocked the request to prevent further data scraping — a common issue that many scrapers encounter.

## Solution: Bright Data Amazon Scraper API
The [Bright Data Amazon Scraper API](https://brightdata.com/products/web-scraper/amazon) is the ultimate solution for scraping Amazon product data at scale. Here’s why:

- **No Infrastructure Management**: No need to handle proxies or unblocking systems.
- **Geo-Location Scraping**: Scrape from any geographical region.
- **Global IP Coverage**: Access over 72 million real user IPs in 195 countries with 99.99% uptime.
- **Flexible Data Delivery**: Get data via Amazon S3, Google Cloud, Azure, Snowflake, or SFTP in formats like JSON, NDJSON, CSV, and `.gz`.
- **Privacy Compliance**: Fully complies with GDPR, CCPA, and other data protection laws.
- **24/7 Support**: Dedicated support team is available around the clock to assist with any API-related questions or issues.

You also get **20 free API calls** to test the product and see how it fits your needs.

## Amazon Scraper API in Action

> For a detailed guide on setting up the Amazon Scraper API, check our [Step-by-Step Setup Guide](https://github.com/luminati-io/Amazon-scraper/blob/main/scraper_api_setup.md#amazon-reviews).

### Customize Data Collection with API Parameters

Use the following API parameters to customize your data collection:

| **Parameter**       | **Type**   | **Description**                                                                                   | **Example**                                           |
|---------------------|------------|---------------------------------------------------------------------------------------------------|-------------------------------------------------------|
| `limit`             | `integer`  | Limit the number of results returned for each input.                                            | `limit=10`                                           |
| `include_errors`    | `boolean`   | Include an error report in the output for troubleshooting.                                      | `include_errors=true`                                |
| `notify`            | `url`      | URL where a notification is sent once the collection completes.                                  | `notify=https://notify-me.com/`                      |
| `format`            | `enum`     | Format for data delivery. Supported formats: JSON, NDJSON, JSONL, CSV.                          | `format=json`                                        |

💡Additional delivery methods: You can choose to deliver the data via [webhook](https://docs.brightdata.com/scraping-automation/web-data-apis/web-scraper-api/overview#via-webhook) or through the [API](https://docs.brightdata.com/scraping-automation/web-data-apis/web-scraper-api/overview#via-api).

### Amazon Product Data
Collect detailed product data from Amazon by providing a product URL.

<img width="700" alt="bright-data-web-scraper-api-amazon-product-data" src="https://github.com/user-attachments/assets/6352b480-2918-41bf-b770-3d272397a429">

#### Key Input Parameters:
| Parameter | Type   | Description                    | Required |
|-----------|--------|--------------------------------|----------|
| `url`       | `string` | The Amazon product URL to scrape data | Yes      |

#### Performance:
- Average response time per input: 13 seconds

#### Sample Output Data:
Here’s an example of the output you will receive after scraping Amazon product data:
```json
{
    "url": "https://www.amazon.com/KitchenAid-Protective-Dishwasher-Stainless-8-72-Inch/dp/B07PZF3QS3",
    "title": "KitchenAid All Purpose Kitchen Shears with Protective Sheath...",
    "seller_name": "Amazon.com",
    "brand": "KitchenAid",
    "description": "These all-purpose shears from KitchenAid are a valuable addition...",
    "initial_price": 11.99,
    "final_price": 8.99,
    "currency": "USD",
    "availability": "In Stock",
    "reviews_count": 77557,
    "rating": 4.8,
    "categories": [
        "Home & Kitchen",
        "Kitchen & Dining",
        "Kitchen Utensils & Gadgets",
        "Shears"
    ],
    "asin": "B07PZF3QS3",
    "images": [
        "https://m.media-amazon.com/images/I/41E7ALk+uXL._AC_SL1200_.jpg",
        "https://m.media-amazon.com/images/I/710B9HpzMPL._AC_SL1500_.jpg"
    ],
    "delivery": [
        "FREE delivery Friday, October 25 on orders shipped by Amazon over $35",
        "Or fastest Same-Day delivery Today 10 AM - 3 PM. Order within 4 hrs 46 mins"
    ]
}
```
#### Code Example:
Below is a Python script that triggers the Amazon product data collection and stores the results in a JSON file:
```python
import json
import requests
import time


def trigger_datasets(api_token, dataset_id, datasets):
    headers = {
        "Authorization": f"Bearer {api_token}",
        "Content-Type": "application/json",
    }

    trigger_url = (
        f"https://api.brightdata.com/datasets/v3/trigger?dataset_id={dataset_id}"
    )

    # Sending API request to trigger dataset collection
    response = requests.post(trigger_url, headers=headers, data=json.dumps(datasets))

    if response.status_code == 200:
        print("Data collection triggered successfully!")
        snapshot_id = response.json().get("snapshot_id")
        return snapshot_id if snapshot_id else print("No snapshot ID returned.")
    else:
        print(f"Error: {response.status_code} - {response.text}")
        return None


def get_snapshot_data(api_token, snapshot_id):
    headers = {"Authorization": f"Bearer {api_token}"}
    snapshot_url = (
        f"https://api.brightdata.com/datasets/v3/snapshot/{snapshot_id}?format=json"
    )

    # Polling until the snapshot data is ready
    while True:
        time.sleep(10)
        response = requests.get(snapshot_url, headers=headers)

        if response.status_code == 200:
            return response.json()
        elif response.status_code == 202:
            print("Snapshot still processing... retrying.")
        else:
            print(f"Error: {response.status_code} - {response.text}")
            return None


def store_data(data, filename="amazon_products_data.json"):
    if data:
        with open(filename, "w") as file:
            json.dump(data, file, indent=4)
        print(f"Data saved in {filename}.")
    else:
        print("No data to store.")


if __name__ == "__main__":
    API_TOKEN = "YOUR_API_TOKEN"
    DATASET_ID = "gd_l7q7dkf244hwjntr0"

    datasets = [
        {
            "url": "https://www.amazon.com/Quencher-FlowState-Stainless-Insulated-Smoothie/dp/B0CRMZHDG8"
        },
        {
            "url": "https://www.amazon.com/KitchenAid-Protective-Dishwasher-Stainless-8-72-Inch/dp/B07PZF3QS3"
        },
        {
            "url": "https://www.amazon.com/TruSkin-Naturals-Vitamin-Topical-Hyaluronic/dp/B01M4MCUAF"
        },
    ]

    # Trigger dataset collection
    snapshot_id = trigger_datasets(API_TOKEN, DATASET_ID, datasets)

    if snapshot_id:
        # Retrieve the data once the snapshot is ready
        data = get_snapshot_data(API_TOKEN, snapshot_id)
        if data:
            store_data(data)
```
You can view the full output by downloading [this sample JSON file](https://github.com/luminati-io/Amazon-scraper/blob/main/output_data/amazon_products_data.json).

### Amazon Reviews Data
Collect Amazon reviews by providing the product URL along with specific parameters like time frames, keywords, and the number of reviews to scrape.

<img width="700" alt="bright-data-web-scraper-api-amazon-product-reviews" src="https://github.com/user-attachments/assets/27513388-ccfa-4b27-9515-e1662f0da457">


#### Key Input Parameters:
| **Parameter**       | **Type**  | **Description**                                                                 | **Required** |
|---------------------|-----------|---------------------------------------------------------------------------------|--------------|
| `url`               | `string`  | The Amazon product URL from which to scrape reviews.                             | Yes          |
| `days_range`        | `number`  | The number of past days to consider when collecting reviews (leave blank for no limit). | No           |
| `keyword`           | `string`  | Filter reviews by a specific keyword.                            | No           |
| `num_of_reviews`    | `number`  | The number of reviews to scrape (if not provided, it will scrape all available reviews). | No           |

#### Performance:
- Average response time per input: 1 minute 1 second

#### Sample Output Data:
Here’s an example of the output you’ll receive when scraping Amazon reviews:
```json
{
    "url": "https://www.amazon.com/RORSOU-R10-Headphones-Microphone-Lightweight/dp/B094NC89P9/",
    "product_name": "RORSOU R10 On-Ear Headphones with Microphone...",
    "product_rating": 4.5,
    "product_rating_object": {
        "one_star": 386,
        "two_star": 237,
        "three_star": 584,
        "four_star": 1493,
        "five_star": 7630
    },
    "rating": 5,
    "author_name": "Amazon Customer",
    "review_header": "Great Sound For the Price!",
    "review_text": "I bought these headphones twice...",
    "badge": "Verified Purchase",
    "review_posted_date": "September 7, 2024",
    "helpful_count": 3
}
```
#### Code Example:
Below is a Python script that triggers the Amazon review data collection and stores the results in a JSON file:
```python
import json
import requests
import time


def trigger_datasets(api_token, dataset_id, datasets):
    headers = {
        "Authorization": f"Bearer {api_token}",
        "Content-Type": "application/json",
    }

    trigger_url = (
        f"https://api.brightdata.com/datasets/v3/trigger?dataset_id={dataset_id}"
    )

    # Sending API request to trigger dataset collection
    response = requests.post(trigger_url, headers=headers, data=json.dumps(datasets))

    if response.status_code == 200:
        print("Data collection triggered successfully!")
        snapshot_id = response.json().get("snapshot_id")
        return snapshot_id if snapshot_id else print("No snapshot ID returned.")
    else:
        print(f"Error: {response.status_code} - {response.text}")
        return None


def get_snapshot_data(api_token, snapshot_id):
    headers = {"Authorization": f"Bearer {api_token}"}
    snapshot_url = (
        f"https://api.brightdata.com/datasets/v3/snapshot/{snapshot_id}?format=json"
    )

    # Polling until the snapshot data is ready
    while True:
        time.sleep(10)
        response = requests.get(snapshot_url, headers=headers)

        if response.status_code == 200:
            return response.json()
        elif response.status_code == 202:
            print("Snapshot still processing... retrying.")
        else:
            print(f"Error: {response.status_code} - {response.text}")
            return None


def store_data(data, filename="amazon_reviews_data.json"):
    if data:
        with open(filename, "w") as file:
            json.dump(data, file, indent=4)
        print(f"Data saved in {filename}.")
    else:
        print("No data to store.")


if __name__ == "__main__":
    API_TOKEN = "YOUR_API_TOKEN"
    DATASET_ID = "gd_le8e811kzy4ggddlq"

    datasets = [
        {
            "url": "https://www.amazon.com/RORSOU-R10-Headphones-Microphone-Lightweight/dp/B094NC89P9/",
            "days_range": 0,
            "num_of_reviews": 4,
            "keyword": "great",
        },
        {
            "url": "https://www.amazon.com/Solar-Eclipse-Glasses-Certified-Viewing/dp/B08GB3QC1H",
            "days_range": 0,
            "num_of_reviews": 4,
            "keyword": "",
        },
    ]

    # Trigger dataset collection
    snapshot_id = trigger_datasets(API_TOKEN, DATASET_ID, datasets)

    if snapshot_id:
        # Retrieve the data once the snapshot is ready
        data = get_snapshot_data(API_TOKEN, snapshot_id)
        if data:
            store_data(data)
```
You can view the full output by downloading [this sample JSON file](https://github.com/luminati-io/Amazon-scraper/blob/main/output_data/amazon_reviews_data.json).

### Amazon Products Search
Discover Amazon products by providing a keyword for your search.

<img width="700" alt="bright-data-web-scraper-api-keyword-search" src="https://github.com/user-attachments/assets/3f5b3539-e222-470c-a6ee-fb92f83f7ecb">

#### Key Input Parameters:
| Parameter         | Type    | Description                                 | Required |
|-------------------|---------|---------------------------------------------|----------|
| `keyword`         | string  | The keyword used to search for products      | Yes      |
| `url`             | string  | The domain URL to search within              | Yes      |
| `pages_to_search` | number  | The number of pages to search through        | No       |

#### Performance:
- Average response time per input: 1 second

#### Sample Output Data:
Here’s an example of the output you’ll receive after performing a keyword search for products on Amazon:
```json
{
    "asin": "B08H75RTZ8",
    "url": "https://www.amazon.com/Microsoft-Xbox-Gaming-Console-video-game/dp/B08H75RTZ8/ref=sr_1_1",
    "name": "Xbox Series X 1TB SSD Console - Includes Xbox Wireless Controller...",
    "sponsored": "false",
    "initial_price": 479,
    "final_price": 479,
    "currency": "USD",
    "sold": 2000,
    "rating": 4.8,
    "num_ratings": 28675,
    "variations": null,
    "badge": null,
    "brand": null,
    "delivery": ["FREE delivery"],
    "keyword": "X-box",
    "image": "https://m.media-amazon.com/images/I/616klipzdtL._AC_UY218_.jpg",
    "domain": "https://www.amazon.com/",
    "bought_past_month": 2000,
    "page_number": 1,
    "rank_on_page": 1,
    "timestamp": "2024-10-20T10:39:37.679Z",
    "input": {
        "keyword": "X-box",
        "url": "https://www.amazon.com",
        "pages_to_search": 1
    }
}
```
#### Code Example:
Below is a Python script that triggers an Amazon product search based on a keyword and stores the results in a JSON file:
```python
import json
import requests
import time


def trigger_datasets(api_token, dataset_id, datasets):
    headers = {
        "Authorization": f"Bearer {api_token}",
        "Content-Type": "application/json",
    }

    trigger_url = (
        f"https://api.brightdata.com/datasets/v3/trigger?dataset_id={dataset_id}"
    )

    # Sending API request to trigger dataset collection
    response = requests.post(trigger_url, headers=headers, data=json.dumps(datasets))

    if response.status_code == 200:
        print("Data collection triggered successfully!")
        snapshot_id = response.json().get("snapshot_id")
        return snapshot_id if snapshot_id else print("No snapshot ID returned.")
    else:
        print(f"Error: {response.status_code} - {response.text}")
        return None


def get_snapshot_data(api_token, snapshot_id):
    headers = {"Authorization": f"Bearer {api_token}"}
    snapshot_url = (
        f"https://api.brightdata.com/datasets/v3/snapshot/{snapshot_id}?format=json"
    )

    # Polling until the snapshot data is ready
    while True:
        response = requests.get(snapshot_url, headers=headers)

        if response.status_code == 200:
            return response.json()
        elif response.status_code == 202:
            print("Snapshot still processing... retrying.")
        else:
            print(f"Error: {response.status_code} - {response.text}")
            return None
        time.sleep(10)


def store_data(data, filename="amazon_keywords_data.json"):
    if data:
        with open(filename, "w") as file:
            json.dump(data, file, indent=4)
        print(f"Data saved in {filename}.")
    else:
        print("No data to store.")


if __name__ == "__main__":
    API_TOKEN = "YOUR_API_TOKEN"
    DATASET_ID = "gd_lwdb4vjm1ehb499uxs"

    datasets = [
        {"keyword": "X-box", "url": "https://www.amazon.com", "pages_to_search": 1},
        {"keyword": "PS5", "url": "https://www.amazon.de"},
        {
            "keyword": "car cleaning kit",
            "url": "https://www.amazon.es",
            "pages_to_search": 4,
        },
    ]

    # Trigger dataset collection
    snapshot_id = trigger_datasets(API_TOKEN, DATASET_ID, datasets)

    if snapshot_id:
        # Retrieve the data once the snapshot is ready
        data = get_snapshot_data(API_TOKEN, snapshot_id)
        if data:
            store_data(data)
```
You can view the full output by downloading [this sample JSON file](https://github.com/luminati-io/Amazon-scraper/blob/main/output_data/amazon_keywords_data.json).

### Amazon Sellers Info
Discover detailed information about Amazon sellers by providing their specific seller URL.

<img width="700" alt="bright-data-web-scraper-api-seller-info" src="https://github.com/user-attachments/assets/c2bb725e-8598-4498-85d6-97052018e17a">


#### Key Input Parameters:
| **Parameter** | **Type**  | **Description**                    | **Required** |
|---------------|-----------|------------------------------------|--------------|
| `url`         | `string`  | The Amazon seller URL              | Yes          |

#### Performance:
- Average response time per input: 1 second

#### Sample Output Data:
Below is an example of the output you will receive after scraping seller information:
```json
{
    "input": {
        "url": "https://www.amazon.com/sp?seller=A33W53J5GVPZ8K"
    },
    "seller_id": "A33W53J5GVPZ8K",
    "seller_name": "Peckomatic",
    "description": "Peckomatic is committed to providing each customer with the highest standard of customer service.",
    "detailed_info": [
        {"title": "Business Name"},
        {"title": "Business Address"}
    ],
    "stars": "4.5 out of 5 stars",
    "feedbacks": [
        {
            "date": "By Kao y. on November 16, 2021.",
            "stars": "5 out of 5 stars",
            "text": "It say not to exceed 10lbs total but I did anyway. My bird was 8lbs + the 3lb box = 11lbs. Bird arrived in great condition."
        },
        {
            "date": "By JL on June 9, 2021.",
            "stars": "1 out of 5 stars",
            "text": "How this seller packages its items is not acceptable..."
        }
    ],
    "rating_positive": "89%",
    "feedbacks_percentages": {
        "star_5": "80%",
        "star_4": "9%",
        "star_3": "7%",
        "star_2": "0%",
        "star_1": "5%"
    },
    "products_link": "https://www.amazon.com/s?me=A33W53J5GVPZ8K",
    "buisness_name": "Francis Kunnumpurath",
    "buisness_address": "2612 State Route 80, Lafayette, NY, 13084, US",
    "rating_count_lifetime": 44,
    "country": "US"
}
```

#### Code Example:
Here’s a Python script that triggers the collection of Amazon seller data and stores the results in a JSON file:
```python
import json
import requests
import time


def trigger_datasets(api_token, dataset_id, datasets):
    headers = {
        "Authorization": f"Bearer {api_token}",
        "Content-Type": "application/json",
    }

    trigger_url = (
        f"https://api.brightdata.com/datasets/v3/trigger?dataset_id={dataset_id}"
    )

    # Sending API request to trigger dataset collection
    response = requests.post(trigger_url, headers=headers, data=json.dumps(datasets))

    if response.status_code == 200:
        print("Data collection triggered successfully!")
        snapshot_id = response.json().get("snapshot_id")
        return snapshot_id if snapshot_id else print("No snapshot ID returned.")
    else:
        print(f"Error: {response.status_code} - {response.text}")
        return None


def get_snapshot_data(api_token, snapshot_id):
    headers = {"Authorization": f"Bearer {api_token}"}
    snapshot_url = (
        f"https://api.brightdata.com/datasets/v3/snapshot/{snapshot_id}?format=json"
    )

    # Polling until the snapshot data is ready
    while True:
        response = requests.get(snapshot_url, headers=headers)

        if response.status_code == 200:
            return response.json()
        elif response.status_code == 202:
            print("Snapshot still processing... retrying.")
        else:
            print(f"Error: {response.status_code} - {response.text}")
            return None
        time.sleep(10)


def store_data(data, filename="amazon_seller_data.json"):
    if data:
        with open(filename, "w") as file:
            json.dump(data, file, indent=4)
        print(f"Data saved in {filename}.")
    else:
        print("No data to store.")


if __name__ == "__main__":
    API_TOKEN = "API_TOKEN"
    DATASET_ID = "gd_lhotzucw1etoe5iw1k"

    # Define the dataset with seller URLs
    datasets = [
        {"url": "https://www.amazon.com/sp?seller=A33W53J5GVPZ8K"},
        {"url": "https://www.amazon.com/sp?seller=A33YXLPENB0JBD"},
        {"url": "https://www.amazon.com/sp?seller=A33ZG27WW2U3E6"},
    ]

    # Trigger dataset collection
    snapshot_id = trigger_datasets(API_TOKEN, DATASET_ID, datasets)

    if snapshot_id:
        # Retrieve the data once the snapshot is ready
        data = get_snapshot_data(API_TOKEN, snapshot_id)
        if data:
            store_data(data)
```

You can view the full output by downloading [this sample JSON file](https://github.com/luminati-io/Amazon-scraper/blob/main/output_data/amazon_seller_data.json).

### Amazon Products by Best Sellers
Discover top-selling products on Amazon by providing the URL for the Best Sellers category.

<img width="700" alt="bright-data-web-scraper-api-amazon-best-sellers" src="https://github.com/user-attachments/assets/82f8c98e-3050-4d5e-a3be-24ebae8f7fc9">


#### Key Input Parameters:

| Parameter       | Type     | Description                                    | Required |
|-----------------|----------|------------------------------------------------|----------|
| `category_url`  | `string` | The Best Sellers category URL from which to scrape | Yes      |

#### Performance:
- Average response time per input: 6 minutes 49 seconds

#### Sample Output Data:
Here’s an example of the output you will receive after scraping Amazon’s Best Sellers data:

```json
{
    "title": "Amazon Basics Multipurpose Copy Printer Paper, 8.5\" x 11\", 1 Ream, 500 Sheets, White",
    "seller_name": "Amazon.com",
    "brand": "Amazon Basics",
    "initial_price": 9.99,
    "final_price": 7.41,
    "currency": "USD",
    "availability": "In Stock",
    "reviews_count": 178695,
    "rating": 4.8,
    "categories": [
        "Office Products",
        "Paper",
        "Copy & Multipurpose Paper"
    ],
    "asin": "B01FV0F8H8",
    "buybox_seller": "Amazon.com",
    "discount": "-26%",
    "root_bs_rank": 1,
    "url": "https://www.amazon.com/AmazonBasics-Multipurpose-Copy-Printer-Paper/dp/B01FV0F8H8?th=1&psc=1",
    "image_url": "https://m.media-amazon.com/images/I/81x0cTHWQJL._AC_SL1500_.jpg",
    "delivery": [
        "FREE delivery Friday, October 25",
        "Same-Day delivery Today 10 AM - 3 PM"
    ],
    "features": [
        "1 ream (500 sheets) of 8.5 x 11 white copier and printer paper",
        "Works with laser/inkjet printers, copiers, and fax machines",
        "Smooth 20lb weight paper for consistent ink and toner distribution"
    ],
    "bought_past_month": 100000,
    "root_bs_category": "Office Products",
    "bs_category": "Copy & Multipurpose Paper",
    "bs_rank": 1,
    "amazon_choice": true,
    "badge": "Amazon's Choice",
    "seller_url": "https://www.amazon.com/sp?ie=UTF8&seller=ATVPDKIKX0DER&asin=B01FV0F8H8",
    "timestamp": "2024-10-20T13:30:56.666Z"
}
```
#### Code Example:
Below is a Python script that triggers the collection of Amazon Best Sellers data and stores the results in a JSON file:
```python
import json
import requests
import time


def trigger_datasets(api_token, dataset_id, datasets):
    headers = {
        "Authorization": f"Bearer {api_token}",
        "Content-Type": "application/json",
    }

    trigger_url = f"https://api.brightdata.com/datasets/v3/trigger?dataset_id={dataset_id}&type=discover_new&discover_by=best_sellers_url&limit_per_input=3"

    # Sending API request to trigger dataset collection
    response = requests.post(trigger_url, headers=headers, data=json.dumps(datasets))

    if response.status_code == 200:
        print("Data collection triggered successfully!")
        snapshot_id = response.json().get("snapshot_id")
        return snapshot_id if snapshot_id else print("No snapshot ID returned.")
    else:
        print(f"Error: {response.status_code} - {response.text}")
        return None


def get_snapshot_data(api_token, snapshot_id):
    headers = {"Authorization": f"Bearer {api_token}"}
    snapshot_url = (
        f"https://api.brightdata.com/datasets/v3/snapshot/{snapshot_id}?format=json"
    )

    # Polling until the snapshot data is ready
    while True:
        time.sleep(10)
        response = requests.get(snapshot_url, headers=headers)

        if response.status_code == 200:
            return response.json()
        elif response.status_code == 202:
            print("Snapshot still processing... retrying.")
        else:
            print(f"Error: {response.status_code} - {response.text}")
            return None


def store_data(data, filename="amazon_bestsellers_data.json"):
    if data:
        with open(filename, "w") as file:
            json.dump(data, file, indent=4)
        print(f"Data saved in {filename}.")
    else:
        print("No data to store.")


if __name__ == "__main__":
    API_TOKEN = "YOUR_API_TOKEN"
    DATASET_ID = "gd_l7q7dkf244hwjntr0"

    datasets = [
        {
            "category_url": "https://www.amazon.com/gp/bestsellers/office-products/ref=pd_zg_ts_office-products"
        },
    ]

    # Trigger dataset collection
    snapshot_id = trigger_datasets(API_TOKEN, DATASET_ID, datasets)

    if snapshot_id:
        # Retrieve the data once the snapshot is ready
        data = get_snapshot_data(API_TOKEN, snapshot_id)
        if data:
            store_data(data)
```
You can view the full output by downloading [this sample JSON file](https://github.com/luminati-io/Amazon-scraper/blob/main/output_data/amazon_bestsellers.json).

### Amazon Products by Category URL
Discover and collect Amazon product data by providing a specific category URL. Customize your search with sorting options and location-based filters.

<img width="700" alt="bright-data-web-scraper-api-discover-by-category-url" src="https://github.com/user-attachments/assets/fe0c08d4-15ac-4f59-bc54-5dc9e9b74df7">

#### Key Input Parameters:
| **Parameter** | **Type**  | **Description**                              | **Required** |
|---------------|-----------|----------------------------------------------|--------------|
| `url`         | `string`  | The category URL to scrape products from      | Yes          |
| `sort_by`     | `string`  | Criteria for sorting the product results      | No           |
| `zipcode`     | `string`  | Zip code for location-specific product results| No           |

#### Performance:
- Average response time per input: 16 minutes 16 seconds

#### Sample Output Data:
Below is an example of the data you’ll receive after scraping products from a specified category:
```json
{
    "title": "Quilted Makeup Bag Floral Makeup Bag Cotton Makeup Bag",
    "brand": "WYJ",
    "price": 9.99,
    "currency": "USD",
    "availability": "In Stock",
    "rating": 5,
    "reviews_count": 1,
    "categories": [
        "Beauty & Personal Care",
        "Cosmetic Bags"
    ],
    "asin": "B0DC3WX7RM",
    "seller_name": "yisenshangmaoyouxiangongsi",
    "number_of_sellers": 1,
    "url": "https://www.amazon.com/WYJ-Quilted-Coquette-Aesthetic-Blue/dp/B0DC3WX7RM",
    "image_url": "https://m.media-amazon.com/images/I/71SI04tB6QL._AC_SL1500_.jpg",
    "product_dimensions": "8.7\"L x 2.8\"W x 5.1\"H",
    "item_weight": "2.5 Ounces",
    "variations": [
        {
            "name": "Pink",
            "asin": "B0DC3RKYPF",
            "price": 9.99
        },
        {
            "name": "Blue",
            "asin": "B0DC3WX7RM",
            "price": 9.99
        },
        {
            "name": "Purple",
            "asin": "B0DC47CDDT",
            "price": 9.99
        }
    ],
    "badge": "#1 New Release",
    "top_review": "I love everything about this bag! It's made well and a good size. Super cute!"
}
```

#### Code Example:
Below is a Python script that triggers the collection of products from a specified category URL and stores the data in a JSON file:
```python
import json
import requests
import time


def trigger_datasets(api_token, dataset_id, datasets):
    headers = {
        "Authorization": f"Bearer {api_token}",
        "Content-Type": "application/json",
    }

    trigger_url = f"https://api.brightdata.com/datasets/v3/trigger?dataset_id={dataset_id}&type=discover_new&discover_by=category_url&limit_per_input=4"

    # Sending API request to trigger dataset collection
    response = requests.post(trigger_url, headers=headers, data=json.dumps(datasets))

    if response.status_code == 200:
        print("Data collection triggered successfully!")
        snapshot_id = response.json().get("snapshot_id")
        return snapshot_id if snapshot_id else print("No snapshot ID returned.")
    else:
        print(f"Error: {response.status_code} - {response.text}")
        return None


def get_snapshot_data(api_token, snapshot_id):
    headers = {"Authorization": f"Bearer {api_token}"}
    snapshot_url = (
        f"https://api.brightdata.com/datasets/v3/snapshot/{snapshot_id}?format=json"
    )

    # Polling until the snapshot data is ready
    while True:
        response = requests.get(snapshot_url, headers=headers)

        if response.status_code == 200:
            return response.json()
        elif response.status_code == 202:
            print("Snapshot still processing... retrying.")
        else:
            print(f"Error: {response.status_code} - {response.text}")
            return None
        time.sleep(10)


def store_data(data, filename="amazon_bestsellers_data.json"):
    if data:
        with open(filename, "w") as file:
            json.dump(data, file, indent=4)
        print(f"Data saved in {filename}.")
    else:
        print("No data to store.")


if __name__ == "__main__":
    API_TOKEN = "YOUR_API_TOKEN"
    DATASET_ID = "gd_l7q7dkf244hwjntr0"

    datasets = [
        {
            "url": "https://www.amazon.com/s?i=luggage-intl-ship",
            "sort_by": "Best Sellers",
            "zipcode": "10001",
        },
        {
            "url": "https://www.amazon.com/s?i=baby-products-intl-ship",
            "sort_by": "Avg. Customer Review",
            "zipcode": "",
        },
        {
            "url": "https://www.amazon.com/s?rh=n%3A16225012011&fs=true&ref=lp_16225012011_sar",
            "sort_by": "Price: Low to High",
            "zipcode": "",
        },
    ]

    # Trigger dataset collection
    snapshot_id = trigger_datasets(API_TOKEN, DATASET_ID, datasets)

    if snapshot_id:
        # Retrieve the data once the snapshot is ready
        data = get_snapshot_data(API_TOKEN, snapshot_id)
        if data:
            store_data(data)
```

You can view the full output by downloading [this sample JSON file](https://github.com/luminati-io/Amazon-scraper/blob/main/output_data/amazon_discover_by_category_url.json).

### Amazon Products by Keyword
Discover products by using specific keywords.

<img width="700" alt="bright-data-web-scraper-api-discover-by-keyword" src="https://github.com/user-attachments/assets/4c57fb02-90c4-4c19-94ee-c5800201f3c3">

#### Key Input Parameters:
| **Parameter** | **Type**  | **Description**                   | **Required** |
|---------------|-----------|-----------------------------------|--------------|
| `keyword`     | `string`  | The keyword to search for products | Yes          |

#### Performance:
- Average response time per input: 2 minutes 46 seconds

#### Sample Output Data:
Here’s an example of the output you will receive after searching for products using a keyword:

```json
{
    "title": "SYLVANIA ECO LED Light Bulb, A19 60W Equivalent, 750 Lumens, 2700K, Non-Dimmable, Frosted, Soft White - 8 Count (Pack of 1)",
    "brand": "LEDVANCE",
    "seller_name": "Amazon.com",
    "initial_price": 13.99,
    "final_price": 12.12,
    "currency": "USD",
    "discount": "-13%",
    "rating": 4.7,
    "reviews_count": 48418,
    "availability": "In Stock",
    "url": "https://www.amazon.com/Sylvania-40821-Equivalent-Efficient-Temperature/dp/B08FRSS4BF",
    "image_url": "https://m.media-amazon.com/images/I/81wKhRO66oL._AC_SL1500_.jpg",
    "delivery": [
        "FREE delivery Friday, October 25 on orders shipped by Amazon over $35",
        "Or Prime members get FREE delivery Tomorrow, October 21. Order within 8 hrs 8 mins. Join Prime"
    ],
    "features": [
        "60W Incandescent Replacement Bulb - 750 Lumens",
        "Long-lasting – 7 years lifespan",
        "Energy-saving – Estimated energy cost of $1.08 per year"
    ],
    "discovery_input": {
        "keyword": "light bulb"
    },
    "input": {
        "url": "https://www.amazon.com/Sylvania-40821-Equivalent-Efficient-Temperature/dp/B08FRSS4BF"
    }
}
```
#### Code Example:
Below is a Python script that triggers the collection of Amazon products based on a keyword and stores the results in a JSON file:
```python
import json
import requests
import time


def trigger_datasets(
    api_token, dataset_id, datasets, dataset_type="discover_new", discover_by="keyword"
):
    headers = {
        "Authorization": f"Bearer {api_token}",
        "Content-Type": "application/json",
    }

    trigger_url = f"https://api.brightdata.com/datasets/v3/trigger?dataset_id={dataset_id}&type={dataset_type}&discover_by={discover_by}"

    # Sending API request to trigger dataset collection
    response = requests.post(trigger_url, headers=headers, data=json.dumps(datasets))

    if response.status_code == 200:
        print("Data collection triggered successfully!")
        snapshot_id = response.json().get("snapshot_id")
        return snapshot_id if snapshot_id else print("No snapshot ID returned.")
    else:
        print(f"Error: {response.status_code} - {response.text}")
        return None


def get_snapshot_data(api_token, snapshot_id):
    headers = {"Authorization": f"Bearer {api_token}"}
    snapshot_url = (
        f"https://api.brightdata.com/datasets/v3/snapshot/{snapshot_id}?format=json"
    )

    # Polling until the snapshot data is ready
    while True:
        response = requests.get(snapshot_url, headers=headers)

        if response.status_code == 200:
            return response.json()
        elif response.status_code == 202:
            print("Snapshot still processing... retrying.")
        else:
            print(f"Error: {response.status_code} - {response.text}")
            return None
        time.sleep(10)


def store_data(data, filename="amazon_keyword_data.json"):
    if data:
        with open(filename, "w") as file:
            json.dump(data, file, indent=4)
        print(f"Data saved in {filename}.")
    else:
        print("No data to store.")


if __name__ == "__main__":
    API_TOKEN = "API_TOKEN"
    DATASET_ID = "gd_l7q7dkf244hwjntr0"

    # Define the dataset with keywords
    datasets = [{"keyword": "light bulb"}, {"keyword": "dog toys"}]

    # Trigger dataset collection
    snapshot_id = trigger_datasets(API_TOKEN, DATASET_ID, datasets)

    if snapshot_id:
        # Retrieve the data once the snapshot is ready
        data = get_snapshot_data(API_TOKEN, snapshot_id)
        if data:
            store_data(data)
```

You can view the full output by downloading [this sample JSON file](https://github.com/luminati-io/Amazon-scraper/blob/main/output_data/amazon_keyword_data.json).

### Amazon Products Global Dataset
Collect product data across all major Amazon domains by providing a URL.

<img width="700" alt="bright-data-web-scraper-api-amazon-product-global-dataset" src="https://github.com/user-attachments/assets/f6aa9161-c519-4f58-bef4-ffea9c96b306">


#### Key Input Parameters:
| **Parameter** | **Type**  | **Description**           | **Required** |
|---------------|-----------|---------------------------|--------------|
| `url`         | `string`  | The Amazon product URL     | Yes          |

#### Performance:
- **Average response time per input**: Less than 1 second

#### Sample Output Data:
Here’s an example of the output you will receive after collecting product data:

```json
{
    "title": "Toys of Wood Oxford Wooden Stacking Rings – Learning to Count – Counting Game with 45 Rings – Wooden Toy for Ages 3 and Above",
    "brand": "Toys of Wood Oxford",
    "seller_name": "Toys of Wood Oxford",
    "initial_price": 23.99,
    "currency": "EUR",
    "final_price": 23.99,
    "availability": "Only 20 left in stock.",
    "rating": 4.5,
    "reviews_count": 1677,
    "asin": "B078TNNZK3",
    "url": "https://www.amazon.de/dp/B078TNNZK3?th=1&psc=1",
    "image_url": "https://m.media-amazon.com/images/I/815t1-d+7BL._AC_SL1500_.jpg",
    "product_dimensions": "43.31 x 11.61 x 11.51 cm; 830 g",
    "categories": [
        "Toys",
        "Baby & Toddler Toys",
        "Early Development & Activity Toys",
        "Sorting, Stacking & Plugging Toys"
    ],
    "delivery": [
        "FREE delivery Friday, 25 October on eligible first order",
        "Or fastest delivery Thursday, 24 October. Order within 4 hrs 40 mins"
    ],
    "features": [
        "Sturdy and stable base plate with 9 pins and 45 beautiful large wooden rings and 10 removable square number plates in rainbow colours.",
        "Great for learning counting, sorting, and matching colors and numbers, as well as practicing simple mathematics.",
        "Made from sustainable wood with eco-friendly and non-toxic paints. Complies with EN71 / CPSA standards."
    ],
    "top_review": "Sehr lehrreich",
    "variations": [
        {
            "name": "Caterpillar Threading Toy",
            "price": 13.99,
            "currency": "EUR"
        },
        {
            "name": "Pack of 15",
            "price": 16.99,
            "currency": "EUR"
        },
        {
            "name": "Pack of 45",
            "price": 23.99,
            "currency": "EUR"
        }
    ],
    "product_rating_object": {
        "one_star": 35,
        "two_star": 0,
        "three_star": 82,
        "four_star": 227,
        "five_star": 1308
    }
}
```
#### Code Example:
Below is a Python script that triggers the collection of products across all major Amazon domains and stores the results in a JSON file:
```python
import json
import requests
import time


def trigger_datasets(
    api_token, dataset_id, datasets, dataset_type="trigger", discover_by="url"
):
    headers = {
        "Authorization": f"Bearer {api_token}",
        "Content-Type": "application/json",
    }

    trigger_url = f"https://api.brightdata.com/datasets/v3/trigger?dataset_id={
        dataset_id}&type={dataset_type}&discover_by={discover_by}"

    # Sending API request to trigger dataset collection
    response = requests.post(trigger_url, headers=headers, data=json.dumps(datasets))

    if response.status_code == 200:
        print("Data collection triggered successfully!")
        snapshot_id = response.json().get("snapshot_id")
        return snapshot_id if snapshot_id else print("No snapshot ID returned.")
    else:
        print(f"Error: {response.status_code} - {response.text}")
        return None


def get_snapshot_data(api_token, snapshot_id):
    headers = {"Authorization": f"Bearer {api_token}"}
    snapshot_url = f"https://api.brightdata.com/datasets/v3/snapshot/{
        snapshot_id}?format=json"

    # Polling until the snapshot data is ready
    while True:
        response = requests.get(snapshot_url, headers=headers)

        if response.status_code == 200:
            return response.json()
        elif response.status_code == 202:
            print("Snapshot still processing... retrying.")
        else:
            print(f"Error: {response.status_code} - {response.text}")
            return None
        time.sleep(10)


def store_data(data, filename="amazon_products_global_dataset.json"):
    if data:
        with open(filename, "w") as file:
            json.dump(data, file, indent=4)
        print(f"Data saved in {filename}.")
    else:
        print("No data to store.")


if __name__ == "__main__":
    API_TOKEN = "API_TOKEN"
    DATASET_ID = "gd_lwhideng15g8jg63s7"

    # Define the dataset with URLs
    datasets = [
        {"url": "https://www.amazon.com/dp/B0CHHSFMRL/"},
        {
            "url": "https://www.amazon.de/-/en/dp/B078TNNZK3/ref=sspa_dk_browse_2/?_encoding=UTF8&ie=UTF8&sp_csd=d2lkZ2V0TmFtZT1zcF9icm93c2VfdGhlbWF0aWM%3D&pd_rd_w=fHlOu&content-id=amzn1.sym.642a11a6-0e1e-47fa-93c2-5dc9d607a7a1&pf_rd_p=642a11a6-0e1e-47fa-93c2-5dc9d607a7a1&pf_rd_r=4JX920KFM8Q7PR83HJ7V&pd_rd_wg=K1OVN&pd_rd_r=be656f87-1a09-4144-b7cf-4e932d6a73c4&ref_=sspa_dk_browse&th=1"
        },
        {
            "url": "https://www.amazon.co.jp/X-TRAK-Folding-Bicycle-Carbon-Adjustable/dp/B0CWV9YTLV/ref=sr_1_1_sspa?crid=3MKZ2ALHSLFOM&dib=eyJ2IjoiMSJ9.YnBVPwJ7nLxlNGHktwDTFM5v2evnsXlnZTJHJKuG8dLeeRCILpy0Knr3ofiKpUGQYi6xR6y4tgdtal85DJ8u6DD_n9r1oVCXdVo0NFmNAfStU6E-MhBig5p_gZGjluAYv5HgUIoEPl0v3iMiRxZNRfivqB-utxOkPOOfXIBHLemry17XcltUDTQqtJv-kP-ZqdP29mjD2cRlbkALtHPKU44MvBC9WUrNcUHAMrlAxtTAByuriywMqz-w2P0HCeehcZTJ1EiLf2VR8cxCiwuaUbIOU3tr1kDN6D7yYPrgRn4.6AOdSmJsksZkqLg8kNM6EvWxIFOijCsP2zo5NLHn1P4&dib_tag=se&keywords=Bicycles&qid=1716973495&sprefix=%2Caps%2C851&sr=8-1-spons&sp_csd=d2lkZ2V0TmFtZT1zcF9hdGY&psc=1"
        },
        {
            "url": "https://www.amazon.in/Watches-Women%EF%BC%8CLadies-Stainless-Waterproof-Luminous/dp/B0D31HBWG1/ref=sr_1_2_sspa?dib=eyJ2IjoiMSJ9.1zFa2vTCZdD-bv6Knt_pWqvcRZPSSTPDwgMClRJNsWqdyGdCmryjEAfWpd-ZhwhC3vvNx9A0G2Gt1R952e7huzlukge2bmJETNf-kHBoWS5kV6g0pUVapEyDOEAGcw5ZvWlkeuLQ9oIwuhckRC6ARCt2yglYV-1HpP7lVGXotK6K6tjrdKxUSAOZJSXeOGP3dGuYPTjo9sllOrwA7FC2GG00aDcsSTzURENFj1c2rS-vNHkYmxOL1JYuwDWK2PJdMpsmkJw3jeMdgaiw7jG5ppMfAjwiETVldQzhHGVUFV8.manfNZwtTUhvDuSGdh32APM1_SmnNiKgOGabyA7rXBo&dib_tag=se&qid=1716973272&rnid=2563505031&s=watch&sr=1-2-spons&sp_csd=d2lkZ2V0TmFtZT1zcF9hdGZfYnJvd3Nl&psc=1"
        },
    ]

    # Trigger dataset collection
    snapshot_id = trigger_datasets(API_TOKEN, DATASET_ID, datasets)

    if snapshot_id:
        # Retrieve the data once the snapshot is ready
        data = get_snapshot_data(API_TOKEN, snapshot_id)
        if data:
            store_data(data)
```

You can view the full output by downloading [this sample JSON file](https://github.com/luminati-io/Amazon-scraper/blob/main/output_data/amazon_products_global_dataset.json).

### Amazon Products Global Dataset - Discover by Category URL
Discover products by providing a specific category URL.

<img width="700" alt="bright-data-web-scraper-api-amazon-product-global-category-url" src="https://github.com/user-attachments/assets/6273ae07-72ea-4a68-a8b7-9c90a0931f90">


#### Key Input Parameters:
| **Parameter** | **Type** | **Description**                               | **Required** |
|---------------|----------|-----------------------------------------------|--------------|
| `url`         | `string` | The category URL from which to scrape products | Yes          |
| `sort_by`     | `string` |Criteria for sorting the results               | No           |
| `zipcode`     | `string` | Zip code for location-specific results         | No           |

#### Performance:
- Average response time per input: 3 minutes 57 seconds

#### Sample Output Data:
Here’s an example of the output you will receive after collecting product data:
```json
{
    "title": "De'Longhi Stilosa EC230.BK, Traditional Barista Pump Espresso Machine, Espresso and Cappuccino, 2 cups, Black",
    "brand": "De'Longhi",
    "seller_name": "Hughes Electrical",
    "initial_price": 104.99,
    "final_price": 94,
    "currency": "GBP",
    "availability": "Only 1 left in stock.",
    "rating": 3.9,
    "reviews_count": 395,
    "asin": "B085J8LV4F",
    "url": "https://www.amazon.co.uk/dp/B085J8LV4F?th=1&psc=1",
    "image_url": "https://m.media-amazon.com/images/I/715gqhkOEiL._AC_SL1500_.jpg",
    "categories": [
        "Cooking & Dining",
        "Coffee, Tea & Espresso",
        "Coffee Machines",
        "Espresso & Cappuccino Machines"
    ],
    "delivery": [
        "FREE delivery 25 - 28 October",
        "Or fastest delivery Tomorrow, 22 October. Order within 3 hrs 59 mins"
    ],
    "features": [
        "Unleash your inner barista and create all your coffee shop favourites at home",
        "15-bar pump espresso maker with a stainless steel boiler for perfect coffee extraction",
        "Steam arm to create frothy cappuccinos and smooth lattes",
        "Combination of matt and glossy black finish with an anti-drip system"
    ],
    "input": {
        "url": "https://www.amazon.co.uk/DeLonghi-EC230-BK-Traditional-Espresso-Cappuccino/dp/B085J8LV4F/ref=sr_1_4"
    },
    "discovery_input": {
        "url": "https://www.amazon.co.uk/b/?_encoding=UTF8&node=10706951&ref_=Oct_d_odnav_d_13528598031_1",
        "sort_by": "Best Sellers",
        "zipcode": ""
    }
}
```
#### Code Example:
Below is a Python script that triggers the collection of products by category URL and stores the results in a JSON file:
```python
import json
import requests
import time


def trigger_datasets(api_token, dataset_id, datasets, dataset_type="discover_new", discover_by="category_url", limit_per_input=4):
    headers = {
        "Authorization": f"Bearer {api_token}",
        "Content-Type": "application/json",
    }

    trigger_url = f"https://api.brightdata.com/datasets/v3/trigger?dataset_id={dataset_id}&type={
        dataset_type}&discover_by={discover_by}&limit_per_input={limit_per_input}"

    # Sending API request to trigger dataset collection
    response = requests.post(
        trigger_url, headers=headers, data=json.dumps(datasets))

    if response.status_code == 200:
        print("Data collection triggered successfully!")
        snapshot_id = response.json().get("snapshot_id")
        return snapshot_id if snapshot_id else print("No snapshot ID returned.")
    else:
        print(f"Error: {response.status_code} - {response.text}")
        return None


def get_snapshot_data(api_token, snapshot_id):
    headers = {"Authorization": f"Bearer {api_token}"}
    snapshot_url = f"https://api.brightdata.com/datasets/v3/snapshot/{
        snapshot_id}?format=json"

    # Polling until the snapshot data is ready
    while True:
        response = requests.get(snapshot_url, headers=headers)

        if response.status_code == 200:
            return response.json()
        elif response.status_code == 202:
            print("Snapshot still processing... retrying.")
        else:
            print(f"Error: {response.status_code} - {response.text}")
            return None
        time.sleep(10)


def store_data(data, filename="amazon_category_url_data.json"):
    if data:
        with open(filename, "w") as file:
            json.dump(data, file, indent=4)
        print(f"Data saved in {filename}.")
    else:
        print("No data to store.")


if __name__ == "__main__":
    API_TOKEN = "API_TOKEN"
    DATASET_ID = "gd_lwhideng15g8jg63s7"

    # Define the dataset with category URLs, sort_by, and zipcodes
    datasets = [
        {"url": "https://www.amazon.com/s?i=luggage-intl-ship",
            "sort_by": "Featured", "zipcode": "10001"},
        {"url": "https://www.amazon.de/-/en/b/?node=1981001031&ref_=Oct_d_odnav_d_355007011_2&pd_rd_w=OjE3S&content-id=amzn1.sym.0069bc39-a323-47d6-a8fb-7558e4a563e4&pf_rd_p=0069bc39-a323-47d6-a8fb-7558e4a563e4&pf_rd_r=6YXZ7HGFNNEAF0GSDPDH&pd_rd_wg=0yR1G&pd_rd_r=a95cb46c-78ef-4b7b-845d-49fe04556440", "sort_by": "Price: Low to High", "zipcode": ""},
        {"url": "https://www.amazon.co.uk/b/?_encoding=UTF8&node=10706951&bbn=11052681&ref_=Oct_d_odnav_d_13528598031_1&pd_rd_w=LghVp&content-id=amzn1.sym.7414f21e-2c95-4394-9a75-8c1b3641bcea&pf_rd_p=7414f21e-2c95-4394-9a75-8c1b3641bcea&pf_rd_r=EE0PQWMSY2J0G8M032EB&pd_rd_wg=7snrU&pd_rd_r=349e1e79-8bf8-4e00-947d-17eab2942b8d", "sort_by": "Best Sellers", "zipcode": ""},
        {"url": "https://www.amazon.co.jp/-/en/b/?node=377403011&ref_=Oct_d_odnav_d_15314601_0&pd_rd_w=ajUV4&content-id=amzn1.sym.0d505cca-fde9-497c-b5f8-e827c26fad17&pf_rd_p=0d505cca-fde9-497c-b5f8-e827c26fad17&pf_rd_r=92HSETNKKN3RTA615BV7&pd_rd_wg=AwOOk&pd_rd_r=629211d8-6768-478c-94a2-829a0a0ca2a6", "sort_by": "", "zipcode": ""}
    ]

    # Trigger dataset collection
    snapshot_id = trigger_datasets(API_TOKEN, DATASET_ID, datasets)

    if snapshot_id:
        # Retrieve the data once the snapshot is ready
        data = get_snapshot_data(API_TOKEN, snapshot_id)
        if data:
            store_data(data)
```
You can view the full output by downloading [this sample JSON file](https://github.com/luminati-io/Amazon-scraper/blob/main/output_data/amazon_product_global_category_url.json).

### Amazon Products Global Dataset - Discover by Keywords
Discover products by using specific keywords across Amazon domains.

<img width="700" alt="bright-data-web-scraper-api-amazon_global_dataset_by_keyword" src="https://github.com/user-attachments/assets/a613559e-bba0-44d4-82fa-c947d8258212">

#### Key Input Parameters:
| **Parameter**      | **Type**   | **Description**                            | **Required** |
|--------------------|------------|--------------------------------------------|--------------|
| `keywords`         | `string`   | The keyword to search for products         | Yes          |
| `domain`           | `string`   | Amazon domain to search within             | Yes          |
| `pages_to_search`  | `number`   | Number of pages to search                  | No           |

#### Performance:
- Average response time per input: 56 seconds

#### Sample Output Data:
Here’s an example of the output you will receive after performing a keyword search for products:
```json
{
    "title": "Mitutoyo 500-197-30 Electronic Digital Caliper AOS Absolute Scale Digital Caliper, 0 to 8\"/0 to 200mm Measuring Range, 0.0005\"/0.01mm Resolution",
    "brand": "Mitutoyo",
    "seller_name": "Everly Home & Gift",
    "initial_price": 157.97,
    "final_price": 137.77,
    "currency": "USD",
    "availability": "In Stock",
    "rating": 4.8,
    "reviews_count": 88,
    "asin": "B01N6C3EGR",
    "url": "https://www.amazon.com/dp/B01N6C3EGR?th=1&psc=1",
    "image_url": "https://m.media-amazon.com/images/I/61Gigoh3LbL._SL1500_.jpg",
    "categories": [
        "Industrial & Scientific",
        "Test, Measure & Inspect",
        "Dimensional Measurement",
        "Calipers",
        "Digital Calipers"
    ],
    "delivery": [
        "FREE delivery Saturday, October 26",
        "Or Prime members get FREE delivery Tomorrow, October 22"
    ],
    "features": [
        "Hardened stainless steel construction for protection of caliper components",
        "Digital, single-value readout LCD display in metric units for readability",
        "Measuring Range 0 to 8\"/0 to 200mm",
        "Measurement Accuracy +/-0.001",
        "Resolution 0.0005\"/0.01mm"
    ],
    "input": {
        "url": "https://www.amazon.com/Mitutoyo-500-197-30-Electronic-Measuring-Resolution/dp/B01N6C3EGR"
    },
    "discovery_input": {
        "keywords": "Mitutoyo",
        "domain": "https://www.amazon.com",
        "pages_to_search": 1
    }
}
```
#### Code Example:
Below is a Python script that triggers the collection of products by keyword search and stores the results in a JSON file:
```python
import json
import requests
import time


def trigger_datasets(
    api_token, dataset_id, datasets, dataset_type="discover_new", discover_by="keywords"
):
    headers = {
        "Authorization": f"Bearer {api_token}",
        "Content-Type": "application/json",
    }

    trigger_url = f"https://api.brightdata.com/datasets/v3/trigger?dataset_id={
        dataset_id}&type={dataset_type}&discover_by={discover_by}"

    # Sending API request to trigger dataset collection
    response = requests.post(trigger_url, headers=headers, data=json.dumps(datasets))

    if response.status_code == 200:
        print("Data collection triggered successfully!")
        snapshot_id = response.json().get("snapshot_id")
        return snapshot_id if snapshot_id else print("No snapshot ID returned.")
    else:
        print(f"Error: {response.status_code} - {response.text}")
        return None


def get_snapshot_data(api_token, snapshot_id):
    headers = {"Authorization": f"Bearer {api_token}"}
    snapshot_url = f"https://api.brightdata.com/datasets/v3/snapshot/{
        snapshot_id}?format=json"

    # Polling until the snapshot data is ready
    while True:
        response = requests.get(snapshot_url, headers=headers)

        if response.status_code == 200:
            return response.json()
        elif response.status_code == 202:
            print("Snapshot still processing... retrying.")
        else:
            print(f"Error: {response.status_code} - {response.text}")
            return None
        time.sleep(10)


def store_data(data, filename="amazon_global_dataset_by_keyword.json"):
    if data:
        with open(filename, "w") as file:
            json.dump(data, file, indent=4)
        print(f"Data saved in {filename}.")
    else:
        print("No data to store.")


if __name__ == "__main__":
    API_TOKEN = "YOUR_API_TOKEN"
    DATASET_ID = "gd_lwhideng15g8jg63s7"

    # Define the dataset with keywords, domain, and pages_to_search
    datasets = [
        {
            "keywords": "Mitutoyo",
            "domain": "https://www.amazon.com",
            "pages_to_search": 1,
        },
        {
            "keywords": "smart watch",
            "domain": "https://www.amazon.co.uk",
            "pages_to_search": 2,
        },
        {
            "keywords": "football",
            "domain": "https://www.amazon.in",
            "pages_to_search": 4,
        },
        {
            "keywords": "baby cloth",
            "domain": "https://www.amazon.de",
            "pages_to_search": 3,
        },
    ]

    # Trigger dataset collection
    snapshot_id = trigger_datasets(API_TOKEN, DATASET_ID, datasets)

    if snapshot_id:
        # Retrieve the data once the snapshot is ready
        data = get_snapshot_data(API_TOKEN, snapshot_id)
        if data:
            store_data(data)
```
You can view the full output by downloading [this sample JSON file](https://github.com/luminati-io/Amazon-scraper/blob/main/output_data/amazon_global_dataset_by_keyword.json).
