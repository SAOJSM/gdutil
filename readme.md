# Google Drive 百寶箱

> [與其他工具的對比](./compare.md)

## 目錄
- [<a href="./changelog.md">更新日志</a>](#更新日志)
- [demo](#demo)
- [English Version (thanks to <a href="https://github.com/roshanconnor123">@roshanconnor123</a>)](#english-version-thanks-to-roshanconnor123)
- [無需域名和nginx版](#無需域名和nginx版)
- [colab腳本（省去本地安裝步驟，直接網頁可用，感謝貢獻者<a href="https://github.com/orange2008">@orange2008</a>）](#colab腳本省去本地安裝步驟直接網頁可用感謝貢獻者orange2008)
- [一鍵安裝腳本(感謝 腳本制作者 <a href="https://github.com/vitaminx">@vitaminx</a>)](#一鍵安裝腳本感謝-腳本制作者-vitaminx)
- [繁體中文版（感謝貢獻者<a href="https://github.com/liaojack8/">@liaojack8</a>）](#繁體中文版感謝貢獻者liaojack8)
- [Docker 版（感謝貢獻者<a href="https://github.com/gdtool/">@gdtool</a>)](#docker-版感謝貢獻者gdtool)
- [常見問題](#常見問題)
- [搭建過程](#搭建過程)
- [功能簡介](#功能簡介)
- [環境配置](#環境配置)
- [依賴安裝](#依賴安裝)
- [Service Account 配置](#service-account-配置)
- [個人帳號配置](#個人帳號配置)
- [Bot配置](#bot配置)
- [補充說明](#補充說明)
- [專家設置](#專家設置)
- [注意事項](#注意事項)

## [更新日志](./changelog.md)

## demo
[https://drive.google.com/drive/folders/124pjM5LggSuwI1n40bcD5tQ13wS0M6wg](https://drive.google.com/drive/folders/124pjM5LggSuwI1n40bcD5tQ13wS0M6wg)

## English Version (thanks to [@roshanconnor123](https://github.com/roshanconnor123))
- [roshanconnor123/gd-utils](https://github.com/roshanconnor123/gd-utils)
- [roshanconnor123/Gdutils_Tgbot](https://github.com/roshanconnor123/Gdutils_Tgbot)

## 無需域名和nginx版
> 此版本無需域名和web服務即可使用tg機器人，大大簡化了配置過程，感謝貢獻者 [@dissipator](https://github.com/dissipator)

[https://github.com/dissipator/gd-utils](https://github.com/dissipator/gd-utils)

## colab腳本（省去本地安裝步驟，直接網頁可用，感謝貢獻者[@orange2008](https://github.com/orange2008)）
[https://colab.research.google.com/drive/1i1W9nAzgiDtfA_rmTBcpMpwxVUhwgLsq](https://colab.research.google.com/drive/1i1W9nAzgiDtfA_rmTBcpMpwxVUhwgLsq)

> 打開上面鏈接後，保存到自己的雲端硬盤（請一定要保存，因為上面的共享鏈接操作記錄所有人可見）

colab使用錄屏：[https://drive.google.com/drive/folders/19T37ARH7M1h67JGYanKp9LvORjJLEp_x](https://drive.google.com/drive/folders/19T37ARH7M1h67JGYanKp9LvORjJLEp_x)

這裡還有另一位網友[@iErics](https://github.com/iErics)制作的colab腳本，界面更加規整，功能也更完整些（比如可以選擇是否繼續任務等），使用方法大同小異：
[https://colab.research.google.com/github/iErics/gd-utils/blob/master/Colab_gd_utils.ipynb](https://colab.research.google.com/github/iErics/gd-utils/blob/master/Colab_gd_utils.ipynb)

## 一鍵安裝腳本(感謝 腳本制作者 [@vitaminx](https://github.com/vitaminx))
> 如果你沒有Linux操作經驗或者是新開的vps，可嘗試使用此腳本

請訪問 [https://github.com/vitaminx/gd-utils](https://github.com/vitaminx/gd-utils) 獲取安裝方法

## 繁體中文版（感謝貢獻者[@liaojack8](https://github.com/liaojack8/)）
[https://github.com/liaojack8/gd-utils-cht](https://github.com/liaojack8/gd-utils-cht)

> 目前項目處於起始階段，尚不支持 i18n(多語言) ，所以上面繁體版是hard code的fork，如果你有興趣讓本項目增加多語言支持，歡迎PR。

## Docker 版（感謝貢獻者[@gdtool](https://github.com/gdtool/))
[https://github.com/gdtool/gd-utils-docker](https://github.com/gdtool/gd-utils-docker)

## 常見問題
**[如果你遇到任務完成時拷貝成功的文件少於統計的文件數，請務必點擊查看](https://github.com/iwestlin/gd-utils/blob/master/changelog.md#%E9%87%8D%E8%A6%81%E6%9B%B4%E6%96%B02020-06-29)**

在命令行操作時有時會輸出Google內部報錯信息，這是正常情況，不會影響最終結果，因為程序對每個請求都有7次重試的機制。
如果經常出現404 file not found的錯誤，說明是sa的權限有問題，請點擊上面的鏈接查看解決辦法。

復制結束後，如果最後輸出的消息裡有 `未讀取完畢的目錄ID`，只需要在命令行執行上次同樣的拷貝命令，選continue即可繼續。

如果你復制完成以後，統計新的文件夾鏈接發現文件數比源文件夾少，說明Google正在更新數據庫，請給它一點時間，一般等半小時再統計數據會比較完整。

如果你使用tg機器人拷貝文件數超多的目錄時，發送拷貝命令以後，任務進度很久未開始，這是因為程序正在獲取源文件夾的所有文件信息。

**轉存的運行機制嚴格按照以下順序**：
```
1、獲取源文件夾所有文件信息
2、根據源文件夾的目錄結構，在目標文件夾創建目錄
3、所有目錄創建完成後，開始復制文件
```

如果源文件夾的文件數非常多（數十萬），在命令行操作時需要添加額外參數：（因為程序運行的時候會把文件信息保存在內存中，文件數太多的話容易內存占用太多被nodejs干掉）
```
 node --max-old-space-size=1024 count folder-id -S
```
這樣進程就能最大占用 1G 內存了，我最多測試過200萬+文件數的任務，1G 內存足以完成。

這裡還有一些網友的踩坑心得，如果你配置的時候也不小心掉進坑裡，可以進去找找有沒有解決辦法：  
- [ikarosone 基於寶塔的搭建過程](https://www.ikarosone.top/archives/195.html)
- [@greathappyforest 踩的坑](doc/tgbot-appache2-note.md)

## 搭建過程
機器人搭建過程錄屏：[https://drive.google.com/drive/folders/1Lu7Cwh9lIJkfqYDIaJrFpzi8Lgdxr4zT](https://drive.google.com/drive/folders/1Lu7Cwh9lIJkfqYDIaJrFpzi8Lgdxr4zT)

需要注意的地方：

- 視頻中省略了一個比較重要的步驟就是**從本地上傳service account授權文件到 sa 目錄下**，tg機器人的所有操作默認都是通過sa授權的，所以讀者請不要忘了
- 視頻中**nginx的配置裡，server_name就是你的二級域名，需要和cloudflare的設置一樣**的（mybbbottt），我分開錄的視頻所以沒做到一致。
- 還有省略的步驟就是注冊域名和把域名托管到cloudflare了，這一步網上太多資料了，甚至也有免費注冊（一年）域名的地方（ https://www.freenom.com/ ），具體教程請自行搜索

## 功能簡介
本工具目前支持以下功能：
- 統計任意（您擁有相關權限的，下同，不再贅述）目錄的文件信息，且支持以各種形式（html, tree, table, json）導出。
支持中斷恢復，且統計過的目錄（包括其所有遞歸子目錄）信息會記錄在本地數據庫文件中（gdurl.sqlite）
請在本項目目錄下命令行輸入 `./count -h` 查看使用幫助

- 拷貝任意目錄所有文件到您指定目錄，同樣支持中斷恢復。
支持根據文件大小過濾，可輸入 `./copy -h` 查看使用幫助

- 對任意目錄進行去重，刪除同一目錄下的md5值相同的文件（只保留一個），刪除同目錄下的同名空目錄。
命令行輸入 `./dedupe -h` 查看使用幫助

- 在 config.js 裡完成相關配置後，可以將本項目部署在（可正常訪問谷歌服務的）服務器上，提供 http 文件統計接口

- 支持 telegram bot，配置完成後，上述功能大多可以通過 bot 進行操作

## 環境配置
本工具需要安裝nodejs，客戶端安裝請訪問[https://nodejs.org/zh-cn/download/](https://nodejs.org/zh-cn/download/)，服務器安裝可參考[https://github.com/nodesource/distributions/blob/master/README.md#debinstall](https://github.com/nodesource/distributions/blob/master/README.md#debinstall)

建議選擇v12版本的node，以防接下來安裝依賴出錯。

如果你的網絡環境無法正常訪問谷歌服務，需要先在命令行進行一些配置：（如果可以正常訪問則跳過此節）
```
http_proxy="YOUR_PROXY_URL" && https_proxy=$http_proxy && HTTP_PROXY=$http_proxy && HTTPS_PROXY=$http_proxy
```
請把`YOUR_PROXY_URL`替換成你自己的代理地址

## 其他環境
nodejs本身是跨平台的，所以項目可以在各種操作系統上運行，下面的說明是針對Linux系統，如果你需要在 Windows 或 Android 上進行安裝，可以參考：
[https://github.com/roshanconnor123/gd-utils#installation (英文)](https://github.com/roshanconnor123/gd-utils#installation)

## 依賴安裝
- 命令行執行`git clone https://github.com/iwestlin/gd-utils && cd gd-utils` 克隆並切換到本項目文件夾下
- **執行 `npm install --unsafe-perm=true --allow-root` 安裝依賴**，部分依賴可能需要代理環境才能下載，所以需要上一步的配置

如果在安裝過程中發生報錯，請切換nodejs版本到v12再試。如果報錯信息裡有`Error: not found: make`之類的消息，說明你的命令行環境缺少make命令，可參考[這裡](https://askubuntu.com/questions/192645/make-command-not-found)或直接google搜索`Make Command Not Found`

如果報錯信息裡有 `better-sqlite3`，先執行 `npm config set unsafe-perm=true`
然後 `rm -rf node_module` 刪掉依賴目錄，最後再執行下`npm i`安裝試試。

依賴安裝完成後，項目文件夾下會多出個`node_modules`目錄，請不要刪除它，接下來進行下一步配置。

## Service Account 配置
強烈建議使用service account（後稱SA），因為機器人的所有操作默認都用的SA權限。
SA授權文件獲取方法請參見  
- 英文[https://github.com/xyou365/AutoRclone](https://github.com/xyou365/AutoRclone)
- 中文[http://blog.jialezi.net/?post=153](http://blog.jialezi.net/?post=153)

獲取到 SA 的 json 文件並將其加入團隊盤成員後，請將文件拷貝到gd-utils的 `sa` 目錄下。  
注意，AutoRclone 將 SA 加入 group 的腳本有點問題，可能會加入不完全，而gd-utils混入未授權的SA文件會導致嚴重的問題，暫時的解決方法是[批量驗證SA的有效性](https://github.com/iwestlin/gd-utils/blob/master/changelog.md#%E9%87%8D%E8%A6%81%E6%9B%B4%E6%96%B02020-06-29)

配置好 SA 以後，如果你不需要對個人盤下的文件進行操作，可跳過[個人帳號配置]這節，而且命令行執行命令的時候，記得帶上 `-S` 參數告訴程序使用SA授權進行操作。

## 個人帳號配置
- 命令行執行 `rclone config file` 找到 rclone 的配置文件路徑
- 打開這個配置文件 `rclone.conf`, 找到 `client_id`, `client_secret` 和 `refresh_token` 這三個變量，將其分別填入本項目下的 `config.js` 中，需要注意這三個值必須被成對的英文引號包裹，且引號後以英文逗號結尾，也就是需要符合JavaScript的[對像語法](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/Object_initializer)

如果你沒有配置過rclone，可以搜索`rclone google drive 教程`完成相關配置。

如果你的`rclone.conf`裡沒有`client_id`和`client_secret`，說明你配置rclone的時候默認用了rclone自己的client_id，連rclone自己[都不建議這樣做](https://github.com/rclone/rclone/blob/8d55367a6a2f47a1be7e360a872bd7e56f4353df/docs/content/drive.md#making-your-own-client_id)，因為大家共享了它的接口調用限額，在使用高峰期可能會觸發限制。

獲取自己的clinet_id可以參見這兩篇文章：[Cloudbox/wiki/Google-Drive-API-Client-ID-and-Client-Secret](https://github.com/Cloudbox/Cloudbox/wiki/Google-Drive-API-Client-ID-and-Client-Secret) 和 [https://p3terx.com/archives/goindex-google-drive-directory-index.html#toc_2](https://p3terx.com/archives/goindex-google-drive-directory-index.html#toc_2)

獲取到client_id和client_secret後，再次執行一遍`rclone config`，創建一個新的remote，**在配置過程中一定要填入你新獲取的clinet_id和client_secret**，就能在`rclone.conf`裡看到新獲取的`refresh_token`了。**注意，不能使用之前的refrest_token**，因為它對應的是rclone自帶的client_id

參數配置好以後，在命令行執行 `node check.js`，如果命令返回了你的谷歌硬盤根目錄的數據，說明配置成功，可以開始使用本工具了。

## Bot配置
如果要使用 telegram bot 功能，需要進一步配置。

首先在 [https://core.telegram.org/bots#6-botfather](https://core.telegram.org/bots#6-botfather) 根據指示拿到 bot 的 token，然後填入 config.js 中的 `tg_token` 變量。

然後獲取自己的 telegram username，這個username不是顯示的名稱，而是tg個人網址後面的那串字符，比如，我的tg個人網址是 `https://t.me/viegg` ，用戶名就是 `viegg`，獲取用戶名的目的是在代碼裡配置白名單，只允許特定的用戶調用機器人。將username填入 `config.js`裡的配置，像這樣：
`tg_whitelist: ['viegg']`，就代表只允許我自己使用這個機器人了。

如果想把機器人的使用權限分享給別的用戶，只需要改成：
```
tg_whitelist: ['viegg', '其他人的username'],
```

接下來需要將代碼部署到服務器上。
如果你一開始就是在服務器上配置的，可以直接執行`npm i pm2 -g`

如果你之前是在本地操作的，請在服務器上同樣重復一遍，配置好相關參數後，執行`npm i pm2 -g`安裝進程守護程序pm2

安裝好pm2之後，執行 `pm2 start server.js --node-args="--max-old-space-size=1024"`，代碼運行後會在服務器上監聽`23333`端口。

如果你啟動程序後想看運行日志，執行 `pm2 logs`

查看 pm2 守護的進程列表，執行 `pm2 l`

停止運行中的進程，執行 `pm2 stop 對應的進程名稱`

**如果你修改了代碼中的配置，需要 `pm2 reload server` 才能生效**。

> 如果你不想用nginx，可以將`server.js`中的`23333`改成`80`直接監聽80端口（可能需要root權限）

接下來可通過nginx或其他工具起一個web服務，示例nginx配置：
```
server {
  listen 80;
  server_name your.server.name;

  location / {
    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_pass http://127.0.0.1:23333/;
  }
}
```
配置好nginx後，可以再套一層cloudflare，具體教程請自行搜索。

檢查網站是否部署成功，可以命令行執行（請將YOUR_WEBSITE_URL替換成你的網址）
```
curl 'YOUR_WEBSITE_URL/api/gdurl/count?fid=124pjM5LggSuwI1n40bcD5tQ13wS0M6wg'
```
如果返回了`gd-utils 成功啟動`的消息，說明部署成功了。

最後，在命令行執行（請將`YOUR_WEBSITE`和`YOUR_BOT_TOKEN`分別替換成你自己的網址和bot token）
```
curl -F "url=YOUR_WEBSITE/api/gdurl/tgbot" 'https://api.telegram.org/botYOUR_BOT_TOKEN/setWebhook'
```
這樣，就將你的服務器連接上你的 telegram bot 了，試著給bot發送個 `/help`，如果它回復給你使用說明，那就配置成功了。

## 補充說明
在`config.js`文件裡，還有另外的幾個參數：
```
// 單次請求多少毫秒未響應以後超時（基准值，若連續超時則下次調整為上次的2倍）
const TIMEOUT_BASE = 7000

// 最大超時設置，比如某次請求，第一次7s超時，第二次14s，第三次28s，第四次56s，第五次不是112s而是60s，後續同理
const TIMEOUT_MAX = 60000

const PAGE_SIZE = 1000 // 每次網絡請求讀取目錄下的文件數，數值越大，越有可能超時，不得超過1000

const RETRY_LIMIT = 7 // 如果某次請求失敗，允許其重試的最大次數
const PARALLEL_LIMIT = 20 // 單個任務的網絡請求並行數量，可根據網絡環境調整

const DEFAULT_TARGET = '' // 必填，拷貝默認目的地ID，如果不指定target，則會拷貝到此處，建議填寫團隊盤ID，注意要用英文引號包裹
```
讀者可根據各自情況進行調整

## 專家設置
這一節面向更加注重安全的專家用戶，並假設讀者了解nodejs的基本語法

在 `config.js` 中，你可以額外設置兩個變量 `ROUTER_PASSKEY` 和 `TG_IPLIST` 來進一步保證接口安全。
```javascript
// 如果設置了這個值，那麼調用 /api/gdurl/count 這個接口必須攜帶一個叫 passkey 的query，且必須等於ROUTER_PASSKEY的值
// 如果不設置這個值，那麼默認關閉 /api/gdurl/count 這個接口的功能（因為觀察到很多用戶公開的貼出了自己的API地址……）
const ROUTER_PASSKEY = 'your-custom-passkey'

// 與你的服務器通信的tg服務器的 ip 地址，可以在pm2 logs 中看到
// 如果設置了這個值，那麼調用 /api/gdurl/tgbot 這個接口的IP地址必須是 TG_IPLIST 數組的其中之一
// 如果不設置這個值，則默認任何IP都可以調用此接口（考慮到後面還有個 tg username的白名單驗證）
const TG_IPLIST = ['tg-ip-address']

module.exports = {
  AUTH,
  PARALLEL_LIMIT,
  RETRY_LIMIT,
  TIMEOUT_BASE,
  TIMEOUT_MAX,
  LOG_DELAY,
  PAGE_SIZE,
  DEFAULT_TARGET,
  ROUTER_PASSKEY,
  TG_IPLIST
}
```

## 注意事項
gd-utlis（以及所有GD轉存工具）的原理是調用了[google drive官方接口](https://developers.google.com/drive/api/v3/reference/files/copy)

gd-utils比較快的原因在[與其他工具的對比](./compare.md)有具體闡述，概括來講，當它進行轉存任務時，不會向google服務器查詢目標文件是否已存在，因為它會把復制記錄存儲在本地數據庫，這樣就節省了查詢花費的時間，而查詢接口是google drive所有接口裡最耗時的。

這也就導致了gd-utils目前無法對已存在的文件進行增量更新，**除非文件之前就是它拷貝的**，由於它已經將記錄保存在本地，所以可以對之前的記錄進行增量更新。

目前尚不知道google是否會對接口做頻率限制，也不知道會不會影響google賬號本身的安全。

**請勿濫用，後果自負**
