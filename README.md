# Ad-Blocker1
import requests
from bs4 import BeautifulSoup
# URL der Webseite, auf der Anzeigen blockiert werden sollen
url = 'https://m.youtube.com'
# Liste von Stichwörtern, die in URLs von Anzeigen enthalten sein können
blocked_keywords = ['ad', 'ads', 'banner', 'sponsor']
# Abrufen der HTML-Inhalte der Webseite
response = requests.get (url)
html_content = response.content
# Verwenden von Beautifu/Soup, um das HTML zu analysieren und zu modifizieren
soup = BeautifulSoup(html_content, 'html.parser')
# Suchen nach allen <a>-Tags auf der Seite und Uberprüfen auf blockierte Stichwörter in der URL
for link in soup.find_all ('a'):
href = link.get ('href')
if any (keyword in href for keyword in blocked_keywords): link.decompose() # Entfernen des Links aus dem HTML
# Ausgabe des modifizierten HTMLs ohne Anzeigen
print (soup prettify ())
