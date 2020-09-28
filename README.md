# IOT
Pycharm code for web info scrapping (price,weather,etc)
import requests
from bs4 import BeautifulSoup
#import urllib.request

#name of the factory：a.opu_l2
page = requests.get("https://price.21food.cn/product/990.html")
soup = BeautifulSoup(page.content, 'html.parser')
containers = soup.find('div', class_='sjs_top_cent_erv')
#print("the new container is :", containers)

ULS = containers.find('ul')
#print(ULs)
list = ULS.findAll('li')
for name1 in list:
    name = name1.find('a',class_='opu_l2')
#print("so the list is:  ", list)

#for i in list:
    price = name1.find_all('span') #<span>tag
    print(name.text)
    print('价格：')
    for p in price:
     print(p.text)

       # print("so the price 最高价: ", p[0],"最低价:",p[1],"平均价：", p[2],"日期：",p[3])

