from stocklerain1001 import StockInfo

# Create an instance of the StockInfo class
stock_info = StockInfo()

# Load historical data from a CSV file (default: "orcl.csv" in the 'data' directory)
stock_info.load_data()

# Access the loaded data
data = stock_info.Data
Calculating Simple Moving Averages (SMA):
# Calculate SMA with a specified window size (default: 5)
sma_values = stock_info.calculate_sma(window_size=10)

# Access the calculated SMA values
print(sma_values)
Calculating Relative Strength Index (RSI):
# Calculate RSI with a specified window size (default: 14)
rsi_values = stock_info.calculate_rsi(window_size=14)

# Access the calculated RSI values
print(rsi_values)
Writing Results to CSV:
# Write SMA results to a CSV file
sma_header = ['Date', 'Close', 'SMA']
sma_data = [(stock_info.Data[i]["Date"], stock_info.Data[i]['Close'], sma) for i, sma in enumerate(sma_values)]
stock_info.write_file("sma_results.csv", sma_header, sma_data)

# Write RSI results to a CSV file
rsi_header = ['Date', 'Close', 'RSI']
rsi_data = [(stock_info.Data[i]["Date"], stock_info.Data[i]['Close'], rsi) for i, rsi in enumerate(rsi_values)]
stock_info.write_file("rsi_results.csv", rsi_header, rsi_data)
