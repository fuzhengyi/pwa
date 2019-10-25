# 一、PWA介绍

一个新的前端技术，PWA(全称：Progressive Web App)也就是说这是个渐进式的网页应用程序。乍一听，不太理解，通过整理资料总结如下：

web和app我们都懂，但是Progressive是什么意思呢？说起“Progressive渐进式”，想必大家或多或少听过一些关于Web应用“平稳退化，渐进增强”的设计理念，由于浏览器对于Web标准的跟进会有不同程度的滞后（更有甚者不但不跟进还有乱搞），很多优秀的新特性老旧浏览器并不支持，所以开发者有时候会采取渐进式的策略，充分利用新特性，为支持新特性的浏览器提供更完善的功能和更好的体验。PWA之P大约就是这个意思。

众所周知，web应用和native应用原本井水不犯河水，二者有着各自的应用场景和优势。但随着浮夸的移动互联网时代的到来，贪婪的人类想要取长补短兼顾两者的优点，乐此不疲的发明了一坨又一坨血统不纯的烂尾混合开发技术，此处就不一一举例，大家都懂。PWA是为了达到同样的目的的另一种方式，它绝不是革命性的技术，只是传统web应用向native应用的的又一次疯狂试探，也只是一次不大不小的进化而已。但区别于混合开发技术，PWA是血统纯正的web技术的自然延伸，背后有相关web标准支撑。 

这一次，PWA相对于传统web应用，主要在以下几个方面变得更强：

- 动感方面：在手机上，可以添加web应用到桌面，并可提供类似于native应用的沉浸式体验（翻译成人话就是可以隐藏浏览器的脑门）。这部分背后的技术是Manifest，虽然可以给带来全新的体验，但不是本文重点，就此别过。
- 性能方面：service worker具有拦截浏览器HTTP请求的超能力，搭配cachestorage, PWA可以提升web应用在网络条件不佳甚至离线时的用户体验和性能。
- 其他方面：推送通知，后台同步等可选的高级功能，这些功能也是利用service worker来实现的。

Google官网：https://developers.google.com/web/progressive-web-apps/

国内：https://lavas-project.github.io/pwa-book/

是Google在2015年提出，2016年6月才推广的项目。是结合了一系列现代web技术的组合，在网页应用中实现和原生应用相近的用户体验。

***特点(官网介绍)***

- Reliable(可靠的)

  当用户从手机主屏幕启动时，不用考虑网络的状态是如何，都可以立刻加载出PWA

- Fast(快速的)

  站在用户的角度考虑，如果一个网页加载速度有点长的话，那么用户就会放弃该网站，所以PWA在这一点上的做的很好，加载速度很快。

- Engaging(可参与的)

  PWA可以添加在用户的主屏幕上不需要从应用商店下载，他们通过网络应用程序Manifest file提供类似于APP的使用体验，并且还能进行推送通知。

***特性***

​	PWA 本质上还是 Web App，借助了新技术具备了一些 Native App 的特性，所以它兼具 Web App 和 Native App 的优点，同时在安全、体验和用户黏性三个方面都有很大的提升。

1. 渐进式 - 适用于所有浏览器，因为它是以渐进式增强作为宗旨开发的
2. 连接无关性 - 能够借助 Service Worker 在离线或者网络较差的情况下正常访问
3. 类原生应用 - 由于是在 App Shell 模型基础上开发，因此应具有 Native App 的交互，给用户 Native App 的体验
4. 持续更新 - 始终是最新的，无版本和更新问题
5. 安全 - 通过 HTTPS 协议提供服务，防止窥探，确保内容不被篡改
6. 可索引 - manifest 文件和 Service Worker 可以让搜索引擎索引到，从而将其识别为『应用』
7. 黏性 - 通过推送离线通知等，可以让用户回流
8. 可安装 - 用户可以添加常用的 Web App 到桌面，免去到应用商店下载的麻烦
9. 可链接 - 通过链接即可分享内容，无需下载安装

PWA 的这些新特性给 Web App 注入了活力，而 Native App 却没能很好的弥补自己的劣势。对于 Native App来说，最大的痛点是由于其天生封闭的基因，内容无法被索引，这会导致 Native App 很难被分发，例如，用户想知道红烧肉的做法，还需要先知道应用的名称，下载应用之后才能获取内容，这个流程十分不合理，根据 Google 的统计，用户每个月安装的应用个数约等于 0，再加上用户 80% 的时间被 Top3 的超级应用占据，应用分发成本也因此越来越高。相对于 Native App 的封闭，PWA 完全是开放的，PWA 的所有技术都是遵循开放的标准，因此能够被浏览器快速支持，被开发者接受

下表列出了传统 Web App，Native App 和 PWA 在各特性的对比。

|            | 是否可安装 | 是否可链接访问 | 用户体验 | 用户黏性 |
| :--------- | :--------- | :------------- | :------- | :------- |
| 传统 Web   | 无法安装   | 可链接访问     | 体验一般 | 黏性差   |
| Native App | 可安装     | 不可链接访问   | 体验好   | 黏性强   |
| PWA        | 可安装     | 可链接访问     | 体验好   | 黏性强   |

pwa如此优秀，现在已被国内一些大厂使用，例如新浪微博和饿了么的移动版本；

### PWA关键技术

Service Worker(可以理解为服务工厂)

Manifest(应用清单)

Push Notification(推送通知)

##### Service Worker

Service Worker是离线缓存文件。PWA技术使用的就是它！Service Worker是浏览器在后台独立于网页运行的脚本，它可以拦截网络请求，可以操作本地缓存，还可以接受服务器推送的离线消息，它的功能很丰富，并且 Service Worker 可扩展性很强，想象空间比较大，未来 PWA 很多的特性会基于 Service Worker 来设计，Service Worker作用于浏览器于服务器之间，相当于一个代理服务器。下面让我们来看一看service worker长什么样，以及如何让它跑起来：

```javascript
if('serviceWorker' in navigator){
    window.addEventListener('load', function(){
        navigator.serviceWorker.register('/service-worker.js').then(function(registration){
            console.log('我注册成功了')
        },function(err)=>{
        	console.log('我注册失败了')                                                            
        })
    })
}
```

***浏览器支持***

参考这个网址：https://lavas.baidu.com/ready

***特点***

目前只能在localhost和https环境下才能使用Service Worker，因为Service Worker权力比较大，能够直接截取和返回用户的请求，所以要考虑一下安全性问题。

1. 一个特殊的 worker 线程，独立于当前网页主线程，有自己的执行上下文
2. 一旦被安装，就永远存在，除非显示取消注册
3. 使用到的时候浏览器会自动唤醒，不用的时候自动休眠
4. 可拦截并代理请求和处理返回，可以操作本地缓存，如 CacheStorage，IndexedDB 等
5. 离线内容开发者可控
6. 能接受服务器推送的离线消息
7. 异步实现，内部接口异步化基本是通过 Promise 实现
8. 不能直接操作 DOM
9. 必须在 HTTPS 或本地localhost环境下才能工作

***事件机制***

***功能***

- 后台数据的同步
- 从其他域获取资源请求
- 接受计算密集型数据的更新，多页面共享该数据
- 客户端编译与依赖管理
- 后端服务的hook机制
- 根据URL模式，自定义模板
- 性能优化
- 消息推送
- 定时默认更新
- 地理围栏

***生命周期***

- Parsed(解析成功)：首次注册SW时，浏览器解决脚本并获得入口点，如果解析成功，就可以访问到SW注册对象，在这一点中我们需要在HTML页面中添加一个判断，判断该浏览器是否否支持SW。

- Installing(正在安装)：SW脚本解析完成之后，浏览器会尝试进行安装，installing中install事件被执行，如果其中有event.waitUntil()方法，则installing事件会一直等到该方法中的Promise完成之后才会成功，如果Promise被拒绝，则安装失败，SW会进入Redundant（废弃）状态。

- Installed/Waiting(安装成功/等待中)：如果安装成功，SW将会进入这个状态。

- Activating(正在激活)：处于waiting状态的SW发生以下情况，将会进入activating状态中：

  ​	当前已无激活状态的worker、SW脚本中的self.skipWaiting()方法被调用（ps:self是SW中作用于全局的对象，这个方法根据英文翻译过来也能明白什么意思啦，跳过等待状态）、用户已关闭S作用域下的所有页面，从而释放了当前出于激活状态的worker、超出指定时间，从而释放当前出于激活状态的worker

- Activated(激活成功)：该状态，其成功接收了document全面控制的激活态worker。

- Redundant(废弃)：这个状态的出现是由原因的，如果installing事件失败或者activating事件失败或者新的SW替换其成为激活态worker。installing事件失败和activating事件失败的信息我们可以在Chrome浏览器的DevTools中查看


##### Manifest

Web App Manifest是一个W3C规范，它定义了一个基于JSON的List。Manifest在PWA中的作用有：

1. 能够将你浏览的网页添加到你的手机屏幕上

2. 在Android上能够全屏启动，不显示地址栏（由于iphone手机的浏览器是safari，所以不支持哦）

3. 控制屏幕 横屏/竖屏 展示

4. 定义启动画面

5. 可以设置你的应用启动是从主屏幕启动还是从URL启动

6. 可以设置你添加屏幕上的应用程序图标、名字、图标大小

   ```javascript
   {
       "name":"一个PWA示例",
       "short_name":"PWA示例",
       "start_url":"/index.html",
       "display":"standalone",
       "background_color":"#fff",
       "theme_color":"#e73480",
       "icons":[
           {
               "src": "/Koala.jpg",
               "sizes": "120*120",
               "type":"image/png"
           }
       ]
   }
   ```

   

##### Push Notification

Push和Notification是两个不同的功能，涉及到两个API。

Notification是浏览器发出的通知消息。

Push和Notification的关系，Push：服务器端将更新的信息传递给SW,Notification:SW将更新的信息推送给用户。

### pwa发展与未来

#### pwa的发展

**现阶段使用案例**：新浪微博移动版、饿了么移动版、阿里速卖通（AliExpress）、Flipkart

**标准的支持**：PWA 采用的最新技术，当前浏览器还没有达到完全支持的程度，很多技术在 W3C 还没有定稿，不过这也意味着这些技术的还有很大的想象空间。

根据 [Can I Use](https://caniuse.com/) 的统计（包括 PC 和移动端，截至 2019 年 4 月 2 日），PWA 的关键技术在浏览器中的支持度如下：

- Web App Manifest 的支持度达到 80.63%。
- Service Worker 的支持度达到 89.84%。
- Notifications API 的支持度达到 75.17%。
- Push API 的支持度达到 78.06%。

随着标准的进一步完善，国内外各大浏览器都会逐步支持，拥抱标准。Chrome 自不必说，Apple 从 iOS 11.3 版本开始在 Safari 上支持 Service Worker，iOS 12.2 版本修复了 PWA 很多致命的体验问题，支持了 Web Share API 等。可见大家都在拥抱标准，拥抱开放。

Can I Use 的统计由于一些原因在国内不是很适用，为此百度 Web 生态团队维护了一份列表，开发者可以在上面查看国内各主流浏览器对 PWA 主要技术的支持程度，https://lavas.baidu.com/ready。

#### pwa的未来

从 Google 最初提出 PWA 到现在，PWA 已经有不小的改变了，这就是 Web 的魅力，遵循标准且完全开放的魅力，来自世界各地的开发者参与标准的制定，它还在不断进化，Web 即使已经 30 岁了，它还依旧是被广泛应用的技术之一。

关注 Web 标准化的开发者会在标准文档里发现很多有意思的提案，有 Web 蓝牙、Web XR 等，在 [TPAC Lyon 2018](https://www.w3.org/2018/10/TPAC/) 上，Intel 的开发者演示了他们开发的 Web Machine Learning 的 DEMO，Web 也能直接利用 NPU 来进行深度学习的计算。

一年前主流浏览器还不支持pwa中的关键技术Service Worker，目前Service Worker已经被大多数浏览器所认可。

### pwa示例

***准备***

我们先创建一个关于PWA的项目文件夹，

进入文件夹我们准备一张120*120的图片一张，作为我们的应用程序图标。

创建一个index.html文件

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <link rel="stylesheet" href="main.css">
    <link rel="manifest" href="manifest.json">
    <script src="./jquery/dist/jquery.js"></script>
</head>
<body>
    <h3>Hello PWA</h3>
</body>
<script>
    //检查浏览器是否支持SW
    if(navigator.serviceWorker != null){
        navigator.serviceWorker.register('./sw.js')
        .then(function(registartion){
            console.log('支持sw：',registartion.scope)
        })
    }

    $.ajax({
        type:"get",
        url:"http://localhost:65535/test/getList",
        success:function(data){
            console.log(data)
        },
        error:function(err){
            console.log(err)
        }
    })

    setTimeout(() => {
        const img = new Image();
        img.src = './qe.jpg';
        document.body.appendChild(img);
    }, 3000);

</script>
</html>
```

创建一个main.css文件

```
h3{
    color: #e73480
}
```

创建一个mainifest.json文件

```
{
    "name":"一个PWA示例",
    "short_name":"PWA示例",
    "start_url":"/index.html",
    "display":"standalone",
    "background_color":"#fff",
    "theme_color":"#e73480",
    "icons":[
        {
            "src": "/Koala.jpg",
            "sizes": "120*120",
            "type":"image/png"
        }
    ]
}
```

创建一个sw.js文件

```
/* self.addEventListener('fetch', function (event) {
    event.respondWith(
        new Response('bad111123') //这个SW注册好以后，整个SW控制站点的所有请求返回的都将是字符串"bad"，包括页面的HTML
    );
});*/
console.log(self) 




var cacheStorageKey = 'cachesName'//缓存的键名
var cacheList = [
    // 注册成功后要立即缓存的资源列表
    '/',
    'index.html',
    'main.css',
    'kl.jpg'
]

// 当浏览器解析完sw文件时触发install事件，install 事件是 SW 触发的第一个事件，并且仅触发一次。
self.addEventListener('install', function (e) {
    // install事件中一般会将cacheList中要缓存的内容通过addAll方法，拉一遍放入caches中
    e.waitUntil(
        caches.open(cacheStorageKey)
        .then(function (cache) {
            return cache.addAll(cacheList)
        })
        .then(() => self.skipWaiting())
    )
})

// 激活时触发activate事件
self.addEventListener('activate', function (e) {
    // active事件中通常做一些过期资源释放的工作，匹配到就从caches中删除
    var cacheDeletePromises = caches.keys()
    .then(cacheNames => {
        return Promise.all(cacheNames.map(name => {
            if (name !== cacheStorageKey) {
                return caches.delete(name);
            } else {
                return Promise.resolve();
            }
        }));
    });
    e.waitUntil(
        Promise.all([cacheDeletePromises])
    )
})

self.addEventListener('fetch', function (e) {
    // 在此编写缓存策略
    console.log(e.request)
    console.log(e.request.url)
    const url = new URL(e.request.url);
    //如果是同域并且请求的是 qe.jpg 的话，那么返回 kl.jpg
    if (url.origin == location.origin && url.pathname == '/qe.jpg') {
        e.respondWith(caches.match('/kl.jpg'));
    }
})



// 其实所有站点SW的install和active都差不多， 无非是做预缓存资源列表， 更新后缓存清理的工作， 逻辑不太复杂， 而重点在于fetch事件。 上面的代码， 我把fetch事件的逻辑省略了， 因为如果认真写的话， 太多了， 而且也不利于讲明白缓存策略这件事。 想象一下， 你需要根据不同文件的扩展名把不同的资源通过不同的策略缓存在caches中， 各种css， js， html， 图片， 都需要单独搞一套缓存策略， 你就知道fetch中需要写多少东西了吧。

// install 事件是 SW 触发的第一个事件， 并且仅触发一次。
// installEvent.waitUntil() 接收一个 Promise 参数， 用它来表示 SW 安装的成功与否
// SW 在安装成功并激活之前， 不会响应 fetch或push等事件。
// 默认情况下， 页面的请求（ fetch） 不会通过 SW， 除非它本身是通过 SW 获取的， 也就是说， 在安装 SW 之后， 需要刷新页面才能有效果。
// clients.claim() 可以改变这种默认行为。
```

# 二、 Service Worker

***Service Worker***

Service Worker 是 PWA 技术基础之一，脱离浏览器主线程的特性，使得 Web App 离线缓存成为可能，更为后台同步、通知推送等功能提供了思路。Service Worker 和缓存之间的关系，可以理解为 Service Worker 是一种调度机制，类似于铁路调度系统，而缓存则类似于具体的火车，可以是绿皮车、动车、高铁等，所有的车都是基于这一套铁路调度系统在工作的，使用 Service Worker 可以在不同场景下更加精细化控制缓存。

#### Service Worker 简介

丢失网络连接是一个困扰 Web 用户多年的难题，即使是世界上最好的 Web App，如果因为网络原因访问不了它，那体验也是非常糟糕的。本小节要介绍的 Service Worker 能提供一种良好的统筹机制对资源缓存和网络请求进行缓存和处理，是 PWA 实现离线可访问、稳定访问、静态资源缓存的一项重要技术。

通常所讲的 Service Worker 指的是 Service Worker 线程。了解浏览器工作原理的开发者都知道浏览器中执行的 JavaScript 文件是运行在一个单一线程上，称之为 **主线程**。而 Service Worker 是一种独立于浏览器主线程的 **工作线程**，与当前的浏览器主线程是完全隔离的，并有自己独立的执行上下文（context）。

首先借一个简单的例子来了解一下什么是 Service Worker，假如现在有一个最简单的前端项目 serviceWorkerDemo ，目录结构如下：

```javascript
.
└── serviceWorkerDemo
    ├── index.html
    └── sw.js
```

`index.html` 文件的内容如下：

```
<!DOCTYPE html>
  <head>
    <title>Service Worker Demo</title>
  </head>
  <body>
    <script>
      navigator.serviceWorker.register('./sw.js')
    </script>
  </body>
</html>
```

HTML5 提供的一个 Service Worker API，能够进行 Service Worker 线程的注册、注销等工作，在该示例中，通过 `navigator.serviceWorker.register()` 方法就能够注册一个 Service Worker，在当前的浏览器主线程的基础上新起一个 Service Worker 线程。

在示例项目的目录中还有一个 `sw.js`，有时候开发者会将这个 JavasScript 脚本文件称之为 Service Worker，这种说法不是很严谨，通常将可以被 `navigator.serviceWorker.register()` 方法注册的 JavaScript 文件称之为 Service Worker 文件，可以是任何命名，在这个示例中命名为 `sw.js`，其内容就是在 Service Worker 线程上下文中执行的内容（如果文件为空代表 worker 线程什么也不会做），由于 Service Worker 线程是独立于主线程的工作线程，所以在 `sw.js` 中的任何操作都不会影响到主线程

接下来，我们来运行一下第一章的简易的示例，可以借助 local-web-server 工具在示例项目根目录下启动一个本地服务器，帮助我们查看一下 Service Worker 的具体运行状态，如下操作：

```
npm install -g local-web-server
ws
```

使用 Chrome 浏览器访问示例站点 `localhost:8000` 的，可以在开发者模式的 `Applications > Service Worker` 面板中看到当前 Service Worker 线程的状态，在完成了 Service Worker 注册安装之后，结果如下图所示：

![1571729019601](C:\Users\zhengyi.fu\AppData\Roaming\Typora\typora-user-images\1571729019601.png)

当调节当前的网络状态为「离线」，依然可以看到 Service Worker 还是生效状态，通过这个例子可以发现，Service Worker 不仅是一个独立于主线程的的一个工作线程，并且还是一个可以在离线环境下运行的工作线程，这样就为 PWA 的离线与缓存功能提供了可行性基础。

**为什么有 Service Worker**

在了解了 Service Worker 是一个工作线程的本质之后，接下来继续了解一下为什么会有 Service Worker 这个技术出现呢？W3C（国际万维网联盟）早在 2014 年 5 月就提出了 Service Worker HTML5 API 草案，用来进行 Web 资源和请求的持久离线缓存。Service Worker 的来历可以从两个方面来介绍。

一方面，浏览器中的 JavaScript 都是运行在一个单一主线程上的，在同一时间内只能做一件事情。随着 Web 业务不断复杂，在 JavaScript 中的代码逻辑中往往会出现很多耗资源、耗时间的复杂运算过程。这些过程导致的性能问题在 Web App 日益增长的复杂化过程中更加凸显出来。所以 W3C 提出了 Web Worker API 来专门解放主线程，Web Worker 是脱离在主线程之外的工作线程，开发者可以将一些复杂的耗时的工作放在 Web Worker 中进行，工作完成后通过 postMessage 告诉主线程工作的结果，而主线程通过 onmessage 得到 Web Worker 的结果反馈，从而释放了主线程的性能压力。

**Service Worker 的特点**

Service Worker 功能虽然强大，但是使用 Service Worker 还是有一定的条件以及一些专有的特点的。

出于安全的考虑 Service Worker **必须运行在 HTTPS 协议下**，Github 提供的 [git page](https://pages.github.com/)是个用来测试 Service Worker 的好地方，因为它就直接就支持 HTTPS，直接就可以测试静态页面和静态资源，为了便于本地开发，`localhost`、`127.0.0.1` 这种非 HTTPS 协议也被浏览器认为是安全源。

Service Worker 线程**有自己完全独立的执行上下文**。**一旦被安装成功就永远存在，除非线程被程序主动解除**，而且 Service Worker 在访问页面的时候可以直接被激活，如果关闭浏览器或者浏览器标签的时候会自动睡眠，以减少资源损耗。

Service Worker 是完全异步实现的，内部的接口的异步化都是通过 Promise 实现，并且在 Service Worker 中**不能直接操作 DOM**，出于安全和体验的考虑，UI 的渲染工作必须只能在主线程完成。

Service Worker **可以拦截并代理请求，可以处理请求的返回内容**，可以持久化缓存静态资源达到离线访问的效果，和 ApplicationCache 不同，Service Worker 的所有的离线内容**开发者完全可控**，甚至是可以控制动态请求，第三方静态资源等。

由于 Service Worker 可以离线并且在后台工作，所以可以进行 **推送消息**（第六章会详细说明）、**后台同步**资源等功能，在不久的将来，利用 Service Worker 的这一特性，甚至可以衍生出更多的 Web App 原生化的功能。

**浏览器支持程度**

可以在https://jakearchibald.github.io/isserviceworkerready/或https://caniuse.com/网站上看浏览器的支持程度，目前来看，浏览器对Service Worker的支持程度已经达到90%；其中 Chrome 作为开路先锋早早的在 V40 版本就已经支持 Service Worker，并在 Devtools 中还提供了完善的 Debug 方案，Apple 方面从 MacOS Safari 11.1 和 iOS Safari 11.3 开始全面支持，IE Edge 从 17 版本开始也全面支持。

目前 Apple 和微软都已经支持了 Service Worker，所以对于 “离线可访问” 这样的 PWA 特性来讲，几乎可以在任何的现代浏览器中被实现。

由于 Service Worker 的功能是渐进式的，如果浏览器不支持 Service Worker，在架构设计上 Web App 也应该能够正常运行，为了防止 JavaScript 报错，所以通常在注册之前需要进行嗅探处理。修改 serviceWorkerDemo 的 `index.html` 代码如下所示：

```
<!DOCTYPE html>
  <head>
    <title>Service Worker Demo</title>
  </head>
  <body>
    <script>
      if ('serviceWorker' in navigator) {
        navigator.serviceWorker.register('./sw.js')
      }
    </script>
  </body>
</html>
```

#### Service Worker 注册

下面主要会介绍如何为 Web App 注册一个 Service Worker、在不同的项目架构下注册 Service Worker 的方法、Service Worker 注册的一些细节和注意点等。

**作用域**

Service Worker 是有自己的作用域的，Service Worker 作用域是一个 URL path 地址，指的是 Servcie Worker 能够控制的页面的范围，例如：某个 Service Worker 的作用域为 `https://somehost/a/b/`，那这个 Service Worker 能控制 `https://somehost/a/b/` 目录下的所有页面，可以包含下面列出的页面：

- `https://somehost/a/b/index.html`
- `https://somehost/a/b/c/index.html`
- `https://somehost/a/b/anothor.html`
- ...

所谓的 “控制页面” 指的是 Service Worker 可以处理这些页面里面的资源请求和网络请求，然后通过 Service Worker 自身的调度机制构建离线缓存策略。如果页面不在 Service Worker 的作用域范围内，Service Worker 就无法处理页面的任何资源或请求。

为了加深对 Service Worker 作用域的理解，接下来还是来看下 serviceWorkerDemo 这个示例，在 `index.html` 中修改一下代码如下所示：

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
     <script>
         if ('serviceWorker' in navigator) {
            navigator.serviceWorker.register('./sw.js')
            .then(reg => {
                console.log(reg)
            })
         }
     </script>
</body>
</html>
```

首先从上面代码可以看出 `navigator.serviceWorker.register()` 方法返回的是一个 Promise，这个 Promise 中 resolve 返回的是 Service Worker 注册成功后返回的 ServiceWorkerRegistration 对象。运行之后将这个对象打印出来的结果如下图所示。

![1571898635376](C:\Users\zhengyi.fu\AppData\Roaming\Typora\typora-user-images\1571898635376.png)

ServiceWorkerRegistration 对象中的 scope 的值就是当前的 Service Worker 的作用域，在这个示例中为 `http://127.0.0.1:8000/`。

为了更直观的看到 Service Worker 作用域的工作原理，接下来新建一个 serviceWorkerScopeDemo 项目，项目目录结构如下：

```
.
└── serviceWorkerScopeDemo
    ├── a
    │   └── b
    │       └── sw.js
    └── index.html
```

将 `sw.js` 放入 `/a/b/` 目录下，将 `index.html` 中的注册 Service Worker 逻辑修改一下，代码如下所示：

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
    <script>
        if ('serviceWorker' in navigator) {
            navigator.serviceWorker.register('./a/b/sw.js')
                .then(reg => {
                    console.log(reg.scope)
                    // http://127.0.0.1:8000/a/b/
                })
        }
    </script>
</body>
</html>
```

将 `navigator.serviceWorker.register()` 方法的 Service Worker 文件 URL 改成 `./a/b/sw.js`，运行结果打印出来的 scope 结果为 `http://127.0.0.1:8000/a/b/`。通常情况下在注册 `sw.js` 的时候会忽略 Service Worker 作用域的问题，Service Worker 默认的作用域就是注册时候的 path, 例如：Service Worker 注册的 path 为 `/a/b/sw.js`，则 scope 默认为 `/a/b/`。

也可以通过在注册时候在 `navigator.serviceWorker.register()` 方法中传入 `{scope: '/some/scope/'}` 参数的方式自己指定作用域，如下代码所示：

```
<script>
   if ('serviceWorker' in navigator) {
      navigator.serviceWorker.register('./a/b/sw.js', {
        // 手动指定一个作用域
        scope: '/a/b/c/'
      }).then(reg => {
        console.log(reg.scope)
        // http://127.0.0.1:8000/a/b/c/
      })
   }
</script>
```

将 scope 配置 `{scope: '/a/b/c/'}` 传入 `navigator.serviceWorker.register()` 方法，运行后打印出来的内容为 `http://127.0.0.1:8000/a/b/c/`。也就是说可以通过参数为 Service Worker 指定一个作用域。当然，这个自定义作用域是不可以随意指定的，可以通过如下代码修改 `index.html`：

```
<!DOCTYPE html>
  <head>
    <title>Service Worker Scope Demo</title>
  </head>
  <body>
    <script>
      if ('serviceWorker' in navigator) {
        navigator.serviceWorker.register('./a/b/sw.js', {
          scope: '/a/'
        }).then(reg => {
          console.log(reg.scope)
        })
      }
    </script>
  </body>
</html>



/*注意： 类似于 Ajax 的跨域请求可以通过对请求的 Access-Control-Allow-Origin 设置，我们也可以通过服务器对 sw.js 这个文件的请求头进行设置，就能够突破作用域的限制，只需要在服务端对sw.js 请求设置 Service-Worker-Allowed 请求头为更大控制范围或者其他控制范围的 scope 即可。如：Service-Worker-Allowed: /a/。*/
```

上面代码将作用域指定为 `/a/`，运行后浏览器会报错，报错的内容如下图所示。

![1571904744555](C:\Users\zhengyi.fu\AppData\Roaming\Typora\typora-user-images\1571904744555.png)

通过报错信息知道 `sw.js` 文件所在的 URL 的 path 是 `/a/b/`，则默认的作用域和最大的作用域都是 `/a/b/`，不允许指定超过最大作用域范围的 `/a/` 为作用域。

通俗的讲，Service Worker 最多只能在 Service Worker 文件 URL path 范围内发挥作用，以上面代码为例，`/a/b/`，`/a/b/c/`，`/a/b/c/d/` 下的页面都可以被注册的 Service Worker 控制。但是 `/a/`、`/e/f/` 目录下面的页面是不受注册的 Service Worker 的控制的（当然浏览器也会抛出错误告知开发者）。也就是说，在最大作用域的基础上才能通过 scope 配置在注册 Service Worker 的时候指定自定义的作用域。

**Service Worker 作用域污染**

通过对 Service Woker 作用域的了解会发现一个问题：**会不会存在多个 Service Worker 控制一个页面的情况呢？** 接下来再新建 serviceWorkerScopeDemo1 项目来了解注册多个 Service Worker 的情况下会有些什么神奇的情况发生。项目目录如下所示：

```
.
└── serviceWorkerScopeDemo1
    ├── a/
    │   ├── a-sw.js
    │   └── index.html
    ├── b/
    │   └── index.html
    └── root-sw.js
```

如果 `/a/index.html` 页面是如下方式注册 Service Worker：

```
<!DOCTYPE html>
  <head>
    <title>Service Worker Scope DEMO1 PageA</title>
  </head>
  <body>
    <script>
      if ('serviceWorker' in navigator) {
        navigator.serviceWorker.register('./a-sw.js')
      }
    </script>
  </body>
</html>
```

而 `/b/index.html` 页面是如下方式注册 Service Worker：

```
<!DOCTYPE html>
  <head>
    <title>Service Worker Scope DEMO1 PageB</title>
  </head>
  <body>
    <script>
      if ('serviceWorker' in navigator) {
        navigator.serviceWorker.register('../root-sw.js')
      }
    </script>
  </body>
</html>
```

`http://127.0.0.1:8000/a/index.html` 页面（称为 A 页面）在 `/a/` 作用域下注册了一个 Service Worker，而 `http://127.0.0.1:8000/b/index.html` 页面（称为 B 页面）在 `/` 作用域下注册了一个 Service Worker，这种情况下 B 页面的 Service Worker 就可以控制 A 页面，因为 B 页面的作用域是包含 A 页面的最大作用域的，这个时候这种情况就称之为**作用域污染**，这时候就会出现如下图所示的情况，A 页面被两个 Service Worker 所控制。

![1571909261308](C:\Users\zhengyi.fu\AppData\Roaming\Typora\typora-user-images\1571909261308.png)

在开发环境开发者在 Chrome 浏览器还可以通过 Devtools 进行手动 “unregister” 来清除掉污染的 Service Worker，但是如果在线上环境被安装了 Service Worker 之后这就是个持久的过程。除非用户手动清除存储的缓存（这个也是不可能的），否则就会出现 Service Worker 交叉控制页面的问题。

当然，线上出现作用域污染的情况也是有办法解决的，比较合理的一种做法是在 A 页面新上线的 `/a/index.html` 版本中注册 Service Worker 之前借助 `navigator.serviceWorker.getRegistrations()` 方法将污染的 Service Worker 先注销掉，然后在注册自己的所在作用域的 Service Worker。具体做法还是看下示例，将 serviceWorkerScopeDemo1 项目的 `/a/index.html` 文件修改后代码如下所示：

```
    <script>
      if ('serviceWorker' in navigator) {
        navigator.serviceWorker.getRegistrations()
          .then(regs => {
            for (let reg of regs) {
              // 注销掉不是当前作用域的所有的 Service Worker
              if (reg.scope !== 'https://127.0.0.1:8000/a/') {
                reg.unregister()
              }
            }
            // 注销掉污染 Service Worker 之后再重新注册自己作用域的 Service Worker
            navigator.serviceWorker.register('./a-sw.js')
          })
      }
    </script>
```

通过这样的方式，运行 serviceWorkerDemo 项目会发现，A 页面只会有一个被自己注册的 Service Worker 生效，在复杂的项目架构中，Service Worker 的作用域污染问题会经常发生，在设计 Service Worker 注册逻辑的时候，尤其是大型的 Web App 项目的时候需要考虑到这点。

**Service Worker 注册设计**

由于 Service Worker 注册会有意想不到的作用域污染问题，而 Web App 项目又有多种形式存在，有 SPA（单页面应用），MPA（多页面应用）等架构方式

***SPA注册Service Worker***

SPA 在工程架构上只有一个 `index.html` 的入口，站点的内容都是异步请求数据之后在前端渲染的，应用中的页面切换都是在前端路由控制的。

通常会将这个 `index.html` 部署到 `https://somehost`，SPA 的 Service Worker 只需要在 `index.html` 中注册一次。所以一般会将 `sw.js` 直接放在站点的根目录保证可访问，也就是说 Service Worker 的作用域通常就是 `/`，这样 Service Worker 能够控制 `index.html`，从而控制整个 SPA 的缓存。

SPA 每次路由的切换都是前端渲染的，这个过程本质上还是在 `index.html` 上的前端交互。通常 Service Worker 会预先缓存 SPA 中的 AppShell 所需的静态资源以及 `index.html`。当然有一种情况比较特殊，当用户从 `https://somehost/a` 页面切换到 `https://somehost/b` 页面的时候，这时候刷新页面首先渲染的还是 `index.html`，在执行 SPA 的路由逻辑之后，通过 SPA 前端路由的处理，继续在前端渲染相应的路由对应的渲染逻辑，这部分的逻辑都是在已经缓存的 JavaScript 中完成了。

***MPA 注册 Service Worker***

MPA 这种架构的模式在现如今的大型 Web App 非常常见，这种 Web App 相比较于 SPA 能够承受更重的业务体量，并且利于大型 Web App 的后期维护和扩展。MPA 可以理解为是有多个 HTML 文件对应着多个不同的服务端路由，也就是说 `https://somehost/a` 映射到 `a.html`，`https://somehost/b` 映射到 `b.html`。

那么 MPA 架构下怎么去注册 Service Worker 呢？是不同的页面注册不同的 Service Worker，还是所有的页面都注册同一个 Service Worker？结论是：需要根据实际情况来定。

***MPA 注册单个 Service Worker***

在每个页面之间的业务相似度较高，或者每个页面之间的公共静态资源或异步请求较多，这种 MPA 是非常适合在所有的页面只注册一个 Service Worker。

例如 `https://somehost/a` 和 `htps://somehost/b` 之间的公共内容较多，则通常情况下在 `/` 作用域下注册一个 Service Worker。这样这个 Service Worker 能够控制 `https://somehost` 域下的所有页面。

MPA 维护单个 Service Worker 有如下特点：

- 可以统一管理整个站点的缓存。
- 不会造成页面之间的作用域污染。
- 后期维护成本相对较低。

**MPA 注册多个 Service Worker**

MPA 注册多个 Service Worker 适用于主站非常庞大的 Web App，并且是以 path 分隔的形式铺展垂类子站的大型 Web App，这种情况下就不适合只在 `/` 作用域下只注册一个 Service Worker 了。

例如：`https://somehost/a` 和 `https://somehost/b` 几乎是两个站点，其中公共使用的静态资源或异步请求非常少，则比较适合每个子站注册维护自己的 Service Worker，`https://somehost/a` 注册 Servcie Worker 的作用域为 `/a/`，最好是存在 `/a/sw.js` 对应的 Service Worker 文件 URL 可访问，尽量不要使用某一个公用的 `/sw.js` 并使用 scope 参数来自定义作用域，这样会增加后期的维护成本以及增加出现 bug 的风险。

子站在实现上还要考虑一点是，防止其他页面的 Service Worker 对自身页面造成污染，需要在注册子站 Service Worker 之前将不是子站 path 作用域的 Service Worker 先注销掉。

注册多个 Service Worker 有如下特点：

- 需要严格要求每个子站管理好自己的 `sw.js` 及作用域。
- 防止对其他子站的 Service Worker 造成影响。
- 相比较整个站点只注册一个 Service Worker，这种维护多个 Service Worker 的方式更加灵活。
- 随着子站的增多，风险相对会更加大，也更加难以维护。

**Service Worker 更新**

当在页面中通过 `sw.js` 注册了一个 Service Worker 之后，如果 `sw.js` 内容发生了变更，Service Worker 该如何更新呢？

拿 SPA 为例，作为 AppShell 的载体 `index.html` 是会被缓存起来的，AppShell 的静态资源也都会被缓存起来的，由于 Service Worker 的注册入口必须是在主线程完成，所以 Service Worker 的注册必然是需要在 `index.html` 的 `<script></script>` 标签或者被缓存住的 JavaScript 文件中来实现的。

如果 Web App 功能发生了升级更新，我们预期的结果是当用户刷新页面的时候希望浏览器立即更新当前页面的缓存，并且立即加载最新的内容和资源，呈现最新的效果给用户看到。可是用户在刷新页面的时候看到的还是之前缓存的老的内容，这时候该如何处理呢？

通常在每次进行 Web App 升级的时候，都必须伴随着 Service Worker 文件 `sw.js` 的升级，当浏览器检测到 `sw.js` 的升级之后，就会重新触发注册、安装、激活、控制页面的流程，并在这个过程中就会更新当前 Web App 的离线缓存为最新的上线内容。

在执行 `navigator.serviceWorker.register()` 方法注册 Service Worker 的时候，浏览器通过自身 diff 算法能够检测 `sw.js` 的更新包含两种方式：

- Service Worker 文件 URL 的更新
- Service Worker 文件内容的更新

在实际项目中，在 Web App 新上线的时候，通常是在注册 Service Worker 的时候，通过修改 Service Worker 文件的 URL 来进行 Service Worker 的更新，一般采用以下代码所示的方式处理：

```
if ('serviceWorker' in navigator) {
  navigator.serviceWorker.register('./sw.js?v=20190401235959')
}
```

每次 Web App 上线构建的时候，维护一个最新的唯一构建版本号，将构建版本号写入 Service Worker 文件 URL 的版本号参数中，这样的话，就能够保证每次 Web App 有最新上线功能的时候，都能够有最新的 Service Worker 文件 diff 让浏览器能够检测到。当然，除了改变 Service Worker 文件 URL，还可以改变 Service Worker 文件的内容，如下代码所示：

```
// sw.js
self.version = '20190401235959'

//注意： 在 sw.js 中，self 为 Service Worker 线程的全局命名空间，类似于主线程的 window，在 sw.js //中是访问不到 window 命名空间的。
```

在 Web App 每次上线新的功能，项目进行构建的时候，可以将最新的唯一构建版本号写在 `sw.js` 文件内，这样也能保证每次 Web App 都能够有最新的 Service Worker 文件 diff 被浏览器检测到。

**Service Worker 容错**

由于 Service Worker 一旦上线就会永久生效，如果发现线上 Service Worker 有 bug 该怎么办呢？有一种亡羊补牢的方法是重新上一次线，注销掉有 bug 的 Service Worker，假如现在有一个现存的项目 serviceWorkerUnregisterDemo，项目目录如下：

```
.
└── serviceWorkerUnregisterDemo/
    ├── index.html
    └── sw.js
```

如果需要紧急下线该项目的 Service Worker，则 `index.html` 代码如下所示：

```
<!DOCTYPE html>
  <head>
    <title>Service Worker Unregister Demo</title>
  </head>
  <body>
    <script>
      if ('serviceWorker' in navigator) {
        navigator.serviceWorker.getRegistrations()
          .then(regs => {
            for (let reg of regs) {
              // 注销掉所有的 Service Worker
              reg.unregister()
            }
          })
      }
    </script>
  </body>
</html>
```

这种方法是在发现 Service Worker 出现问题之后，必须重新上线 Web App 来解决问题，这样的成本比较高。一般大型 Web App 上线的过程也非常复杂，上线周期长，所以这种止损效果较差，不是很可取。还有一种方法可以避免重新上线 Web App，只需要在 Service Worker 注册的时候通过一个 “**开关请求**” 做一个容错降级的处理，这个开关请求需要满足几个条件：

- 能够快速上线，和 Web App 的上线解耦
- 不能被缓存（无论是 HTTP 缓存还是 Service Worker 缓存）

在实际项目中，通常开关请求会维护成一个 JavaScript 文件（当然也可以是任何一种请求类型，只不过 JavaScript 文件通常比较好维护，而且无需考虑请求跨域的问题），放在某一个可以快速上线的静态资源服务器。那么现在可以修改 serviceWorkerUnregisterDemo 项目的 `index.html` 代码来看看具体如何解决问题的，代码如下面所示：

```
<!DOCTYPE html>
  <head>
    <title>Service Worker Unregister Demo</title>
  </head>
  <body>
    <script>
      if ('serviceWorker' in navigator) {
        // 正常进行注册 Service Worker
        navigator.serviceWorker.register('./sw.js?v=20190401235959')
        let script = document.createElement('script')
        // 假设这个 JS 中存在 Service Worker 开关全局变量
        script.src = 'https://some-static-cdn-host/sw-on-off.js'
        script.async = true
        script.onload = () => {
          // Service Worker 开关全局变量的名称
          if (window.SW_TURN_OFF) {
            navigator.serviceWorker.getRegistrations()
              .then(regs => {
                for (let reg of regs) {
                  // 注销掉所有的 Service Worker
                  reg.unregister()
                }
              })
          }
        }
        document.body.appendChild(script)
      }
    </script>
  </body>
</html>
```

假如在 `https://some-static-cdn-host/sw-on-off.js` 静态资源服务器维护了一个开关 JavaScript 文件，那这个文件正常情况下的代码内容如下所示：

```
/**
 * @file https://some-static-cdn-host/sw-on-off.js
 */

// 当 Web App 线上出现紧急问题的时候将值设为 true 并上线
window.SW_TURN_OFF = false
```

#### Service Worker 工作原理

下面讲一讲Service Worker是如何进行离线缓存控制的，其实Service Worker的工作原理主要体现在它的生命周期上，一个 Service Worker 从被注册开始，就会经历自身的一些生命周期的节点，而在这些节点都可以去做一些特定的事情，比如一些复杂的计算、缓存的写入、缓存的读取等操作。通过这些生命周期节点的联合调度，Service Worker 才能完成复杂的资源离线缓存的工作。只有了解了 Service Worker 的生命周期，才能通过设计相关逻辑，并开发 Service Worker 文件 `sw.js` ，让 Service Worker 去完成 PWA 离线缓存策略。

**生命周期**

了解下什么是 Service Worker 的生命周期，每个 Service Worker 都有一个独立于 Web 页面的生命周期，其示意图如下图所示。

![Service Worker 生命周期](https://lavas-project.github.io/pwa-book/chapter04/img/service_worker_lifecycle.png)

1. 在主线程成功注册 Service Worker 之后，开始下载并解析执行 Service Worker 文件，执行过程中开始安装 Service Worker，在此过程中会触发 worker 线程的 install 事件。
2. 如果 install 事件回调成功执行（在 install 回调中通常会做一些缓存读写的工作，可能会存在失败的情况），则开始激活 Service Worker，在此过程中会触发 worker 线程的 activate 事件，如果 install 事件回调执行失败，则生命周期进入 Error 终结状态，终止生命周期。
3. 完成激活之后，Service Worker 就能够控制作用域下的页面的资源请求，可以监听 fetch 事件。
4. 如果在激活后 Service Worker 被 unregister 或者有新的 Service Worker 版本更新，则当前 Service Worker 生命周期完结，进入 Terminated 终结状态。

Service Worker 生命周期是一个比较复杂的知识点，其中有较多的细节需要深入理解，为了更清楚的进行介绍，接下来新建一个项目 serviceWorkerLifecycleDemo，项目目录结构如下：

```
.
└── serviceWorkerLifecycleDemo/
    ├── imgs/
    │   └── dog.jpg
    ├── index.html
    └── sw.js
```

首先，需要有一个 Service Worker 的注册入口，所以 `index.html` 的代码内容如下所示：

```
<!DOCTYPE html>
  <head>
    <title>Service Worker Lifecycle Demo</title>
  </head>
  <body>
    <img src="./imgs/dog.jpg" alt="demo image" />
    <script>
      if ('serviceWorker' in navigator) {
        // 由于 127.0.0.1:8000 是所有测试 Demo 的 host
        // 为了防止作用域污染，将安装前注销所有已生效的 Service Worker
        navigator.serviceWorker.getRegistrations()
          .then(regs => {
            for (let reg of regs) {
              reg.unregister()
            }
            navigator.serviceWorker.register('./sw.js')
          })
      }
    </script>
  </body>
</html>
```

这次在 serviceWorkerLifecycleDemo 项目的 HTML 文件中加入一个 `<img>` 标签来加载一张图片，主要是用来理解 Service Worker 如何在生命周期中进行离线与缓存处理的。

虽然空的 Service Worker 文件也是可以通过注册来新开一个 Service Worker 线程，但是通常 Service Worker 文件中需要编写一些 JavaScript 代码逻辑来完成 Web App 的离线与缓存的策略设计。接下来我们会一步步的详细讲解这些代码该如何编写，首先先给 `sw.js` 写入以下代码，用来理解 Service Worker 的生命周期：

```
// sw.js
console.log('service worker 注册成功')

self.addEventListener('install', () => {
  // 安装回调的逻辑处理
  console.log('service worker 安装成功')
})

self.addEventListener('activate', () => {
  // 激活回调的逻辑处理
  console.log('service worker 激活成功')
})

self.addEventListener('fetch', event => {
  console.log('service worker 抓取请求成功: ' + event.request.url)
})
```

这段代码一开始是直接通过 `console.log()` 打印输出一段内容，然后绑定了三个事件，分别是 `install`、`activate`、`fetch` 事件，用来响应 Service Worker 生命周期的事件触发。

接下来用 Chrome 浏览器来测试一下 serviceWorkerLifecycleDemo 这个例子，为了更好的理解测试结果，在打开测试页面 `http://127.0.0.1:8000` 之前需要将所有的浏览器标签关闭（后面会详细解释为什么需要如此操作）。不出意外的话，**第一次**访问 `http://127.0.0.1:8000` 页面的时候 Chrome Devtools Console 控制台的打印结果如下：

```
service worker 注册成功
service worker 安装成功
service worker 激活成功
```

当我们**第二次**刷新页面的时候，这时候控制台的打印结果如下：

```
service worker 抓取请求成功：http://127.0.0.1:8000/imgs/dog.jpg
```

从这个执行结果来看，初步能够说明以下几点：

- Service Worker 文件只在首次注册的时候执行了一次。
- 安装、激活流程也只是在首次执行 Service Worker 文件的时候进行了一次。
- 首次注册成功的 Service Worker 没能拦截当前页面的请求。
- 非首次注册的 Service Worker 可以控制当前的页面并能拦截请求。

Service Worker 在内部都有一系列的工作流程，这些工作流程决定了开发者可以在 Service Worker 文件中如何进行开发。下图展示的是 Service Worker 工作流程图。

![Service Worker 工作流程图](https://lavas-project.github.io/pwa-book/chapter04/img/service_worker_process.png)

实际上 Service Worker 首次注册或者有新版本触发更新的时候，才会重新创建一个 worker 工作线程并解析执行 Service Worker 文件，在这之后并进入 Service Worker 的安装和激活生命周期。

而在首次注册、安装、激活之后，Service Worker 已经拿到了当前页面的控制权了，但为什么首次刷新却没有拦截到网络请求呢？主要是因为在 Service Worker 的注册是一个异步的过程，在激活完成后当前页面的请求都已经发送完成，因为时机太晚，此时是拦截不到任何请求的，只能等待下次访问再进行。

而第二次刷新页面，由于当前站点的 Service Worker 是处于激活状态，所以不会再次新建 worker 工作线程并执行 Service Worker。也就是说激活状态的 Service Worker 在一个站点只会存在一个 worker 工作线程，除非 Service Worker 文件发生了变化（手动 unregister Service Worker 也会注销掉 worker 工作线程），触发了浏览器更新，才会重新开启生命周期。而由于 Service Worker 工作线程的离线特性，只要处于激活状态，在后续的任何访问中，都会通过 fetch 事件监听器拦截当前页面的网络请求，并执行 `fetch` 事件回调。

**waitUntil 机制**

如果 Service Worker 安装失败会导致 Service Worker 生命周期终止。由于 Service Worker install 回调是在用户首次访问注册的时候才会触发，所以在项目设计的时候，会将 Web App 一些只有上线才会改变的静态资源会在 install 阶段进行缓存，让用户更快的体验到缓存加速的好处。如果缓存成功了才算是 Service Worker 安装完成，如果这些静态资源缓存失败了，那 Service Worker 安装就会失败，生命周期终止。

什么情况下才算是 Service Worker 安装失败呢？如果在 Service Worker 文件中的 install 回调中写一段错误逻辑会不会导致安装失败呢？接下来修改一下 serviceWorkerLifecycleDemo 的 `sw.js`，代码如下：

```
// sw.js
console.log('service worker 注册成功')

self.addEventListener('install', () => {
  // 一段一定会报错的代码
  console.log(a.undefined)
  console.log('service worker 安装成功')
})

self.addEventListener('activate', () => {
  // 激活回调的逻辑处理
  console.log('service worker 激活成功')
})

self.addEventListener('fetch', event => {
  console.log('service worker 抓取请求成功: ' + event.request.url)
})
```

在 install 事件回调中，插入了一段一定会报错的代码，看看是不是会导致 Service Worker 的安装失败呢？

示例运行结果如下图所示：

![Service Worker install 回调中报错情况](https://lavas-project.github.io/pwa-book/chapter04/img/service_worker_error_in_install.png)

从运行结果看，当 install 回调中的逻辑报错了，并不会影响 Service Worker 的生命周期继续向后推进，因为运行结果还是有 `激活成功`，甚至第二次刷新发现还能正常拦截请求。

所以说并不是 intall 回调中出错了就会导致生命周期中断。由于 Service Worker 生命周期异步触发的特性，并不是像同步执行模式，如果报错就会中断执行。Service Worker 事件回调的参数是一个 ExtendableEvent 对象，在 Service Worker 中需要使用 `ExtendableEvent.waitUntil()` 方法来保证生命周期的执行顺序。该方法接收一个 Promise 参数，开发者通常会将安装的回调执行逻辑（如缓存的写入）封装在一个 Promise 里，如果操作报错应该通过 Promise 来 reject 错误，这样 Service Worker 就知道了安装失败，然后 Service Worker 就能中断生命周期。接下来修改 `sw.js` 代码如下所示：

```javascript
// sw.js
console.log('service worker 注册成功')

self.addEventListener('install', event => {
  // 引入 event.waitUntil 方法
  event.waitUntil(new Promise((resolve, reject) => {
    // 模拟 promise 返回错误结果的情况
    reject('安装出错')
    // resolve('安装成功')
  }))
})

self.addEventListener('activate', () => {
  // 激活回调的逻辑处理
  console.log('service worker 激活成功')
})

self.addEventListener('fetch', event => {
  console.log('service worker 抓取请求成功: ' + event.request.url)
})
```

这时候运行刷新页面的时候发现 Service Worker 的生命周期中断，而且没有执行 activate 事件回调。当将 `reject('安装失败')` 改成 `resolve('安装成功')` 的时候，会发现 Service Worker 能够顺利激活。事实上，`ExtendableEvent.waitUntil()` 方法扩展了事件的生命周期。在服务工作线程中，延长事件的寿命能够阻止浏览器在事件中的异步操作完成之前终止 worker 工作线程。

在 install 事件回调被调用时，它把即将被激活的 worker 线程状态延迟为 installing 状态，直到传递的 Promise 被成功地 resolve。这主要用于确保：Service Worker 工作线程在所有依赖的核心 cache 被缓存之前都不会被安装。

不只是 install 事件回调可以调用这个方法，如果在 activate 事件回调被调用时，它把即将被激活的 worker 线程状态延迟为 activating 状态，直到传递的 Promise 被成功地 resolve。这主要用于确保：任何功能事件不会被分派到 ServiceWorkerGlobalScope 对象，直到它升级数据库模式并删除过期的缓存条目。

当 `ExtendableEvent.waitUntil()` 运行时，如果 Promise 是 resolved，任何事情都不会发生；如果 Promise 是 rejected，installing 或者 activating 的状态会被设置为 redundant。

**终端**

在运行 serviceWorkerLifecycleDemo 示例的时候，提到了需要关闭所有浏览器标签再打开测试页面，其中主要的原因是涉及到 Service Worker 的终端（clients）的概念。

![Service Worker 终端](https://lavas-project.github.io/pwa-book/chapter04/img/service_worker_clients.png)

在手机端或者 PC 端浏览器，每新打开一个已经激活了 Service Worker 的页面，那 Service Worker 所控制的终端就新增一个，每关闭一个包含已经激活了 Service Worker 页面的时候（不包含手机端浏览器进入后台运行的情况），则 Service Worker 所控制的终端就减少一个，如上图打开了三个浏览器标签，则当前 Service Worker 控制了三个终端，通过 Chrome 浏览器 Devtools 的 `Applications -> ServiceWorker` 标签可以查看如下图所示 Service Worker 控制的三个终端。

