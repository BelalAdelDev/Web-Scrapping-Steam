# Web-Scrapping-Steam

This Python project automates the process of scraping current Steam market prices for specific inventory items (CS:GO cases), calculates their value after fees, tracks this data over time by saving it to CSV, and provides live and static visualizations of the total inventory worth.

***

## Features

- Scrapes prices from Steam Community Market listings for specified items
- Calculates item value accounting for Steam's 12% transaction fee
- Maintains historical price data saved in CSV format for weekly or regular review
- Generates live interactive plots (Plotly) to visualize prices and proportions
- Creates a saved pie chart image for contributions of each item to overall inventory worth
- Runs fully automated workflow from data collection to visualization

***

## Installation

1. Ensure Python 3.7+ is installed.
2. Install dependencies:
   ```bash
   pip install pandas plotly matplotlib selenium
   ```
3. Download and install ChromeDriver matching your Chrome version from:
   https://sites.google.com/chromium.org/driver/
4. Set environment variables or update paths inside the script:
   - `CHROMEDRIVER_PATH` - Path to ChromeDriver executable
   - `CHROME_BINARY_PATH` - Path to Chrome browser executable (optional)

***

## Usage

Run the script to scrape prices, update data, and generate plots:

```bash
python your_script_name.py
```

### How It Works

- Scrapes prices weekly or as often as run, from Steam Community Market URLs configured inside the `ITEMS` list.
- Saves incremental results to a CSV file located in `D:/Automation/Inventory Value/cases_prices.csv`.
- Displays a live Plotly dashboard in IPython-compatible environments showing item prices and total worth.
- Produces a pie chart graphic showing contribution of each item to the total value, saved by date.

***

## Configuration

- Modify the `ITEMS` list to add or remove Steam market items. Each entry includes the URL, item name, and inventory quantity.
- Set `SAVE_TO_CSV` to `True` or `False` to enable/disable saving data.
- Adjust `DATA_DIR` and `CSV_PATH` variables to change storage location.
- Specify whether ChromeDriver runs headless or not in `create_driver()` function.

***

## Main Functions

- `create_driver(headless=True)`: Initializes Selenium Chrome WebDriver.
- `scrape_price(driver, url)`: Extracts the current market price from a given Steam market URL.
- `get_prices(output_csv)`: Scrapes all configured items, updates CSV, and live plot.
- `create_live_plot()`: Initializes and displays an interactive Plotly figure.
- `update_plot(df)`: Updates the plot with current data live.
- `plot_skin_contributions(df, output_dir)`: Saves a pie chart PNG visualizing inventory value distribution.
- `main()`: Runs entire data collection and visualization workflow.

***

## Example Items List

```python
ITEMS = [
    ("https://steamcommunity.com/market/listings/730/Dreams%20%26%20Nightmares%20Case", "Dreams & Nightmares Case", 1),
    ("https://steamcommunity.com/market/listings/730/Revolution%20Case", "Revolution Case", 2),
    ("https://steamcommunity.com/market/listings/730/Kilowatt%20Case", "Kilowatt Case", 3),
    ("https://steamcommunity.com/market/listings/730/Fracture%20Case", "Fracture Case", 1),
    ("https://steamcommunity.com/market/listings/730/Recoil%20Case", "Recoil Case", 2),
    ("https://steamcommunity.com/market/listings/730/Gallery%20Case", "Gallery Case", 3),
]
```

***

## Notes

- The script uses the 12% Steam market transaction fee to calculate the net price after fees.
- Running the script requires a stable internet connection and valid Steam market URLs.
- The live plot requires an IPython/Jupyter environment to display interactively.
- The project setup assumes Windows paths but can be customized for other OSs.

***

## License

This project is open source and available for adaptation and use.

***

This project is perfect for users who want to check their inventory values regularly on a weekly basis by running a quick script to keep track of fluctuating market prices and the total worth of their cases.
