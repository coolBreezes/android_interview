# WebView

## 1、WebView的一些坑

1. android 16前 安全漏洞 利用java的反射机制，调用WebView.addJavascriptInterface
2. webView的销毁（内存泄漏） 先remove掉容器中的webView，然后再调用webView.removeAllViews 和destroy方法
3. jsbridge  native调用web端方法
4. webViewClient.onPageFinished -&gt; WebChromeClient.onProgressChanged
5. 后台耗电
6. webView硬件加速导致页面渲染问题（白块）

### 1.1内存泄漏解决思路

1. 独立进程
2. 动态添加webView，对传入的webView使用的Context使用弱引用 add  remove

