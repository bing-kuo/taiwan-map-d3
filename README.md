# taiwan-map-d3
Make a taiwan map using D3.js.

[直轄市、縣市界線(TWD97經緯度) | 政府資料開放平台](http://data.gov.tw/node/7442)

TopoJSON、Shapefile、GeoJSON都是地圖格式，政府網站下載下來的都是Shapefile，這次要做的是用D3.js畫地圖，用的是D3.js作者Mike提供的topojson的函式庫，他可以幫我們把讀取地圖資訊，我們在把他畫到svg上，之後做些特效，包括上色、標點、Zoom in、Zoom out、event，我環境是win10，下面是我自己的實現步驟：

Step1. 安裝[Node.js](https://nodejs.org/en/)
Step2. 安裝npm
Step3. 安裝topojson
```
sudo npm install -g topojson
```
Step4. 從上方網站抓下來的是SHP，所以我們要把他轉成TopoJSON，這裡需要注意的是，若SHP的格式為TWD97，務必要轉成WGS84格式，這部分我是靠[QGIS](http://www.qgis.org/en/site/)替我達成(QGIS->Layer->Save As)，確定是WGS84格式的SHP之後，用terminal到放置檔案的地方，
```
topojson -s 0.0000001 -o taiwan.json -p --shapefile-encoding big5 County_WGS84.shp
```
taiwan.json是我們想要輸出的檔案名稱，原始檔文字編碼為BIG5，County_WGS84.shp則是我們的SHP檔案名稱，執行後就得到我們的TopoJSON
Step5. 
```
taiwan-map-d3/
├── css/
│   └── style.css
└── img/
│   └── pin (1)~(7).png
├── map/
│   ├── WGS84/
│   │   ├── County_WGS84.dbf
│   │   ├── County_WGS84.prj
│   │   ├── County_WGS84.qpj
│   │   ├── County_WGS84.shp
│   │   └── County_WGS84.shx
│   └── taiwan.json
├── default.html
├── fill.html
├── index.html
├── marker.html
└── zoom.html
```
* map/WGS84/ 放置台灣地圖SHP原檔(WGS84格式)
* map/taiwan.json 台灣地圖TopoJSON檔
* index.html 為各功能的組合
* default.html 產生地圖
* fill.html 讀數值上色
* marker.html 標點
* zoom.html 放大縮小、滑動











