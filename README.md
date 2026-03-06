# Hoji Shinbun Digital Collection Webscraper

This script utilizes Playwright and Node.js to scrape data from a specific website. It automatically navigates through search results, extracts relevant article content, and counts the occurrences of a specific word in the text. The collected data is saved into a JSON file.

## Prerequisites

Before running the script, make sure you have the following installed:

- **Node.js** (version 14 or higher)
- **Python** (latest version)

## Setup

1. **Clone this repository** or download the script `webScraper.js`.

2. **Install dependencies:**

   The project includes a `package.json` file that lists all required dependencies. To install them, open a terminal and run the following command:

   ```bash
   npm install
   ```

   This will automatically download and install all required packages, including:
   - `playwright` (for browser automation)
   - `fs` (for file system operations)
   - `readline` (for handling input/output)

3. **Prepare the script:**
   - The script allows you to input a target word to search for, a file name for output, the starting URL, and the number of pages to scrape.
   - By default, the script is configured to scrape URLs from a specified starting page and continue until the set number of pages is reached.

## Usage

To use the script, follow these steps:

1. **Launch the script** by running the following command in your terminal:

   ```bash
   node webScraper.js
   ```

2. **Enter the required information**:
   - **Word to search for**: Enter the word you want to search for in the articles.
   - **File name**: Provide a name for the output JSON file (without the `.json` extension).
   - **Start URL**: Provide the starting URL for the scraping process.
   - **Number of pages**: Enter how many pages you want the scraper to process.

3. **When copying and pasting links or Japanese text into the terminal**, remember to use `Ctrl + Shift + V` (instead of the usual `Ctrl + V`). This is necessary to paste the content properly, especially when dealing with non-English characters like Japanese text. **MAKE SURE TO SORT BY "DATA, OLDEST FIRST" ON THE WEBSITE AND SELECT ONLY "CATEGORY: NEWSPAPERS"**

4. **Wait for the script to finish**: The scraper will navigate through the pages, extract the article contents, count the occurrences of the target word, and save the data into a JSON file. **PLEASE DO NOT CLOSE THE VSCODE LET IT SCRAPE EVERYTHING FIRST TO PREVENT LOSING SCRAPED DATA**

## Output

- The results are saved as a JSON file in the format `output-<file_name>.json`.
- The JSON file contains:
  - **link**: The URL of the article.
  - **linkWithDate**: The URL of the article with the publication date.
  - **numWords**: The count of occurrences of the target word in the article.
  - **paragraphs**: The full text content of the article.

## Example

```bash
Enter the word you want to search for: 二世
Enter a file name (without extension): nisei
Enter URL to start scraping from: https://hojishinbun.hoover.org/?a=q&qp=0&r=1&results=1&tyq=PAGE&e=-------en-10--1-byDA-img-%e4%ba%8c%e4%b8%96------
Enter the number of pages to search: 5
```

This will search through 5 pages starting from the provided URL, look for occurrences of the word "二世", and save the results in `output-nisei.json`.

## Troubleshooting

- If the script encounters a login-required page, it will skip that page and move to the next one.
- If there are network or DNS issues, the script will retry the action up to 3 times by default.
- If Cloudflare is active on the Hoji Shinbun website, inject your own verified cookies from a normal chrome tab (cf_clearance) into a "cookies.json" inside the playwright_ws folder.
- An example cookies file is provided, "cookies-example.json"

## License

This project is licensed under the MIT License.
