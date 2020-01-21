D27：Scrapy 爬蟲流程 (2) - XPath + Item Pipeline
=====

Code
-----
[commit](https://github.com/BbsonLin/cupoy-pycrawler-2019/commit/7bcbad7f05047b1225a8a05f9fbe9e1d4535745d#diff-f13c9e47421cb5bbbd1f5b589eaf522c)

Output
-----

```
PS E:\Code\dev-projects\Cupoy\pycrawler\myproject> scrapy.exe crawl ptt_crawler 
2020-01-21 12:33:32 [scrapy.utils.log] INFO: Scrapy 1.8.0 started (bot: myproject)
2020-01-21 12:33:32 [scrapy.utils.log] INFO: Versions: lxml 4.4.2.0, libxml2 2.9.5, cssselect 1.1.0, parsel 1.5.2, w3lib 1.21.0, Twisted 19.10.0, Python 3.6.4 
(v3.6.4:d48eceb, Dec 19 2017, 06:54:40) [MSC v.1900 64 bit (AMD64)], pyOpenSSL 19.1.0 (OpenSSL 1.1.1d  10 Sep 2019), cryptography 2.8, Platform Windows-10-10.0.18362-SP0
2020-01-21 12:33:32 [scrapy.crawler] INFO: Overridden settings: {'BOT_NAME': 'myproject', 'EDITOR': 'D:\\Microsoft VS Code\\Code.exe', 'NEWSPIDER_MODULE': 'myproject.spiders', 'ROBOTSTXT_OBEY': True, 'SPIDER_MODULES': ['myproject.spiders']}
2020-01-21 12:33:32 [scrapy.extensions.telnet] INFO: Telnet Password: e265df176d348e32
2020-01-21 12:33:32 [scrapy.middleware] INFO: Enabled extensions:
['scrapy.extensions.corestats.CoreStats',
 'scrapy.extensions.telnet.TelnetConsole',
 'scrapy.extensions.logstats.LogStats']
2020-01-21 12:33:32 [scrapy.middleware] INFO: Enabled downloader middlewares:
['scrapy.downloadermiddlewares.robotstxt.RobotsTxtMiddleware',
 'scrapy.downloadermiddlewares.httpauth.HttpAuthMiddleware',
 'scrapy.downloadermiddlewares.downloadtimeout.DownloadTimeoutMiddleware',
 'scrapy.downloadermiddlewares.defaultheaders.DefaultHeadersMiddleware',
 'scrapy.downloadermiddlewares.useragent.UserAgentMiddleware',
 'scrapy.downloadermiddlewares.retry.RetryMiddleware',
 'scrapy.downloadermiddlewares.redirect.MetaRefreshMiddleware',
 'scrapy.downloadermiddlewares.httpcompression.HttpCompressionMiddleware',
 'scrapy.downloadermiddlewares.redirect.RedirectMiddleware',
 'scrapy.downloadermiddlewares.cookies.CookiesMiddleware',
 'scrapy.downloadermiddlewares.httpproxy.HttpProxyMiddleware',
 'scrapy.downloadermiddlewares.stats.DownloaderStats']
2020-01-21 12:33:32 [scrapy.middleware] INFO: Enabled spider middlewares:
['scrapy.spidermiddlewares.httperror.HttpErrorMiddleware',
 'scrapy.spidermiddlewares.offsite.OffsiteMiddleware',
 'scrapy.spidermiddlewares.referer.RefererMiddleware',
 'scrapy.spidermiddlewares.urllength.UrlLengthMiddleware',
 'scrapy.spidermiddlewares.depth.DepthMiddleware']
2020-01-21 12:33:32 [scrapy.middleware] INFO: Enabled item pipelines:
['myproject.pipelines.JSONPipline']
2020-01-21 12:33:32 [scrapy.core.engine] INFO: Spider opened
2020-01-21 12:33:32 [ptt_crawler] DEBUG: Start: open_spider ...
2020-01-21 12:33:32 [ptt_crawler] DEBUG: Create temp file for store JSON - E:\Code\dev-projects\Cupoy\pycrawler\myproject\crawled_data\.tmp.json.swp
2020-01-21 12:33:32 [ptt_crawler] DEBUG: End: open_spider ...
2020-01-21 12:33:32 [scrapy.extensions.logstats] INFO: Crawled 0 pages (at 0 pages/min), scraped 0 items (at 0 items/min)
2020-01-21 12:33:32 [scrapy.extensions.telnet] INFO: Telnet console listening on 127.0.0.1:6023
2020-01-21 12:33:33 [scrapy.core.engine] DEBUG: Crawled (404) <GET https://www.ptt.cc/robots.txt> (referer: None)
2020-01-21 12:33:33 [scrapy.core.engine] DEBUG: Crawled (200) <GET https://www.ptt.cc/bbs/NBA/M.1579141804.A.812.html> (referer: None)
2020-01-21 12:33:34 [py.warnings] WARNING: E:\Code\dev-projects\Cupoy\pycrawler\myproject\myproject\spiders\ptt_crawler.py:29: UserWarning: No parser was explicitly specified, so I'm using the best available HTML parser for this system ("lxml"). This usually isn't a problem, but if you run this code on another system, or in a different virtual environment, it may use a different parser and behave differently.

The code that caused this warning is on line 29 of the file E:\Code\dev-projects\Cupoy\pycrawler\myproject\myproject\spiders\ptt_crawler.py. To get rid of this warning, pass the additional argument 'features="lxml"' to the BeautifulSoup constructor.

  soup = BeautifulSoup(response.text)

2020-01-21 12:33:34 [ptt_crawler] DEBUG: Start: process_item ...
2020-01-21 12:33:34 [ptt_crawler] DEBUG: End: process_item ...
2020-01-21 12:33:34 [scrapy.core.scraper] DEBUG: Scraped from <200 https://www.ptt.cc/bbs/NBA/M.1579141804.A.812.html>
{'id': 'M.1579141804.A.812', 'url': 'https://www.ptt.cc/bbs/NBA/M.1579141804.A.812.html', 'author': 'Rambo (香帥)', 'title': '[Live] 獨行俠 @ 國王', 'date': 'Thu Jan 16 10:30:01 2020', 'content': '11:00 開打      獨行俠 VS 國王 NBATV 直播   NBA TODAY  1/15 2020   Starting Lineup Starting Lineup
     XX  L. Doncic   XX  D. Fox XX  T. Hardaway Jr.    XX  B. Hield XX  D. FinneySmith XX  H. Barnes XX  M. Kleber XX  N. Bjelica XX  D. Powell
                XX  H. Giles III null [Live] 獨行俠 @ 國王\n\nsac01 ~ sac03\n\n\n線上 BOX: http://cutt.us/ojMnC http://blog.xuite.net/baseballman/blog NBA每日 
線上高光  線上Top10 https://goo.gl/YGH7x7 Chrome extensions to Play Stream\n\n https://www.ptt.cc/bbs/NBA/M.1579141804.A.812.html', 'comments': [{'push_tag': '推', 'push_userid': 'mose56789', 'push_content': '求你王輕虐QQ', 'push_ipdatetime': '01/16 10:31'}, {'push_tag': '推', 'push_userid': 'ijk77692', 'push_content': '獨行俠贏的話 三樓立馬娶五樓做老婆', 'push_ipdatetime': '01/16 10:32'}, {'push_tag': '推', 'push_userid': 'bug198874', 'push_content': '好', 'push_ipdatetime': '01/16 10:32'}, {'push_tag': '推', 'push_userid': 'inthenchen', 'push_content': '可以不要嗎', 'push_ipdatetime': '01/16 10:32'}, {'push_tag': '→', 'push_userid': 'inthenchen', 'push_content': '沒搶到三樓，可惡', 'push_ipdatetime': '01/16 10:33'}, {'push_tag': '→', 'push_userid': 'bug198874', 'push_content': '所以
搶5樓來嫁給我，很好', 'push_ipdatetime': '01/16 10:33'}, {'push_tag': '推', 'push_userid': 'ijk77692', 'push_content': '樓上超閃 祝福百年好合', 'push_ipdatetime': '01/16 10:33'}, {'push_tag': '→', 'push_userid': 'inthenchen', 'push_content': '我是四樓好嗎？沒推到欸欸欸', 'push_ipdatetime': '01/16 10:34'}, {'push_tag': '→', 'push_userid': 'inthenchen', 'push_content': '阿阿阿不要阿阿阿', 'push_ipdatetime': '01/16 10:34'}, {'push_tag': '→', 'push_userid': 'bug198874', 'push_content': '來不及了，跪求77成全', 'push_ipdatetime': '01/16 10:34'}, {'push_tag': '推', 'push_userid': 'MK47', 'push_content': '這推文都不覺得尷尬= =?', 'push_ipdatetime': '01/16 10:35'}, {'push_tag': '→', 'push_userid': 'earldunn', 'push_content': '請勿在LIVE文裡公然放閃', 'push_ipdatetime': '01/16 10:38'}, {'push_tag': '→', 'push_userid': 'cpeyeshield', 'push_content': '走錯版了？', 'push_ipdatetime': '01/16 10:38'}, {'push_tag': '推', 'push_userid': 'wx190', 'push_content': '連在這都要被閃 可以不用這樣喔', 'push_ipdatetime': '01/16 10:39'}, {'push_tag': '推', 'push_userid': 'duece0927', 'push_content': '....', 'push_ipdatetime': '01/16 10:40'}, {'push_tag': '推', 'push_userid': 'qpeter', 'push_content': '這場難打 上次B2B對國王就沒贏', 'push_ipdatetime': '01/16 10:45'}, {'push_tag': '推', 'push_userid': 'wudirk', 'push_content': 'KP又不上了', 'push_ipdatetime': '01/16 10:46'}, {'push_tag': '推', 'push_userid': 'yasan1029', 'push_content': '三樓五樓太閃', 'push_ipdatetime': '01/16 10:50'}, {'push_tag': '噓', 'push_userid': 'attpp', 'push_content': '無聊推文', 'push_ipdatetime': '01/16 11:01'}, {'push_tag': '推', 'push_userid': 'lens82801', 'push_content': '推文在幹嘛 XD', 'push_ipdatetime': '01/16 11:03'}, {'push_tag': '推', 'push_userid': 'bcqqa7785', 'push_content': '國王隊的Logo怎麼變英超了==', 'push_ipdatetime': '01/16 11:18'}, {'push_tag': '噓', 'push_userid': 'mickeygg69', 'push_content': '尷尬推文 可
憐哪', 'push_ipdatetime': '01/16 11:21'}, {'push_tag': '→', 'push_userid': 'mose56789', 'push_content': '77這兩場的第一節好像都不少失誤？', 'push_ipdatetime': 
'01/16 11:28'}, {'push_tag': '噓', 'push_userid': 'lowl99', 'push_content': '國王隊常常一直吃鍋貼，不可能贏獨行俠', 'push_ipdatetime': '01/16 11:29'}, {'push_tag': '推', 'push_userid': 'mose56789', 'push_content': '上次交手你王就贏我犢了啊', 'push_ipdatetime': '01/16 11:30'}, {'push_tag': '噓', 'push_userid': 'qaz19wsx96', 'push_content': '77三分超鐵欸', 'push_ipdatetime': '01/16 11:31'}, {'push_tag': '推', 'push_userid': 'jj3414im', 'push_content': '沒空檔直接投當然鐵', 'push_ipdatetime': '01/16 11:36'}, {'push_tag': '推', 'push_userid': 'qpeter', 'push_content': '今天Q1打得比昨天有活力多了 不像B2B第二場', 'push_ipdatetime': '01/16 11:38'}, {'push_tag': '推', 'push_userid': 'oceanjy6662', 'push_content': '感覺小雞變壯很多', 'push_ipdatetime': '01/16 11:41'}, {'push_tag': '推', 'push_userid': 'jeff1013', 'push_content': 'Doncic三分命中率真的不合格', 'push_ipdatetime': '01/16 11:43'}, {'push_tag': '推', 'push_userid': 'matter224', 'push_content': '77最近都有數據不穩的狀況@@', 'push_ipdatetime': '01/16 11:53'}, {'push_tag': '推', 'push_userid': 'etjj', 'push_content': '請問今天沒有live連結嗎', 'push_ipdatetime': '01/16 11:55'}, {'push_tag': '推', 'push_userid': 'mose56789', 'push_content': '...live連結都禁半年了 老兄', 'push_ipdatetime': '01/16 11:59'}, 
{'push_tag': '推', 'push_userid': 'jeff1013', 'push_content': 'Doncic感覺今天又很可能大三元了', 'push_ipdatetime': '01/16 12:00'}, {'push_tag': '推', 'push_userid': 'qaz19wsx96', 'push_content': '77投3分對方都開始放了', 'push_ipdatetime': '01/16 12:01'}, {'push_tag': '推', 'push_userid': 'panda8888', 'push_content': 
'咖哩今天是哥哥模式', 'push_ipdatetime': '01/16 12:01'}, {'push_tag': '推', 'push_userid': 'k1230588', 'push_content': '71：67 這有在防守嗎', 'push_ipdatetime': '01/16 12:07'}, {'push_tag': '推', 'push_userid': 'cama', 'push_content': 'https://youtu.be/H-kA3UtBj4M', 'push_ipdatetime': '01/16 12:13'}, {'push_tag': '推
', 'push_userid': 'jeff1013', 'push_content': '第三節才剛開始沒多久就只差一助攻就大三元..', 'push_ipdatetime': '01/16 12:22'}, {'push_tag': '→', 'push_userid': 'jeff1013', 'push_content': '大三元了', 'push_ipdatetime': '01/16 12:24'}, {'push_tag': '推', 'push_userid': 'MK47', 'push_content': '大三元跟喝水一樣', 'push_ipdatetime': '01/16 12:25'}, {'push_tag': '推', 'push_userid': 'jardon', 'push_content': '19分鐘大三元', 'push_ipdatetime': '01/16 12:25'}, {'push_tag': '推', 'push_userid': 'potterpig', 'push_content': '大三元對77來說真的好容易...', 'push_ipdatetime': '01/16 12:25'}, {'push_tag': '→', 'push_userid': 'billy759552', 
'push_content': '國王現在那麼爛還要輕虐', 'push_ipdatetime': '01/16 12:26'}, {'push_tag': '→', 'push_userid': 'MK47', 'push_content': '看到上面J大推文才發現077打19分鐘就大三元了......', 'push_ipdatetime': '01/16 12:27'}, {'push_tag': '推', 'push_userid': 'jackal44748', 'push_content': 'THJ這節太罩了', 'push_ipdatetime': '01/16 12:29'}, {'push_tag': '推', 'push_userid': 'jeff1013', 'push_content': '兩邊防守都滿破的這場', 'push_ipdatetime': '01/16 12:30'}, {'push_tag': '推', 'push_userid': 'jeff1013', 'push_content': 'Doncic這場要超大型大三元了XDD', 'push_ipdatetime': '01/16 12:35'}, {'push_tag': '推', 'push_userid': 'yt010004', 'push_content': '這樣打下去 還真有機會30-20-20', 'push_ipdatetime': '01/16 12:36'}, {'push_tag': '推', 'push_userid': 'jj3414im', 'push_content': '隊友在幫忙補 
昨天的助攻啦', 'push_ipdatetime': '01/16 12:39'}, {'push_tag': '推', 'push_userid': 'oceanjy6662', 'push_content': '補助攻XD', 'push_ipdatetime': '01/16 12:39'}, {'push_tag': '推', 'push_userid': 'eastsea1', 'push_content': '天賜良緣！', 'push_ipdatetime': '01/16 12:40'}, {'push_tag': '推', 'push_userid': 'jackal44748', 'push_content': 'FOX真的有夠快', 'push_ipdatetime': '01/16 12:41'}, {'push_tag': '推', 'push_userid': 'jeff1013', 'push_content': '油雞比裁判還小一號XDD', 
'push_ipdatetime': '01/16 12:41'}, {'push_tag': '推', 'push_userid': 'joll150', 'push_content': '想看20-20-20', 'push_ipdatetime': '01/16 12:44'}, {'push_tag': '推', 'push_userid': 'elvisleeee', 'push_content': '這幾個判決都很偏國王阿', 'push_ipdatetime': '01/16 12:46'}, {'push_tag': '推', 'push_userid': 'SwissMiniGun', 'push_content': '好好穩住 我牛加油!', 'push_ipdatetime': '01/16 12:47'}, {'push_tag': '推', 'push_userid': 'MK47', 'push_content': '主場多少都會有一點吧 不
要很離譜就好了', 'push_ipdatetime': '01/16 12:47'}, {'push_tag': '推', 'push_userid': 'jeff1013', 'push_content': '羅國蝦', 'push_ipdatetime': '01/16 12:48'}, 
{'push_tag': '推', 'push_userid': 'jackal44748', 'push_content': 'JJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJ', 'push_ipdatetime': '01/16 12:48'}, {'push_tag': '推', 'push_userid': 'glay7566', 'push_content': 'JJJJJJJJJJJJJJJJJJJJ', 'push_ipdatetime': '01/16 12:49'}, {'push_tag': '推', 'push_userid': 'dy1278dy', 'push_content': 
'JJ!', 'push_ipdatetime': '01/16 12:49'}, {'push_tag': '推', 'push_userid': 'SwissMiniGun', 'push_content': 'JJ壓哨 爽喔', 'push_ipdatetime': '01/16 12:49'}, {'push_tag': '推', 'push_userid': 'seishin', 'push_content': '水', 'push_ipdatetime': '01/16 12:49'}, {'push_tag': '推', 'push_userid': 'money2011', 'push_content': 'JJJJJJJJJJJJJJJJJJ', 'push_ipdatetime': '01/16 12:49'}, {'push_tag': '推', 'push_userid': 'qpeter', 'push_content': '35 36 37', 'push_ipdatetime': '01/16 12:49'}, {'push_tag': '推', 'push_userid': 'lalacoco', 'push_content': 'JJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJ', 'push_ipdatetime': '01/16 12:49'}, 
{'push_tag': '推', 'push_userid': 'ohiyo104', 'push_content': 'JJJJJJJJJJJ', 'push_ipdatetime': '01/16 12:49'}, {'push_tag': '推', 'push_userid': 'snoobi', 'push_content': '壓哨！！', 'push_ipdatetime': '01/16 12:50'}, {'push_tag': '推', 'push_userid': 'oceanjy6662', 'push_content': '舒服', 'push_ipdatetime': '01/16 
12:50'}, {'push_tag': '推', 'push_userid': 'MK47', 'push_content': '好屌', 'push_ipdatetime': '01/16 12:50'}, {'push_tag': '→', 'push_userid': 'ericrobin', 'push_content': '每個人都在練logo shot嗎..', 'push_ipdatetime': '01/16 12:50'}, {'push_tag': '推', 'push_userid': 'jeff1013', 'push_content': '第四節國王爆打回一 
波', 'push_ipdatetime': '01/16 12:53'}, {'push_tag': '推', 'push_userid': 'SwissMiniGun', 'push_content': '目前助攻15次 平77自己單場最高', 'push_ipdatetime': '01/16 12:56'}, {'push_tag': '推', 'push_userid': 'jardon', 'push_content': '小牛也回敬6-0', 'push_ipdatetime': '01/16 13:00'}, {'push_tag': '推', 'push_userid': 'jeff1013', 'push_content': 'Fox的切入真的好難防', 'push_ipdatetime': '01/16 13:03'}, {'push_tag': '→', 'push_userid': 'jeff1013', 'push_content': '但罰球有 
夠悲劇', 'push_ipdatetime': '01/16 13:04'}, {'push_tag': '推', 'push_userid': 'jackal44748', 'push_content': '兩邊一起卡彈', 'push_ipdatetime': '01/16 13:07'}, {'push_tag': '推', 'push_userid': 'mose56789', 'push_content': 'Hield... LOL', 'push_ipdatetime': '01/16 13:07'}, {'push_tag': '推', 'push_userid': 'jeff1013', 'push_content': '回到10分差', 'push_ipdatetime': '01/16 13:07'}, {'push_tag': '推', 'push_userid': 'mose56789', 'push_content': '77被吃假的', 'push_ipdatetime': '01/16 13:08'}, {'push_tag': '推', 'push_userid': 'mose56789', 'push_content': 'THJJJJJJJJJ', 'push_ipdatetime': '01/16 13:10'}, {'push_tag': '推', 'push_userid': 'mose56789', 'push_content': 'QQ  進攻有點卡', 'push_ipdatetime': '01/16 13:13'}, {'push_tag': '噓', 'push_userid': 'jeff1013', 'push_content': '裁判', 'push_ipdatetime': '01/16 13:14'}, {'push_tag': '→', 'push_userid': 'jeff1013', 'push_content': '好吧 我錯了 重播好像有摸到', 'push_ipdatetime': '01/16 13:15'}, {'push_tag': '推', 'push_userid': 'mose56789', 'push_content': '挑戰了 這球的確有點怪Y', 'push_ipdatetime': '01/16 13:15'}, {'push_tag': '推', 'push_userid': 'lalacoco', 'push_content': '這個也算犯規  補哨吧?', 'push_ipdatetime': '01/16 13:16'}, {'push_tag': '→', 'push_userid': 'mose56789', 'push_content': '啊 有 
先拉到左手', 'push_ipdatetime': '01/16 13:16'}, {'push_tag': '推', 'push_userid': 'SwissMiniGun', 'push_content': '罰球好好穩住', 'push_ipdatetime': '01/16 13:17'}, {'push_tag': '推', 'push_userid': 'mose56789', 'push_content': '可以啦 今天才第一個MISS', 'push_ipdatetime': '01/16 13:17'}, {'push_tag': '→', 'push_userid': 'mose56789', 'push_content': '哇 HIELD這姿勢還進XD', 'push_ipdatetime': '01/16 13:18'}, {'push_tag': '→', 'push_userid': 'SwissMiniGun', 'push_content': 'XD我是罰之前推的', 'push_ipdatetime': '01/16 13:18'}, {'push_tag': '推', 'push_userid': 'LKN555', 'push_content': '看不懂運運運  完全沒打算出手?', 'push_ipdatetime': '01/16 13:18'}, {'push_tag': '→', 'push_userid': 'mose56789', 'push_content': '就傳球路線都被踩死了吧', 'push_ipdatetime': '01/16 13:19'}, {'push_tag': 
'→', 'push_userid': 'mose56789', 'push_content': '怎麼變跳球 LUL', 'push_ipdatetime': '01/16 13:19'}, {'push_tag': '→', 'push_userid': 'mose56789', 'push_content': '靠 差點QQ', 'push_ipdatetime': '01/16 13:19'}, {'push_tag': '推', 'push_userid': 'jeff1013', 'push_content': '國王這放槍送走比賽了', 'push_ipdatetime': '01/16 13:19'}, {'push_tag': '推', 'push_userid': 'richi', 'push_content': '拉鋸的時候沒有77以外的戰術嗎 一直讓他被包死', 'push_ipdatetime': '01/16 13:20'}, {'push_tag': '→', 'push_userid': 'jeff1013', 'push_content': '連續兩個籃下放槍有夠傷', 'push_ipdatetime': '01/16 13:20'}, {'push_tag': '→', 'push_userid': 'mose56789', 'push_content': '好險沒被補進', 'push_ipdatetime': '01/16 13:21'}, {'push_tag': '推', 'push_userid': 'LGHa', 'push_content': 'Powell打得很好', 'push_ipdatetime': '01/16 13:21'}, {'push_tag': '推', 'push_userid': 'luck945', 'push_content': '炮這幾個籃板搶得好', 'push_ipdatetime': '01/16 13:21'}, {'push_tag': '推
', 'push_userid': 'LKN555', 'push_content': '炮最近好罩', 'push_ipdatetime': '01/16 13:21'}, {'push_tag': '推', 'push_userid': 'SwissMiniGun', 'push_content': 
'現在還真的沒有 有能力確實執行戰術的..QQ', 'push_ipdatetime': '01/16 13:21'}, {'push_tag': '推', 'push_userid': 'SuperBMW', 'push_content': '小犢第四節真的很考
驗球迷心臟XDDDDD', 'push_ipdatetime': '01/16 13:22'}, {'push_tag': '推', 'push_userid': 'dotless', 'push_content': '沒有KP真的傷...', 'push_ipdatetime': '01/16 13:22'}, {'push_tag': '推', 'push_userid': 'qpeter', 'push_content': 'Powell連兩次重要的爭搶', 'push_ipdatetime': '01/16 13:22'}, {'push_tag': '推', 'push_userid': 'SwissMiniGun', 'push_content': '紀錄之夜  穩住!!', 'push_ipdatetime': '01/16 13:23'}, {'push_tag': '→', 'push_userid': 'SuperBMW', 'push_content': '剩下
27秒  到底誰會先持球 ==', 'push_ipdatetime': '01/16 13:24'}, {'push_tag': '推', 'push_userid': 'mose56789', 'push_content': '又MISS一顆 怕啦', 'push_ipdatetime': '01/16 13:26'}, {'push_tag': '→', 'push_userid': 'SwissMiniGun', 'push_content': '這種關鍵時刻  我們數據就是倒數 沒辦法XD', 'push_ipdatetime': '01/16 13:27'}, {'push_tag': '→', 'push_userid': 'mose56789', 'push_content': '怎麼有人在喊MVP LOL', 'push_ipdatetime': '01/16 13:27'}, {'push_tag': '→', 'push_userid': 'SwissMiniGun', 'push_content': 'THJ發球我很怕', 'push_ipdatetime': '01/16 13:27'}, {'push_tag': '推', 'push_userid': 'jeff1013', 'push_content': '結束', 'push_ipdatetime': '01/16 13:27'}, {'push_tag': '→', 'push_userid': 'SwissMiniGun', 'push_content': '還好有發出來', 'push_ipdatetime': '01/16 13:28'}, {'push_tag': '推
', 'push_userid': 'jj3414im', 'push_content': '關門每次都在劇場', 'push_ipdatetime': '01/16 13:28'}, {'push_tag': '推', 'push_userid': 'bokituto', 'push_content': '讚', 'push_ipdatetime': '01/16 13:28'}, {'push_tag': '→', 'push_userid': 'SwissMiniGun', 'push_content': '依舊很抖', 'push_ipdatetime': '01/16 13:28'}, {'push_tag': '推', 'push_userid': 'dotless', 'push_content': '咖哩弟關鍵時刻罰球真的常失手....', 'push_ipdatetime': '01/16 13:28'}, {'push_tag': '→', 'push_userid': 'mose56789', 'push_content': '這罰球真的來練球迷心臟的XDDDDD', 'push_ipdatetime': '01/16 13:28'}, {'push_tag': '推', 'push_userid': 'LKN555', 'push_content': '連罰球都不太會了XDDDDD', 'push_ipdatetime': '01/16 13:28'}, {'push_tag': '推', 'push_userid': 'cococheng2', 'push_content': '嚇不到我的', 'push_ipdatetime': '01/16 13:28'}, {'push_tag': '→', 'push_userid': 'SwissMiniGun', 'push_content': '25/15/17 出賽109場 20次大三元達陣 生涯助攻新高', 'push_ipdatetime': '01/16 
13:29'}, {'push_tag': '推', 'push_userid': 'jackal44748', 'push_content': '罰球還是不穩 最後好驚險', 'push_ipdatetime': '01/16 13:29'}, {'push_tag': '噓', 'push_userid': 'yugowolf', 'push_content': '罰球有夠爛的', 'push_ipdatetime': '01/16 13:29'}, {'push_tag': '推', 'push_userid': 'qpeter', 'push_content': '嚇死 總 
算是把這場B2B拿下了', 'push_ipdatetime': '01/16 13:29'}, {'push_tag': '推', 'push_userid': 'inthenchen', 'push_content': '乾，不會吧，獨行俠贏了', 'push_ipdatetime': '01/16 13:31'}, {'push_tag': '推', 'push_userid': 'ohiyo104', 'push_content': '真的是爛罰球...', 'push_ipdatetime': '01/16 13:31'}, {'push_tag': '推', 'push_userid': 'thibw13ug1', 'push_content': '每次第四節都不穩', 'push_ipdatetime': '01/16 13:31'}, {'push_tag': '→', 'push_userid': 'mose56789', 'push_content': 'LUL', 'push_ipdatetime': '01/16 13:32'}, {'push_tag': '推', 'push_userid': 'inthenchen', 'push_content': '不是說77打b2b必然慘淡竟然沒有？？', 'push_ipdatetime': '01/16 13:34'}], 'comment_stats': {'all': 131, 'count': 88, 'push': 94, 'boo': 6, 'neutral': 31}}
2020-01-21 12:33:34 [scrapy.core.engine] DEBUG: Crawled (200) <GET https://www.ptt.cc/bbs/NBA/M.1579569920.A.142.html> (referer: None)
2020-01-21 12:33:34 [ptt_crawler] DEBUG: Start: process_item ...
2020-01-21 12:33:34 [ptt_crawler] DEBUG: End: process_item ...
2020-01-21 12:33:34 [scrapy.core.scraper] DEBUG: Scraped from <200 https://www.ptt.cc/bbs/NBA/M.1579569920.A.142.html>
{'id': 'M.1579569920.A.142', 'url': 'https://www.ptt.cc/bbs/NBA/M.1579569920.A.142.html', 'author': 'dragon803 (好想去露營啊~)', 'title': '[情報] 76人跟湖人對Rose有興趣', 'date': 'Tue Jan 21 09:25:18 2020', 'content': 'The Los Angeles LakersPhiladelphia 76ers and multiple teams with championshi\np aspirations have expressed interest in trading for Detroit Pistons Guard Der\nrick Rose league sources told Yahoo Sports.\n\n湖人以及76人跟許多對爭冠有渴望的球隊對交易來活塞的控 
球後衛Derrick Rose有興趣\n\n The Clippers have checked in on Rose as well but it was more of a common exp\nloratory talk sources said.\n\n快艇也有在觀察Rose， 
不過這比較類似普通探索性的談話\n\n\nThe Lakers and Sixers are in search of point guard assistance for the stretch\nrun sources said\n\n湖人跟76人都在尋求控衛上
的補強\n\nWith the rash of injuries the Pistons have endured and Rose playing well the\nveteran guard last week asked for an extended role with more minutes sources\nsaid.\n\n隨著遇到傷兵的來襲活塞跟Rose表現優秀，這位後衛已經像求的要求擔任一個更多上場時\n間的重要角色\n\n\nRose is happy with the Pistons and isnt looking to be traded sources said\nbut the decision is beyond his control. He has one more year at 7.6 million r\nemaining on his contract.\n\nRose在活塞很開心並且 
沒有想被交易，不過控制權不在他手上，他還有再一年760萬的合\n約\n\nDetroit could opt to retool and restructure around Rose in the short term for\na playoff push. The Pistons are currently three games back of the eighthseede\nd Brooklyn Nets for the final playoff spot in the Eastern Conference.\n\n活塞有可能在短期內選擇
圍繞Rose進行改組跟結構調整來對季後賽進行衝次，因為他們距\n離老8的籃網只有3場落差\n\nThe Pistons are sellers as the Feb. 6 trade deadline approaches and that coul\nd result in the front office staying pat or undergoing drastic changes\n\n活塞在交易大限的2/6號前是賣家，但這可能會讓球隊不做出任何改變或是發生重大的改\n變
 https://reurl.cc/jdnQXD 這個消息是來自Chris Haynes\n\n這次是有力的可信消息了，所以很有參考價值\n https://www.ptt.cc/bbs/NBA/M.1579569920.A.142.html 其實retool and restructure兩個詞都有重組的意思，我不知道為啥他這裡要用2次，應\n該是要強調就是可以以Rose當中心短期衝次一下，因為季後賽沒很遠', 'comments': [{'push_tag': '推', 'push_userid': 'dcoog7880', 'push_content': '來我湖', 'push_ipdatetime': '01/21 09:26'}, {'push_tag': '→', 'push_userid': 'lens82801', 'push_content': '開
頭有點亂碼', 'push_ipdatetime': '01/21 09:26'}, {'push_tag': '推', 'push_userid': 'celtics1997', 'push_content': '第4個狀元！', 'push_ipdatetime': '01/21 09:26'}, {'push_tag': '→', 'push_userid': 'amyjoey', 'push_content': '英文有亂碼', 'push_ipdatetime': '01/21 09:27'}, {'push_tag': '推', 'push_userid': 'Yui5', 'push_content': '褲子要回家了QQ不過當家鄉英雄應該不錯', 'push_ipdatetime': '01/21 09:27'}, {'push_tag': '推', 'push_userid': 'KimJongUn', 'push_content': '西門單換
rose', 'push_ipdatetime': '01/21 09:28'}, {'push_tag': '→', 'push_userid': 'a3221715', 'push_content': '鉛筆換Rose', 'push_ipdatetime': '01/21 09:28'}, {'push_tag': '推', 'push_userid': 'nplin', 'push_content': '褲子換玫瑰', 'push_ipdatetime': '01/21 09:29'}, {'push_tag': '→', 'push_userid': 'ine810211', 'push_content': '四狀元！！紫金王朝', 'push_ipdatetime': '01/21 09:29'}, {'push_tag': '推', 'push_userid': 'cidcheng', 'push_content': '活塞要圍繞Rose建隊有點神奇 XD', 'push_ipdatetime': '01/21 09:30'}, {'push_tag': '→', 'push_userid': 'ken720331', 'push_content': '重點是活塞圍繞玫瑰重建', 'push_ipdatetime': '01/21 09:30'}, {'push_tag': '推', 'push_userid': 'Ashely0913', 'push_content': '玫瑰不想走就留啊', 'push_ipdatetime': '01/21 09:30'}, {'push_tag': '推', 'push_userid': 'CW4', 'push_content': 'DH跟Rose在湖人一起奪冠的話還蠻感人的', 'push_ipdatetime': '01/21 09:31'}, {'push_tag': '推', 'push_userid': 'a1773042', 'push_content': '湖人又來
啦', 'push_ipdatetime': '01/21 09:32'}, {'push_tag': '→', 'push_userid': 'leo19841010', 'push_content': '湖人對誰沒興趣才說新聞', 'push_ipdatetime': '01/21 09:34'}, {'push_tag': '推', 'push_userid': 'pneumo', 'push_content': '每次都有湖人', 'push_ipdatetime': '01/21 09:34'}, {'push_tag': '推', 'push_userid': 'CW4', 'push_content': 'mm 內文有講是short term', 'push_ipdatetime': '01/21 09:34'}, {'push_tag': '→', 'push_userid': 'ken720331', 'push_content': '湖人只是抬轎..', 'push_ipdatetime': '01/21 09:34'}, {'push_tag': '推', 'push_userid': 'purplebfly', 'push_content': 'LBJ跟ROSE化學效應不太好', 'push_ipdatetime': '01/21 09:34'}, 
{'push_tag': '→', 'push_userid': 'ine810211', 'push_content': '褲子送活塞 玫瑰來我湖', 'push_ipdatetime': '01/21 09:35'}, {'push_tag': '→', 'push_userid': 'CW4', 'push_content': '湖人想補有經驗的控衛還蠻正常的', 'push_ipdatetime': '01/21 09:35'}, {'push_tag': '推', 'push_userid': 'RushMonkey', 'push_content': '又有湖
人 XD', 'push_ipdatetime': '01/21 09:37'}, {'push_tag': '推', 'push_userid': 'linyi520', 'push_content': '我湖收！！', 'push_ipdatetime': '01/21 09:42'}, {'push_tag': '推', 'push_userid': 'gswsb', 'push_content': '拜託讓玫瑰去湖人圓夢吧', 'push_ipdatetime': '01/21 09:42'}, {'push_tag': '推', 'push_userid': 'wizozd38270', 'push_content': '每次都拿湖人抬轎', 'push_ipdatetime': '01/21 09:43'}, {'push_tag': '推', 'push_userid': 'totemist', 'push_content': '羅斯這次又要回到姆斯
旁邊了嗎', 'push_ipdatetime': '01/21 09:43'}, {'push_tag': '→', 'push_userid': 'totemist', 'push_content': '來我艇啦！', 'push_ipdatetime': '01/21 09:43'}, {'push_tag': '推', 'push_userid': 'MoWilliams', 'push_content': '可以不要去湖人嗎 去了其他隊還要打？', 'push_ipdatetime': '01/21 09:44'}, {'push_tag': '推', 'push_userid': 'RevanHsu', 'push_content': '一隊摸不到分區決賽地板 一隊有LBJ 很明顯要去哪了', 'push_ipdatetime': '01/21 09:44'}, {'push_tag': '→', 'push_userid': 'RevanHsu', 'push_content': '吧', 'push_ipdatetime': '01/21 09:44'}, {'push_tag': '推', 'push_userid': 'ilovekobe824', 'push_content': '去76不要湖人', 'push_ipdatetime': '01/21 09:46'}, {'push_tag': '推', 'push_userid': 'linearppt', 'push_content': '我七和湖人真是為難，我猜湖人啦。kzu後起之秀+AB', 'push_ipdatetime': '01/21 09:47'}, {'push_tag': '→', 'push_userid': 'linearppt', 'push_content': '活塞用的熟了。活塞留Rose是沒有意義', 'push_ipdatetime': '01/21 09:47'}, {'push_tag': '推', 'push_userid': 'owhfr69c', 'push_content': '湖人隊誰都有興趣，沒興趣那肯定是腿不夠粗', 'push_ipdatetime': '01/21 09:49'}, {'push_tag': '推', 'push_userid': 'Eddward', 'push_content': '我湖到底知不知道自己的側翼弱爆了...', 'push_ipdatetime': '01/21 09:49'}, {'push_tag': '推', 'push_userid': 'Y1999', 'push_content': '宇宙人', 'push_ipdatetime': '01/21 09:49'}, {'push_tag': '推', 'push_userid': 'rs813011', 'push_content': 'DR+AD+DH+LBJ', 'push_ipdatetime': '01/21 09:49'}, {'push_tag': '→', 'push_userid': 'BeanBryant', 'push_content': '湖人有乳摸傳出來的就幾乎沒有發生過 看看就好', 'push_ipdatetime': '01/21 09:50'}, {'push_tag': '推', 'push_userid': 'TheBatman', 'push_content': '03狀元+04狀元+08狀元+12狀元', 'push_ipdatetime': '01/21 09:52'}, {'push_tag': '推', 'push_userid': 'hank7218', 'push_content': '有機會四狀元開局嗎', 'push_ipdatetime': '01/21 09:53'}, {'push_tag': '→', 'push_userid': 'Toy17', 'push_content': '褲子可以回家啦', 'push_ipdatetime': '01/21 09:53'}, {'push_tag': '推', 'push_userid': 'laipyn', 'push_content': '給Rose一個冠軍', 'push_ipdatetime': '01/21 09:55'}, {'push_tag': 
'推', 'push_userid': 'a100205069', 'push_content': '去湖人幹嘛 上次去騎士被糟蹋得還不夠是不是', 'push_ipdatetime': '01/21 09:56'}, {'push_tag': '推', 'push_userid': 'bcqqa7785', 'push_content': 'rose跟當年真的有差很多嗎？', 'push_ipdatetime': '01/21 09:56'}, {'push_tag': '→', 'push_userid': 'kakain', 'push_content': 
'去湖人對雙方都不是好事 rose目前的優秀數據在湖人', 'push_ipdatetime': '01/21 09:59'}, {'push_tag': '→', 'push_userid': 'kakain', 'push_content': '是拿不出來的', 'push_ipdatetime': '01/21 09:59'}, {'push_tag': '推', 'push_userid': 'LKN555', 'push_content': '現在凱西用的好好的  換人用就難說了', 'push_ipdatetime': '01/21 09:59'}, {'push_tag': '推', 'push_userid': 'MK47', 'push_content': 'retool:更換主要武器 restruction:並以此重建', 'push_ipdatetime': '01/21 10:02'}, {'push_tag': '→', 'push_userid': 'MK47', 'push_content': '這作者寫作比較婉轉', 'push_ipdatetime': '01/21 10:03'}, {'push_tag': '推', 'push_userid': 'awxsd456', 'push_content': '我湖收，不給收追殺', 'push_ipdatetime': '01/21 10:04'}, {'push_tag': '推', 'push_userid': 'lala31446', 'push_content': 'kuzma換rose不會喔,整天只想用KCP+cook+戳丹這資源', 'push_ipdatetime': '01/21 10:05'}, {'push_tag': '→', 'push_userid': 'lala31446', 'push_content': '回收包騙其他隊', 'push_ipdatetime': '01/21 10:05'}, {'push_tag': '推', 'push_userid': 'als60907', 'push_content': 'Rose配草莓搭詹牧師和AD奪冠！？這畫面太美！', 'push_ipdatetime': '01/21 10:05'}, {'push_tag': '→', 'push_userid': 'als60907', 'push_content': '但是ROSE跟老詹搭起來真的堪憂', 'push_ipdatetime': '01/21 10:06'}, {'push_tag': '推', 'push_userid': 'demon616', 'push_content': 'Rose在騎士時不差吧？只是又傷了。', 'push_ipdatetime': '01/21 10:10'}, {'push_tag': '推', 'push_userid': 'bcqqa7785', 'push_content': '四狀元在總冠G7齊先發拿冠真的畫面超美', 'push_ipdatetime': '01/21 10:15'}, {'push_tag': '噓', 'push_userid': 'hioer', 'push_content': 'rose別來湖人雷', 'push_ipdatetime': '01/21 10:16'}, {'push_tag': '推', 'push_userid': 'rulDD', 'push_content': '什麼乳莫都有湖人的事', 'push_ipdatetime': '01/21 10:21'}, {'push_tag': '推', 'push_userid': 'whitemist', 'push_content': '大家不是都覺得湖人誰都要？', 'push_ipdatetime': '01/21 10:23'}, {'push_tag': '推', 'push_userid': 'ayuro', 
'push_content': '4狀元這畫面太美……………', 'push_ipdatetime': '01/21 10:28'}, {'push_tag': '噓', 'push_userid': 'corlos', 'push_content': '皇叔跟呂布會吵架的', 'push_ipdatetime': '01/21 10:28'}, {'push_tag': '推', 'push_userid': 'ATand', 'push_content': '我還是覺得Rose現在穩定打完自己剩下的球員生涯就好', 'push_ipdatetime': '01/21 10:29'}, {'push_tag': '→', 'push_userid': 'ATand', 'push_content': '好不容易才找到自己的路，別又被其他人的計畫打亂了', 'push_ipdatetime': '01/21 10:30'}, {'push_tag': '推', 'push_userid': 'rulDD', 'push_content': '玫瑰射的你', 'push_ipdatetime': '01/21 10:31'}, {'push_tag': '推', 'push_userid': 'dengjyun', 'push_content': '湖人前幾天怎麼不嘗試拿Ariza之類的', 'push_ipdatetime': '01/21 10:31'}, {'push_tag': '推', 'push_userid': 'Fezico', 'push_content': 'ARIZA退化
太多了...', 'push_ipdatetime': '01/21 10:32'}, {'push_tag': '推', 'push_userid': 'NanaoNaru', 'push_content': '湖人不用報 肯定有興趣', 'push_ipdatetime': '01/21 10:37'}, {'push_tag': '推', 'push_userid': 'kuaiphoto', 'push_content': 'Rose在活塞很開心沒有想被交易，部分原因也是底特律', 'push_ipdatetime': '01/21 10:38'}, {'push_tag': '→', 'push_userid': 'kuaiphoto', 'push_content': '離芝加哥並沒有太遠，他看家人很方便', 'push_ipdatetime': '01/21 10:38'}, {'push_tag': '推', 'push_userid': 'Lovesandy8', 'push_content': '送去湖人吧！不然rose要黑了', 'push_ipdatetime': '01/21 10:43'}, {'push_tag': '→', 'push_userid': 'shwkz', 'push_content': '褲子+Rondo 不知道能不能換到 再補個姊夫', 'push_ipdatetime': '01/21 10:50'}, {'push_tag': '→', 'push_userid': 'peterw', 'push_content': '皇叔這是要入蜀？
', 'push_ipdatetime': '01/21 10:50'}, {'push_tag': '推', 'push_userid': 'han10030079', 'push_content': '別去湖人拜託', 'push_ipdatetime': '01/21 10:53'}, {'push_tag': '→', 'push_userid': 'b19900127', 'push_content': '去湖人的話，肯定被酸史上最大團，超越湖人f5', 'push_ipdatetime': '01/21 10:55'}, {'push_tag': '推', 'push_userid': 'warm0808', 'push_content': '快去我湖圓夢', 'push_ipdatetime': '01/21 10:55'}, {'push_tag': '推', 'push_userid': 'chriscarryu', 'push_content': ' 
各位觀眾 4狀元', 'push_ipdatetime': '01/21 11:09'}, {'push_tag': '推', 'push_userid': 'EllisKidd', 'push_content': '圍繞玫瑰建隊 也太感人了', 'push_ipdatetime': '01/21 11:12'}, {'push_tag': '→', 'push_userid': 'shwkz', 'push_content': 'Rose換到 Rondo必掰', 'push_ipdatetime': '01/21 11:12'}, {'push_tag': '噓', 'push_userid': 'er800100', 'push_content': 'awx到底要反串多久', 'push_ipdatetime': '01/21 11:16'}, {'push_tag': '推', 'push_userid': 'boy50292', 'push_content': '來湖
人圓夢吧 我羅', 'push_ipdatetime': '01/21 11:17'}, {'push_tag': '噓', 'push_userid': 'yangshuwei', 'push_content': '去湖人跟LB同時在場上一定烙賽', 'push_ipdatetime': '01/21 11:18'}, {'push_tag': '推', 'push_userid': 'BeastJAY', 'push_content': '到時候一個弄不好  板上又要開始亂黑人了', 'push_ipdatetime': '01/21 11:25'}, {'push_tag': '推', 'push_userid': 'scatliu', 'push_content': '首位球隊板凳得分王可能沒了', 'push_ipdatetime': '01/21 11:26'}, {'push_tag': '噓', 'push_userid': 'qazii1992', 'push_content': '都有湖人 呵呵', 'push_ipdatetime': '01/21 11:28'}, {'push_tag': '推', 'push_userid': 'awxsd456', 'push_content': '誰跟你反串 
，愛之深責之切不行？', 'push_ipdatetime': '01/21 11:35'}, {'push_tag': '推', 'push_userid': 'iloveeve', 'push_content': '明顯反串還在凹 哈', 'push_ipdatetime': '01/21 11:40'}, {'push_tag': '→', 'push_userid': 'md1011', 'push_content': '像求的要求    衝次', 'push_ipdatetime': '01/21 11:41'}, {'push_tag': '推', 'push_userid': 'Kenshin0707', 'push_content': '去湖人就升級當巨頭了 雖然我覺得做自己就好 任何', 'push_ipdatetime': '01/21 11:55'}, {'push_tag': '→', 'push_userid': 'Kenshin0707', 'push_content': '消息出現湖人都不意外', 'push_ipdatetime': '01/21 11:55'}, {'push_tag': '推', 'push_userid': 'gametv', 'push_content': '如果有Rose的湖人球衣必買', 'push_ipdatetime': '01/21 12:00'}, {'push_tag': '推', 'push_userid': 'hiphopboy7', 'push_content': '只要有名氣的湖人都有興趣 包含自己的棄將', 
'push_ipdatetime': '01/21 12:01'}, {'push_tag': '推', 'push_userid': 'roger2623900', 'push_content': '如果要追求冠軍的話去湖人76都比留活塞好啦 沒強求', 'push_ipdatetime': '01/21 12:18'}, {'push_tag': '→', 'push_userid': 'roger2623900', 'push_content': '冠軍留活塞機會還是比較多', 'push_ipdatetime': '01/21 12:18'}, {'push_tag': '→', 'push_userid': 'Tawara', 'push_content': '湖人又有興趣啦', 'push_ipdatetime': '01/21 12:22'}, {'push_tag': '推', 'push_userid': 'kevin9841', 'push_content': '就跟洋基一樣啊 抬價用', 'push_ipdatetime': '01/21 12:25'}, {'push_tag': '→', 'push_userid': 'SCLPAL', 'push_content': '我用這匹赤兔馬，跟你換皇叔
  (?)', 'push_ipdatetime': '01/21 12:28'}, {'push_tag': '推', 'push_userid': 'rojjujj', 'push_content': 'AD  DH  ROSE  LBJ這四個拿冠的畫面太感人', 'push_ipdatetime': '01/21 12:28'}, {'push_tag': '推', 'push_userid': 'swingingbear', 'push_content': '他是說以rose為核心衝短期 不是長期的…', 'push_ipdatetime': '01/21 12:30'}, {'push_tag': '→', 'push_userid': 'swingingbear', 'push_content': '翻譯有落差', 'push_ipdatetime': '01/21 12:31'}], 'comment_stats': {'all': 99, 'count': 58, 'push': 63, 'boo': 5, 'neutral': 31}}
2020-01-21 12:33:34 [scrapy.core.engine] INFO: Closing spider (finished)
2020-01-21 12:33:34 [ptt_crawler] DEBUG: Start: close_spider ...
2020-01-21 12:33:34 [ptt_crawler] DEBUG: Save result at E:\Code\dev-projects\Cupoy\pycrawler\myproject\crawled_data\20200121T123332-20200121T123334.json       
2020-01-21 12:33:34 [ptt_crawler] DEBUG: End: close_spider ...
2020-01-21 12:33:34 [scrapy.statscollectors] INFO: Dumping Scrapy stats:
{'downloader/request_bytes': 843,
 'downloader/request_count': 3,
 'downloader/request_method_count/GET': 3,
 'downloader/response_bytes': 14190,
 'downloader/response_count': 3,
 'downloader/response_status_count/200': 2,
 'downloader/response_status_count/404': 1,
 'elapsed_time_seconds': 1.632376,
 'finish_reason': 'finished',
 'finish_time': datetime.datetime(2020, 1, 21, 4, 33, 34, 403044),
 'item_scraped_count': 2,
 'log_count/DEBUG': 15,
 'log_count/INFO': 10,
 'log_count/WARNING': 1,
 'response_received_count': 3,
 'robotstxt/request_count': 1,
 'robotstxt/response_count': 1,
 'robotstxt/response_status_count/404': 1,
 'scheduler/dequeued': 2,
 'scheduler/dequeued/memory': 2,
 'scheduler/enqueued': 2,
 'scheduler/enqueued/memory': 2,
 'start_time': datetime.datetime(2020, 1, 21, 4, 33, 32, 770668)}
2020-01-21 12:33:34 [scrapy.core.engine] INFO: Spider closed (finished)
```