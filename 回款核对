import os
import pandas as pd
import xlrd
#输入日期、银行、卡号自动查询当前余额
def query_dq(date,card):
    os.chdir('C:\\Users\\Administrator\\Desktop\\日常数据\\逾期数据\\银行反馈数据')  
    list = os.listdir('C:\\Users\\Administrator\\Desktop\\日常数据\\逾期数据\\银行反馈数据')
    m=0
    while float(list[m])<=date:                                         #输入日期，得到该日期文件路径
        m = m + 1         
    os.chdir('C:\\Users\\Administrator\\Desktop\\日常数据\\逾期数据\\银行反馈数据\\'+list[m-1])            #改变路径
    list1 = os.listdir('C:\\Users\\Administrator\\Desktop\\日常数据\\逾期数据\\银行反馈数据\\'+list[m-1])    #返回该日期路径下的文件列表 
    for i in list1:    #读取银行账单
        if '四平逾期' in  i:
            bill_sp = pd.read_excel(i)
            bill_sp['银行'] ='四平' 
            bill_sp = pd.DataFrame(bill_sp[['卡号','当前余额','银行']])
        if '长合汽车销售' in i:
            bill_cc = pd.read_excel(i)
            bill_cc['银行'] ='长春'
            bill_cc['当前余额'] = bill_cc['当前卡余额']
            bill_cc = pd.DataFrame(bill_cc[['卡号','当前余额','银行']])
        if '长合逾期' in i:
            bill_jn = pd.read_excel(i)
            bill_jn['银行'] ='江南'
            bill_jn['当前余额'] = bill_jn['卡余额']
            bill_jn = pd.DataFrame(bill_jn[['卡号','当前余额','银行']])
            
    bill = pd.concat([bill_sp,bill_cc,bill_jn])                          #合并每天银行账单数据
    print('日期:  '+list[m-1])
    print(bill[bill['卡号'].isin([card])]) 
#         print(bill_cc[bill_cc['卡号'].isin([card])])                           #根据卡号查找该用户所在行的数据
#         print(bill_sp[bill_sp['卡号'].isin([card])])                           #根据卡号查找该用户所在行的数据
#         print(bill_jn[bill_jn['卡号'].isin([card])])                           #根据卡号查找该用户所在行的数据

#     for i in range(len(bill['卡号'])):                     
#         if bill['卡号'][i]== card:
#             print(bill[i])
