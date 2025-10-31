# Web Scraping Project: Football Match Goals Data

This project scrapes detailed football match data from Adam Choi's Team Goals website using **Selenium with BeautifulSoup**. The scraper automatically iterates through all available countries and leagues, collecting match information including dates, teams, scores, and league details.

## Project Structure

```
├── Teams-Match-Goals.ipynb
├── team_goals_2025-2026-all-leagues.csv
├── team_goals_2025-2026-all-leagues.json
└── README.md
```

-   **Teams-Match-Goals.py**: Implements web scraping using Selenium WebDriver (Firefox) and BeautifulSoup. Collects data from multiple countries and leagues by automating dropdown selections.

## What Data is Scraped

The scraper collects the following information for each match:

-   **Country**: The country where the league is based
-   **Date**: Match date
-   **Home Team**: Home team name
-   **Score**: Final match score
-   **Away Team**: Away team name
-   **League**: League name

## Prerequisites

-   Python 3.8+
-   Firefox browser installed
-   Libraries:
    -   `selenium`
    -   `beautifulsoup4`
    -   `pandas`
    -   `numpy`

Install dependencies using:

```bash
pip install selenium beautifulsoup4 pandas numpy
```

**Note**: You'll also need to install GeckoDriver for Firefox:

-   Download from: https://github.com/mozilla/geckodriver/releases
-   Add to your system PATH or place in the project directory

## Usage

1. Ensure Firefox and GeckoDriver are properly installed and configured.

2. Run the scraper:

    ```bash
    python Teams-Match-Goals.py
    ```

3. The script will:
    - Launch a Firefox browser window
    - Automatically navigate through all available countries
    - For each country, iterate through all leagues
    - Scrape match data from each league
    - Print progress to the console
    - Store all data in a Python list

## How It Works

1. **Browser Automation**: Uses Selenium WebDriver to control Firefox browser
2. **Dynamic Content Handling**: Waits for dropdown elements to load using explicit waits
3. **Dropdown Navigation**:
    - Selects each country from the country dropdown
    - For each country, selects each available league
    - Waits 2 seconds between selections to allow page content to update
4. **Data Extraction**: Uses BeautifulSoup to parse the HTML and extract match data from table rows
5. **Data Storage**: Collects all matches in a structured list of dictionaries

## Code Features

-   **Explicit Waits**: Uses `WebDriverWait` to ensure elements are loaded before interaction
-   **Robust Selectors**: Combines Selenium for interaction and BeautifulSoup for parsing
-   **Error Prevention**: Checks for the presence of date columns before processing rows
-   **Progress Tracking**: Prints country and league names during scraping

## Data Structure

Each match is stored as a dictionary with the following structure:

```python
{
    "country": "England",
    "date": "01/01/2024",
    "home_team": "Arsenal",
    "score": "2 - 1",
    "away_team": "Chelsea",
    "League": "Premier League"
}
```

## Notes

-   **Data Source**: Data is scraped from [Adam Choi's Team Goals](https://www.adamchoi.co.uk/teamgoals/detailed)
-   **Browser Requirement**: Currently configured for Firefox. To use Chrome, replace `webdriver.Firefox()` with `webdriver.Chrome()` and install ChromeDriver
-   **Scraping Time**: The scraping process may take a considerable amount of time as it iterates through all countries and leagues with 2-second delays
-   **Website Structure**: The scraper relies on specific CSS selectors. Changes to the website structure may break the scraper
-   **Memory Usage**: All data is stored in memory. For very large datasets, consider writing to disk periodically

## Example Output

After running the script, the `data` list will contain entries like:

```python
[
    {
        "country": "England",
        "date": "15/08/2023",
        "home_team": "Manchester United",
        "score": "1 - 0",
        "away_team": "Wolves",
        "League": "Premier League"
    },
    {
        "country": "Spain",
        "date": "13/08/2023",
        "home_team": "Barcelona",
        "score": "3 - 0",
        "away_team": "Getafe",
        "League": "La Liga"
    },
    ...
]
```

## License

This project is licensed under the MIT License.
