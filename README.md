# 實作「rule-based」推薦系統

## 預期產出

* 一份文字敘述：Readme，包含題幹敘述中的兩個問題。
    * 清楚記載這個專案的目的和結果，最後的推薦分數是多少，是否有成功
    * 簡明清楚的使用說明：用了哪些工具和方法？為什麼？
* 兩支連結：包含 colab code、github code。
    * [colab code](https://colab.research.google.com/github/fafnerzhang/data-course-sample/blob/dev/week_1/rule_based_recommandation.ipynb#scrollTo=JGcwKFCS7vOt)
    * Github code[](https://github.com/fafnerzhang/data-course-sample/blob/dev/rule_based_recommandation.ipynb)

## 專案目的
* 資料集中並沒有各商品的類別資訊，因此本次專案目的為將資料集中的商品進行簡易分類,並利用此分類產生推薦商品給平台之客戶

## 開發工具與套件
* jupyter lab
* pandas, sklearn

## 實作方法
1. 清理資料，將metadata['rank']欄位中不屬於Personal Care的產品drop掉(512筆)
2. 將metada資料中的title與description合併並產生tf-idf之feature，因資料筆數太多，因此設定idf>200才會算為feature
3. 使用AgglomerativeClustering作為分類器，將所有商品分為20類,並建立商品類別
4. 使用2018-07-01(2月), 2018-05-01(4月), 2018-01-01(9月), 2016-01-01後的資料作為訓練資料
5. 將固定類別之訓練資料最熱門之產品並推薦給用戶
## 推薦結果

在數據中可以觀察到使用固定類別推薦之商品其recall落差很大，且暢銷商品幾乎集中在同一類別，在數據中的第9類不管在任何時間點都會比沒有篩選過的方法準確度還高，最高精準度為2018-07-01後的數據搭配第9類標籤的 0.142
