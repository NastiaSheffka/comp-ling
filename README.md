# scraping
[code with description in google colab](scraping/web.ipynb)

```
import requests
from bs4 import BeautifulSoup
```

## wiki (simple website)
```
url = 'https://en.wikipedia.org/wiki/Pug'
r_wiki = requests.get(url)

r_wiki

headers = {
        'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/109.0.0.0 Safari/537.36',
}

soup_wiki = BeautifulSoup(r_wiki.text, 'html.parser')
soup_wiki

link_wiki = soup_wiki.find_all('a') #достаем все с тегом ссылки
link_wiki

pars_wiki = soup_wiki.find_all('p') #достаем все с тегом параграфы
pars_wiki

texts_wiki= [text.get_text() for text in pars_wiki]
texts_wiki

len(texts_wiki)
```

## imbd (tough connection - you need to overcome protection)
```
url = 'https://www.imdb.com/chart/top/'

r_imbd = requests.get(url=url, headers=headers)
r_imbd

soup_imbd = BeautifulSoup(r_imbd.text, 'html.parser')
soup_imbd

pars_imbd = soup_imbd.find_all('script', type='application/ld+json')[0]
pars_imbd

import json

data = json.loads(pars_imbd.string)
data

from  pprint import pprint
pprint(data)

data.keys()

data['itemListElement'][0]['item']['description']

```
