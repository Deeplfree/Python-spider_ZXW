import urllib,requests,csv
from lxml import etree
##import zxw_title_newurl
page = 0
i = 0
j = 0
file = open('知行网所有提问{}.csv'.format('2'),'w',newline = '',encoding='utf-8')

for i in range(1,2):
    page = range(0,43211,10)
    
    formdata = {'searchMessage':'',
    'wtyjCountNo':'10',
    'wtyjINTEXT' :'',
    'wtyjPAGE':'{}'.format(page[i-1]),
    'wtyjNOWPAGE' :'',
    'wtyjrowCount':'43203',
    'wtyjCURURI':'15E50AA2C73FAD7E1060655A18D88E79',
    'wtyjKEYTYPES': '4,12,4,93,4,4,12',
    'wtyjORDER': 'desc',
    'actiontype': 'FirstPage',
    'wtyjORDERKEY': 'wbdate'}

    for key in formdata:
        formdata[key] = formdata[key].encode('utf-8')

    url = 'http://zhixing.xaut.edu.cn/lyhfmore.jsp?urltype=tree.TreeTempUrl&wbtreeid=11038'
    res = requests.post(url , data = formdata)
##    print(res)

    html = res.text

    s = etree.HTML(html)
    for j in range(1,11):
        title = s.xpath('/html/body/div[2]/div/div[2]/form/div/ul/li[{}]/a/text()'.format(j))
        newurl = s.xpath('/html/body/div[2]/div/div[2]/form/div/ul/li[{}]/a/@href'.format(j))
        number = s.xpath('/html/body/div[2]/div/div[2]/form/div/ul/li[{}]/span[1]/text()'.format(j))
        huifudanwei = s.xpath('/html/body/div[2]/div/div[2]/form/div/ul/li[{}]/span[2]/text()'.format(j))
        timeee = s.xpath('/html/body/div[2]/div/div[2]/form/div/ul/li[{}]/span[3]/text()'.format(j))
        title_newurl = {'number':number,'title':title,'回复单位':huifudanwei,'提交时间':timeee,'newurl':newurl}
##        print(title_newurl)
        if title == ['']:
            break
        csvwriter = csv.writer(file)
        csvwriter.writerow([number,title,huifudanwei,timeee,newurl])
##        file.write('\n') 
##        file.write(str(title_newurl)+'\n')


file.close()
print('完成')
