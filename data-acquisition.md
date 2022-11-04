```python
from bs4 import BeautifulSoup
import urllib.request

file = open('LINKS.txt', 'r')
lines = file.readlines()
for line in lines:
    temp = []
    counter = 0
    words = line.split('#')
    ctg = words[1].strip()
    rang = 0
    while counter < 100:
        url = "".join([words[0].strip(),str(rang)]).strip()
        page = urllib.request.urlopen(url)
        soup = BeautifulSoup(page, 'html.parser')
        for link in soup.find_all('img'):
            pic_url = link['src']
            pic_name = pic_url.split('/')[-1]
            if pic_name[-3:] == 'jpg' and pic_url not in temp:
                try:
                    urllib.request.urlretrieve(pic_url, pic_name)
                except:
                    continue
                temp.append(pic_url)
                counter = counter + 1
                if counter >= 99:
                    break
        rang = rang + 24
    print(counter,ctg,"images downloaded")
```
