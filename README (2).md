# Stock Price Tracker
A Python application that simulates fetching stock prices. This project demonstrates how to work with simulated real-time and historical stock prices, handle errors, use command-line arguments, and log data to a file.

# Features
Fetches simulated stock prices for a given stock symbol.
Retrieves historical stock prices for analysis.
Checks if the current stock price falls within a specified range.
Provides detailed output with options for verbosity.

# Installation
Clone the repository:
git clone https://github.com/amenft7/Stock-Price-Tracker.git
Navigate to the project directory:
cd Stock-Price-Tracker
# Usage
Run the script:
python stock_price_tracker.py

# Code
import datetime

# Simulated stock prices for demonstration
simulated_prices = {
    'AAPL': 175.05,
    'TSLA': 678.90,
    'GOOGL': 2845.23,
    'AMZN': 3342.88,
    'MSFT': 295.21
}

# Simulated historical data
historical_prices = {
    'AAPL': [170.10, 172.25, 174.55, 176.00, 175.05],
    'TSLA': [665.10, 670.50, 675.00, 680.00, 678.90],
    'GOOGL': [2800.00, 2825.50, 2835.00, 2850.00, 2845.23],
    'AMZN': [3300.00, 3325.50, 3335.75, 3340.50, 3342.88],
    'MSFT': [290.00, 292.50, 293.75, 296.00, 295.21]
}

def get_stock_price(symbol):
    """
    Retrieve simulated stock price for the given symbol.

    Args:
    symbol (str): Stock symbol (e.g., 'AAPL')

    Returns:
    float: Simulated current stock price
    """
    return simulated_prices.get(symbol.upper(), None)

def get_historical_prices(symbol):
    """
    Retrieve simulated historical prices for the given symbol.

    Args:
    symbol (str): Stock symbol (e.g., 'AAPL')

    Returns:
    list: List of historical prices
    """
    return historical_prices.get(symbol.upper(), [])

def display_stock_info(symbol, price, historical_prices=None):
    """
    Display stock information.

    Args:
    symbol (str): Stock symbol
    price (float): Current stock price
    historical_prices (list, optional): List of historical prices
    """
    timestamp = datetime.datetime.now().strftime('%Y-%m-%d %H:%M:%S')
    if price is not None:
        print(f"[{timestamp}] The current price of {symbol} is ${price:.2f}")
    else:
        print(f"[{timestamp}] Stock symbol '{symbol}' not found.")

    if historical_prices:
        print(f"Historical prices for {symbol}: {', '.join(f'${p:.2f}' for p in historical_prices)}")

def check_price_range(price, min_price, max_price):
    """
    Check if the stock price is within the specified range.

    Args:
    price (float): Current stock price
    min_price (float): Minimum price of the range
    max_price (float): Maximum price of the range

    Returns:
    bool: True if the price is within the range, False otherwise
    """
    return min_price <= price <= max_price

def main():
    # Simulated user input
    symbols = ['AAPL', 'TSLA', 'GOOGL']
    verbose = True
    min_price = 170.00
    max_price = 700.00

    for symbol in symbols:
        # Retrieve stock price and historical data
        price = get_stock_price(symbol)
        historical_data = get_historical_prices(symbol)
        
        if verbose:
            print(f"Fetching stock price for symbol: {symbol}")
            print(f"Retrieved stock price: ${price if price is not None else 'N/A'}")
        
        display_stock_info(symbol, price, historical_data)
        
        if price and check_price_range(price, min_price, max_price):
            print(f"The current price of {symbol} is w

            print(f"The current price of {symbol} is outside the range of ${min_price} to ${max_price}.")
        
        print()  # Print a newline for better readability

if __name__ == "__main__":
    main()

