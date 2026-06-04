ColoxAdminMobile v1.0.5 修改说明

本版重点修复：手机端刷新用户显示 Failed to fetch 的问题。

修改内容：
1. MainActivity.java 增加完整 AndroidBridge.postJson 异步原生 POST 请求。
2. 保留 AndroidBridge.postJsonSync 作为备用通道。
3. index.html 的接口请求优先走 Android 原生 POST，不再优先走浏览器 fetch。
4. 如果在电脑浏览器中预览，会提示“浏览器预览无法连接云端”，避免误判为配置错误。
5. “我的”页面增加“请求通道”显示：
   - Android 原生 POST：代表正在 APK/WebView 环境中运行。
   - 浏览器 fetch 预览：代表不是 APK 原生环境，可能受 CORS 限制。

测试建议：
1. 用 Android Studio 打开项目并安装到手机/模拟器。
2. 进入“我的”页面，确认请求通道显示为“Android 原生 POST”。
3. 确认项目配置中的 Base URL、users_path、action_path、Admin Token 和桌面端一致。
4. 点击“刷新用户数据”。

注意：
如果你直接在电脑 Chrome 浏览器里打开 index.html，仍可能因为 CORS 无法读取云端，这是正常现象；请以 APK 运行结果为准。
