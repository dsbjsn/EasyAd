## EasyAd
### 支持的平台及广告类型
| 平台\广告类型|开屏|激励|全屏|原生|横幅|插屏|Draw|
|:------------|--:|--:|--:|--:|--:|--:|--:|
| CSJ         |yes|yes|yes|yes|yes|yes|yes|
| GroMore     |yes|yes|no |yes|yes|no |no |
| YLH         |yes|yes|yes|yes|yes|yes|no |
| KS          |yes|yes|yes|yes|yes|no |yes|
| Mintegral   |yes|yes|yes|no |yes|no |no |
| Oneway      |no |yes|yes|no |no |no |no |
| Sigmob      |yes|yes|yes|no |no |no |no |
| YKY         |yes|yes|no |yes|no |no |no |
| YLB         |no |yes|no |no |no |no |no |

### AdConfig(广告模块信息初始化类)
AdConfig.Builder  
.with(AppCompatActivity)  设置activity --- 必须  
.setAppInfo(String,String) 设置应用id/key（上报广告事件时需要）--- 非必须 --- 默认为空字符串  
.setUserInfo(Token,String) 设置用户Token/id（上报广告事件时需要）--- 非必须 --- 默认为空字符串  
.setRootPath(String) 后台域名（请求广告信息和上报广告事件需要）--- 必须  
.setAdInfoPath(String,String) 设置广告文件服务器获取路径/本地获取路径(assest下json格式)  --- 必须  
.isRewardNeedVerify(Boolean)  激励视频是否需要后台验证 --- 非必须 --- 默认false  
.addCallBack(ResultCallBack) 初始化监听器 --- 非必须  
.isTest(Boolean) 是否是调试模式 --- 非必须  
.init() 开始初始化 --- 必须 --- 最后调用  

### AdManager(广告管理类)
setAdInfo(AdInfoEntity pAdInfoEntity) 设置广告信息实体对象  
loadLocalAdInfo() 加载本地广告信息  
prepareLoadAds() 开始预加载广告  
showSplash(AdListener pAdListener, FrameLayout pSplashFl) 显示开屏广告  
showRewardVideoAd(Activity pActivity, RewardAdListener pRewardAdListener) 播放激励视频    
showBannerAd(Activity pActivity, FrameLayout pBannerRootFl) 显示banner广告  
showNativeAd(Activity pActivity, FrameLayout pNativeRootFl) 显示原生广告  
showFullAd(Activity pActivity, FullAdListener pFullAdListener) 显示全屏广告  
showInteractionAd(Activity pActivity) 显示插屏广告  

### AdPlatformHelper(初始化各个广告平台)

### 网络请求接口  
getAdJson(String path) 获取服务器广告配置文件，path:广告配置文件路径  
sendADEvent(AdInfoEntity.AdBean pAdBean, AdAction pAdAction) 上报广告事件  
getRewardAdIsValid(AdInfoEntity.AdBean pAdBean, ResultCallBack pResultCallBack) 模拟广告回调

### 广告配置json示例
```
{
  "name": "Demo",
  "maxGDTError": 18,
  "ylbMaxNum": 999,
  "maxThreadNum": 3,
  "concurrentLoadNum": 2,
  "platformData": [
    {
      "platform": "csj",
      "app_id": "******",
      "is_open": true
    },
    {
      "platform": "sigmob",
      "app_id": ""******",
      "app_key": ""**********",
      "is_open": true
    },
  ],
  "rewardList": [
    {
      "type": "reward",
      "adId": "******",
      "price": 10,
      "platform": "csj"
    },
  ],
   "bannerList": [],
   "splashList": [],
   "nativeList": [],
   "fullList": [],
   "interactionList": []
}
```
