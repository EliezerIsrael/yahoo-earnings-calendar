# Yahoo! Earnings Calendar Scraper
Scrapes Yahoo! Finance earnings calendar to get data for a specific date or a date range. 
This is worked on top of the original repo here: https://github.com/wenboyu2/yahoo-earnings-calendar
Adapted to work for Python 3.
Added region parameter to allow retrieval of a specific region. Use two digit country code as
the example below.

## Installation
### Pip
```sh
pip install git+https://github.com/fricative/yahoo-earnings-calendar.git
```

## Usage

### Get earnings date information on a specific date or in a date range
```python
import datetime
from yahoo_earnings_calendar import YahooEarningsCalendar
...
date_from = datetime.datetime(2018,10,28,0,0)
date_to = datetime.datetime(2018,11,2,23,59)
yec = YahooEarningsCalendar()
print (yec.earnings_on(date_from, 'JP'))
print (yec.earnings_between(date_from, date_to, 'JP'))
```

#### Data attributes
- companyshortname: Company Name
  - e.g., 20160606
- ticker: Ticker
  - e.g., AAPL
- startdatetime: Event Start Time
  - e.g., 2017-04-23T21:00:00.000-04:00
- startdatetimetype: Event Start Time Type
  - e.g., TAS (Time Not Supplied), AMC (After Market Close	)
- epsestimate: EPS Estimate
- epsactual: Reported EPS
- epssurprisepct: Surprise (%)
- gmtOffsetMilliSeconds: GMT Offset in MS

### Get the next earnings date of a specific symbol
```python
import datetime
from yahoo_earnings_calendar import YahooEarningsCalendar
# Returns the next earnings date of BOX in Unix timestamp
print(yec.get_next_earnings_date('box'))
# 1508716800
```
