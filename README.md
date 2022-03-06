# Sharktank-India-S1-OffersList
Shark Tank India (Season 1) Entrepreneurs – Offers list scrapped from: https://www.serialupdates.me/shark-tank-india-investors-names-sony-tv-new-show-entrepreneurs-list/

Procedure:
•	Import selenium, Beautiful soup and Pandas packages using import
•	Now, automate a blank browser using browser = webdriver.Edge()
•	Initiate the required URL that we need to scrape using browser.get(‘'https://www.serialupdates.me/shark-tank-india-investors-names-sony-tv-new-show-entrepreneurs-list/'’)
•	Since it is a static webpage we can get the html code of the webpage using html requests like requests.get(url).text but I’m using browser.page_source because its more functional.
•	Get the html code of the page using soup = BeautifulSoup(browser.page_source, 'html.parser')
•	If the required scrapping is a table scrapping then we do in a row wise scrapping.
•	So, First lets scrape the top row i.e. “Sr No.”, “Entrepreneur Name”, “From”, “Business” etc……
•	Now, from the html code we’ll be using the division and class to scrape the table: The top row of the table contains div : ‘figure’ and class: ‘wp-block-table is-style-stripes’ 
•	soup.select('figure.wp-block-table.is-style-stripes')[1] – using this we’re are locating the required table. 
•	Now, scrape the head cell (‘th’) using .text.strip() function: soup.select('figure.wp-block-table.is-style-stripes')[1].find_all('th')[0].text.strip()
•	Iterate the above to get all head cells.
•	Scrape data row wise using ‘tbody’ and ‘tr’: soup.select('figure.wp-block-table.is-style-stripes')[1].tbody.find_all('tr')[0].text.strip()
•	Iterate the above to get all table row cells.
•	Define a function to combine all the scrapped data and store it in a dataframe using pd.DataFrame
•	Now, lastly import the dataframe to a csv file using .to_csv(‘file name’)
