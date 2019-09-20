# Tiingo

import pandas as pd
from io import StringIO
from tiingo import TiingoClient

API_KEY = 'b499de66a5c1e5fdfbf8a3108e93d369b0d54f27' # your API KEY here
client = TiingoClient({'api_key': API_KEY})

df = pd.read_csv(StringIO(client.get_ticker_price('AAPL',
    fmt='csv',
    startDate='01-01-2019',
    endDate='01-15-2019')))



%matplotlib inline
import matplotlib.pyplot as plt


df[['adjClose','close']].plot(kind='barh', subplots=True)
plt.xlabel('Date')
plt.ylabel('Price')
plt.legend()
plt.show()
