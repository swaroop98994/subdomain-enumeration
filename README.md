# subdomain-enumeration
import requests

from bs4 import BeautifulSoup
base_url = 'example.com'

scanner_url = 'https://www.virustotal.com/en/domain/' + base_url + '/information/'

response = requests.get(scanner_url)

soup = BeautifulSoup(response.content, 'html.parser') 

subdomains = soup.find_all('span', class_='domain') 

for subdomain in subdomains:
    print(subdomain.text)

