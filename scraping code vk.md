[code with description](scraping/vk_tutorial.ipynb)

```
!pip install vk_api

vkApiSession = vk_api.VkApi(token='...')

```

Токен живет 1 час, он расположен между https://oauth.vk.com/blank.html#access_token= и user_id=61895623
https://oauth.vk.com/blank.html#access_token= **ЗДЕСЬ ВАШ ТОКЕН** &user_id=61895623

Токен привязан к вашему IP, поэтому запускаем его локально!

```
# https://vkhost.github.io/

import vk_api

vkApiSession= vk_api.VkApi(token="токен")

vk = vkApiSession.get_api()
```
И достаем какую-то информацию со страницы
```
posts = vk.wall.get(owner_id=154186168, count=5)['items']
```
