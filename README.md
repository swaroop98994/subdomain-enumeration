# subdomain-enumeration
import requests
from bs4 import BeautifulSoup

# The base url that we want to find subdomains for
base_url = 'example.com'

# The url to the online subdomain scanner
scanner_url = 'https://www.virustotal.com/en/domain/' + base_url + '/information/'

# Send a GET request to the scanner
response = requests.get(scanner_url)

# Parse the HTML content of the page
soup = BeautifulSoup(response.content, 'html.parser')

# Find all of the subdomains on the page
subdomains = soup.find_all('span', class_='domain')

# Print out the subdomains
for subdomain in subdomains:
    print(subdomain.text)

