# -*- coding: utf-8 -*-
"""
Created on Sat Jan  2 20:41:13 2016

@author: xenia
"""

from __future__ import unicode_literals
"""### Print出txt中全文
f = open('/Users/xenia/Desktop/text.txt', 'r', buffering=-1, encoding='utf-8')
for line in f:
    print (line)
f.close()
"""

### 將 content 中文檔斷詞後，分行寫入 revised 中，並計算總詞數（不包含標點符號）
import jieba
import sys
sys.path.append("../")
import jieba.posseg
import jieba.analyse

content = open('/Users/xenia/Desktop/txt_file/text_1_1225_policy.txt', 'rb').read()
revised = open('/Users/xenia/Desktop/txt_file/out.txt', 'w', buffering=-1, encoding='utf-8')
jieba.suggest_freq(('民進黨'), True) #若有新詞、專有名詞，可隨時提高詞頻 or add_word
words=jieba.cut(content, cut_all=False)
term = 0
for word in words:
    revised.write(word)
    revised.write('\n')
    if word != '，' and word != '。' and word != '：' and word != '；' and word != '、' and word != '「' and word != '」' and word != '？' and word != '！' and word != ' ' and word != '\n' and word != '（' and word != '）' and word != '”' and word != '“': 
        term = term +1

revised.close()

### 針對 revised 中斷詞完成之文檔，搜尋目標詞，計算其出現次數及詞頻 (term frequency)
### 因 jieba 功能限制，計算「我」的次數，必須扣除「我們」的次數
import re
wordnumber = list()
regex=re.compile('立倫') #輸入目標詞
y=open('/Users/xenia/Desktop/txt_file/out.txt', 'r', buffering=-1, encoding='utf-8')
for word in y:
    resultout=regex.search(word)
    if(resultout):
        wordnumber.append('found'),resultout.string
sub='found'
print("目標詞出現次數：",wordnumber.count(sub))
print ("總詞數：",term)
print("詞頻：",wordnumber.count(sub)/term)

"""
### TextRank 算法：以 graph 方式提取文本關鍵詞
print ('-'*30)
print ("TextRank")
for x, w in jieba.analyse.textrank(content, withWeight=True):
    print('%s %s' % (x, w))
print ('-'*30)

### extract_tags: 從文章中取出 TF-IDF 值最大的關鍵詞
print ("Extract Tags")
for x, w in jieba.analyse.extract_tags(content, withWeight=True):
    print('%s %s' % (x, w))
print ('-'*30)
"""
