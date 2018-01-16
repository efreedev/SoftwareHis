**Pale Moon** 中文名"苍月浏览器",是一个强调定制性的开源网络浏览器。其座右铭是"Your browser, Your way"(你的浏览器，你的方式)。官方提供 Windows 和 Linux 版，还有非官方的 macOS 版，以及其它平台的贡献者版本。主要开发者是荷兰人 **M.C. Straver**。
## 简介
**苍月** 是一个 Firefox 的分支，并和 Firefox 具有实质性的分歧，尤其是在对附加组件和用户界面上。**苍月** 在 2009 年发布了首个官方版，是使用调整的编译器设置重新构建的 Fx 3.5.2版。随着项目的发展，最终在 v24 时成为 Firefox 24 ESR 的一个真实的分支版。从 v25 开始，**苍月**使用了完全独立的版本方案。

## 简史
在 2016.11 发布了 Pale Moon 27.0，是对 Firefox 38 ESR 的核心浏览器代码的一次主要的重新建基(rebase)，加入了 HTTP/2, DirectX 11, MSE/DASH 和 JavaScript ES6 功能。而附加组件的支持则除了 Jetpack 兼容性的稍微减弱外，几乎完全没有变化。
Pale Moon 保留了 Firefox 4 到 28 的用户界面，并继续支持 XUL 和 XPCOM 附加组件，同时使用较新的 Firefox 源代码来更新浏览器的其它组件。

## 未来计划
在 2017 年，作者开始了一个 Unified XUL Platform (UXP 统一 XUL 平台)项目。**UXP** 是一个比 Pale Moon 27 更新的 Mozilla 代码库分支，预备作为用于数个基于 XUL 的应用程序的一个平台，包括未来的 Pale Moon 版本。为了演示和改进 UXP，作者使用它创建了一个新的浏览器 Basilisk，在 2017.11 发布了第一个版本。

## 更新日志

###27.7.0 (2018-01-15)
这是一个稳定性和错误修复的发行版，还添加了一些新功能来进一步改进网络兼容性。

**变化/修复**:

	* 重新整理对首选项的访问(在 Linux 上移到了“工具”菜单，而 Windows 上从"Options"(选项)改名为"Preferences"(首选项))。
	* 重命名"Restart with add-ons disabled"(重启为禁用附加组件)为"Restart in Safe Mode"(以安全模式重启)以更好的反映其作用。
	* 解决了默写不正确编码的 PNG 文件在我们的 libpng 更新后不解码的问题。
	* 修复了在 Mac 构建版上的不能正确部署应用程序菜单的问题。
	* 新增了 "My home page"(我的主页)作为新建标签页的选项。
	* 新增了一个选项来禁用第 4 和 5 个鼠标键(Windows)。
	(相应使用 `mouse.button4.enabled` 和 `mouse.button5.enabled`)
	* 改进了非默认配置档的重置。
	* 修复了如果浮动则拥有不正确的高度的细节/摘要，打散布局的问题。
	* 对细节/摘要标记做了一些更进一步的改进，使它们符合当前规范并修复了某些额外的问题。
	* 实现了对按钮中的 flex/columnset 内容的支持，使得其行为符合其它浏览器。
	(这个应该修复了使用 Twitch 的新网络界面的布局问题)
	* 修复了 CSS 克隆操作会绘制一个崩溃的问题。
	* 更改了小数边框宽度的取整方式，以提供更自然的行为。
	* 修复了数值输入可能不正确的标记为只读的问题。
	* 添加了用于在 Windows 启动面板中磁贴显示的 assets()。
	* 通过添加一个用于服务器使用一次性的 pref 迁移来完成 sync infra swapover(同步下互换)。
	* 改进了 WebAudio API: 从 AudioNode.connect() 返回连接的音频节点。
	* 在媒体元素中添加了对一个默认回放开始位置的支持。
	* 修复了在 cubeb-alsa 代码中的 assert(断言) (Linux)。
	* 添加了对媒体的 cue-change 事件(如 subtitles)的支持。
	* 更新 SQLite 为 3.21.0。
	* 修复了当尝试使用嵌入的平台时的崩溃。
	* 修复了在垂直文本页面上的 devtools (gcli) 截屏。
	* 修复了 devtools 复制为 cURL 用于 POST 请求。
	* 改进了 HTML 编辑器组件(几个错误修复)。
	* 添加了对 ES7 的求幂 `a ** b` 操作符的支持。
	* 修复了 arrow 函数不正确的创建一个 'arguments' 绑定的问题。
	* 添加了 Javascript 的 ES6 "unscopables"。

**安全/隐私修复**:

	* 禁止了按默认对登录详细信息的自动填写，以防止凭证被滥用(例如用于跟踪)或窃取的潜在风险。
	* 新增了一个首选项(在【安全】分类中)以方便启用或禁用登录数据的自动填写。
	* 移除了当在一个新的私密窗口中打开一个链接时引用页的发送。
	* 新增了一个选项来禁用页面可见性 Web API (dom.visibilityAPI.enabled)，让用户可以防止页面知道它们是否向用户活动显示。
	* 移除了用于 Cookies 的 "ask every time"(每次询问)策略。为了精细的控制，请使用某些优秀的可用于管理在基于每个站点或基于每个 URL 的基础上的 Cookies 使用的扩展。
	* 新增了对 X-Content-Type-Options 的支持: nosniff (用于脚本)。
	* 更改了性能计时器的分辨率到了一个级别，在这个级别中，任何未来的对硬件计时攻击的潜在滥用将变得不可实现。 *DiD*
*DiD* 中意味着修复是"Defense-in-Depth"(纵深防御)的:这是一个并非应用于 Pale Moon 中的(潜在的)活跃的可利用漏洞，而是用于防止相同的代码，例如在周边的代码发生变化而暴露问题时引发的或者新的攻击防线被发现时而出现的未来的漏洞。

### 27.6.2 (2017-11-28)

这是对浏览器的安全性和小错误修复更新。
这将很可能是 2017 年的最后一次更新，假期不远了。

**变化/修复**:

	* 实现了所谓的 "cookie-averse document objects" 的概念，这是一个屏蔽特定的网络内容设置 cookies 的安全性和保密性措施。这个减轻了有助于针对“隐藏的” Cookie 跟踪的 cookie 注入。
	* 减轻了通过使用带变音符号的无点 i 和无点 j 的 IDN 来进行某些域名欺骗。(CVE-2017-7832)
	Pale Moon 现在将会在实际的地址栏中显示这些类型的使用中文域名的欺骗域名。
	请注意，当使用 IDNs 时，标识面板在安全站点上将总是可以帮助你注意到潜在的欺骗，而不是依赖于 URL 本身的检测算法。通过这样，某些类似 CVE-2017-7833 的其它问题就已经被我们减轻了。
	* 修复了某些混合内容拦截的问题。(CVE-2017-7835)
	* 新增了对证书上的正确签名数据类型的额外检查。
	* 在导出书签到 HTML 中新增了缺少的净化处理。 (CVE-2017-7840)
	* 修复了几个崩溃和内存安全危害。
	* 修复了 Linux 加载风火轮图像以正确的编码，避免闪烁。
	* 移除了用于重启浏览器的快捷键组合，避免大家在使用某些键盘布局时按了组合键而误触浏览器重启的问题。

### 27.6.2 (2017-11-28)
这是对浏览器的一个安全性和小错误修复更新。
这个很可能是 2017 的最后一次更新，假期不远了。

**变化/修复**:

	* 实现了所谓的 "cookie-averse document objects" (反对 cookie 文档对象)的概念，它是一个拦截特定网络内容设置 Cookies 的安全和隐私措施。 这个减轻了 cookie 注入，这个可能有助于防止 "隐式" cookie 跟踪。
	* 使用带 dotless-i 和 dotless-j 来减轻某些通过 IDN 的域名欺骗。(CVE-2017-7832)
	* Pale Moon 现在将会在实际的地址栏中以 punycode(微代码)的形式显示这些类型的欺骗域名。
	* 请注意，身份面板将总是可以帮助你在安全站点上在使用 IDNs 时来通知潜在的欺骗，而不是依赖于在 URL 自身的检测算法。因此，某些如 CVE-2017-7833 的其它问题都已经被我们减轻了。
	* 修复了一个混合内容拦截的问题。 (CVE-2017-7835)
	* 添加了一个额外的检查用于证书上的正确签署数据类型。
	* 在导出书签到 HTML 中添加了缺失的净化。 (CVE-2017-7840)
	* 修复了各种崩溃和内存安全隐患。

### 27.6.1 (2017-11-15)
这是一个解决了某些有人报告的紧急问题的小错误修复。

**变化/修复**:

	* 修复了一个随新建窗口回归的问题(从命令行或文件关联打开两个窗口，在新窗口上的聚焦问题，未在新窗口中加载主页等)
	* 校准 XHR 和当前的规范以允许 withCredentials。
	* 修复了在处理程序中的一个输入元素聚焦问题。
	* 修复了所有填充的 HTTP/2 帧的处理以防止罕见的 HTTP/2 挂起。
	* 更新了花旗银行(CitiBank)的 override 来解决了他们的登录问题。
	* 更新了 Netflix override 为一个社区提供的版本，它似乎更好的满足了他们的任意限制。

### 27.6.0 (2017-11-07)
这是一个重要的开发更新。

**变化/修复**:

	* 减低了对 Direct2D 1.0 的支持以避免字体渲染问题。Windows 安装不能使用 Direct2D 1.1 现在将要回落到软件渲染。因此，如果你在 Windows Vista 或 Windows 7 上的话，从这个版本开始字体看起来有所不同。 在 Windows 7 上受这个影响的用户应该安装平台更新来重新启用 Direct2D。
	* 一个新 Brotli 解码器库，并按默认启用对 Brotli HTTP content-encoding (内容编码)的支持。
	* 添加了当用户尝试安装 WebExtensions 扩展时告知用户有关 WebExtensions 未被支持的通知(相对于 "extension is corrupt"(扩展是坏的))
	* 添加了几个 DOM childNode 方便函数。这个应该修复了某些 lazy-loading (延迟加载)框架。
	* (再次享受你的 LOLcats!)
	* 已更改自动更新到新的架构。
	* 在选项中添加了额外的代理设置，涵盖了通过 SOCKS v5 进行 DNS 查询以及使用已知的凭证自动化代理身份验证。
	* 添加了一个 UTF-8 的可选择备用字符编码并回退为 UTF-8 作为最后的尝试。 (Issue #1423)
	* 改进了 timing of canplay and canplaythrough firing to work around a potential race condition locking up queued video playback.
	* 改进了 upmixing of mono sound for multi-channel setups.
	* 修复了一个由 KISS-FFT 库导致 CPU 死锁线程的并行性问题 (Issue #1425)
	* 修复了下载面板中的"从历史记录中移除"功能。
	* 如果内容是空白文档的话则强制聚焦于新窗口中的地址栏。
	* 修复了地址栏中的滴管标记以允许建议使用点击关闭。
	* 进一步清理了状态了的代码。
	* 禁用了 window.showModalDialog; 它从 2 年前的规范中移除并带有潜在的滥用问题(模式对话框拦截用户界面)
	* 修复了图像解码器的调用来确保图像加载时间不会过早触发。
	* 更新 LibPNG 为 1.6.28，并启用了较快的 SSE2 解码。
	* 从上游更新了 WOFF2 代码。
	* 更新了 zlib 压缩库。
	* 对内部代码结构和规范的遵循做了一般性的改进。
	* 修复了一个特定命令行参数被使用的问题。
	* 更新了默认主题以改进工具栏和下载按钮的统一和对比。
	* 增加了通知弹出窗口的默认持续时间并使它们可配置。
	* 改善了音频可视化媒体的处理(不断进行中)。
	* 修复了 CSS 中的一个问题，其中就是即使有足够的视觉空间，元素有时仍重新流到下一行。
	* 使用最终的 ES6 规范来校准 for(let x=y;;) 循环的实现。
	* 修复了一个被打散的嵌套 contenteditable(内容可编辑)元素中的选择系统。
	* 修复了块链图形驱动程序的 Windows 10 检测。
	* 无需编辑器元素即可启用了在文档中的剪贴板数据的粘贴来改善了网络兼容性。
	* 修复了无需重启附加组件的卸载流程。
	* 修复了在控制台 API 中的未实现函数的处理。
	* 更新了 Facebook 用户代理已启用其它供应商受限的功能。
	* 更新了 SVG 伸缩缓存限制以便在一个较小的性能权衡中更好的缓解较大的 SVG 图像，解决了某些站点的设计问题。

**安全/隐私修复**:

	* 添加了一个选项来清除 Site Connectivity Data (站点连通性数据)(删除历史记录)。
	* 从 HSTS 预载列表中移除了过时的实体，并改进了其生成/处理。
	* 移除不想要的证书发行者组织到 common name fallback (如果发行人组织是空白的).
	* 添加了 ECDSA-SHA224, 256, 384 和 512 哈希过的证书签名的美化打印。
	* 拒绝了某些破坏的 Apple 字体的问题。

### 27.5.1 (2017-10-10)
这是对浏览器的一个安全和稳定性更新，并修复了某些用户已指出的某些问题。

**变化/修复**:

	* 更改了当没有重点色应用到白底黑字时的默认 Windows 10 样式。
	* 更改了当系统窗口框架被用于(启用了菜单栏)直接使用窗口管理器背景时在 Windows 10 上的主题样式化，以防止当发生更新窗口时出现的视觉卡顿。
	* 更新了 DropBox, YouTube 和 Yahoo 的 user agent overrides 以解决用户代理嗅探问题。
	* 修复了在媒体子系统中的一个崩溃。
	* 修复了在某些系统上视频回放的硬件加速被不正确的禁用的倒退问题。

**安全修复**:

	* 更新 hyphenation 库为最新的上游代码以修复一个安全问题。
	* 使用一个补丁更新 NSPR 为 4.16-RTM 以在 win64 上 un-bust building。
	* 更新 NSS 为 3.32.1-RTM.
	* 解决了更多的 Mac 字体问题 (CVE-2017-7825).
	* 修复了在 NPAPI 插件代码中的一个潜在的根危险。 DiD
	* 修复了在 JavaScript 数组中的一个潜在引用问题。 DiD

DiD 这意味着这个修复是 "Defense-in-Depth"(深度防御): 这是一个并非应用于 Pale Moon 中的(潜在的)活跃的可利用漏洞， 而是用于防止相同的代码在周边的代码发生变化而暴露问题从而导致未来的漏洞的修复。
### 27.5.0 (2017-09-26)
这是促进浏览器的常规开发的主要更新。

**变化/修复**:

	**用户界面**:
		* 添加了一个菜单选项用于重启浏览器。
		* 添加了 Windows 专用的 CSS 参数和查询，用于系统的重点色的使用。添加的是参数 -moz-win-accentcolor 和 -moz-win-accentcolortext 以及 media query -moz-win-accentcolor-applies 以了解 Windows 当前是否使用了一种重点色。
		* 更改了 Windows 的浏览器的 CSS 样式表以使用变量而不是硬编码的颜色，简化了它的样式并使其更灵活。进一步清理了 Windows 10 专用的浏览器样式。
		* 更改了 Windows 10 上的主题以使用新的重点色并改进操作系统的统一性。
		* 修复了在所有 Windows 操作系统上的 Windows 主题中的某些普通的不统一。
		* 更新了 Windows 饰件以便可以动态的选取 Windows 10 的重点色并让浏览器的感观能够相应的做出响应，即使是使用了基于桌面墙纸的自动化颜色比变化。
		* 移除了实验性质的 FF4 预发行的 status-in-addressbar (状态嵌入地址栏)功能，因为已经够拥挤的地址栏需要放松一下。这应该解决了某些用户已报告的扩展的 interop (互操作)问题，主题问题和域名加亮问题。
		* 清理了用于不再存在的插件更新工具的某些死亡代码。
		* 修复了在首选项中的一个文本方向问题。
		* 修复了在使用定制...后和禁用的上下文菜单相关的问题。
		* 重新整理并清除了状态首选项。
	**媒体**:
		* MSE 媒体更新(不断进行)。我们着眼于改善 MP4 的处理。
		* 改进了 MP3 metadata 解析(例如带嵌入专辑封面的不正确的时长)
		* 修复了 MP3 文件中的几个搜索问题
		* 修复了一些崩溃。
	* 修复了在关机时自动导出书签到 HTLM 的问题。
	* 修复了一个 re: 域名允许/拦截自安装的附加组件的回流问题。
	* 修复了在前端中的数个内部错误抛出。
	* 修复了开发工具中的数个小问题。
	* 添加了一个修复以防止主页在恢复会话时被加载(继而覆盖)。
	* 添加了一个选项来控制附加组件的拦截列表的行为(选项-> 安全性)
	* 添加了 DOM 函数 isSameNode().
	* 添加了 DOM onvisibilitychange 事件。
	* 添加了 document.scrollingelement (CSSOM)。
	* 添加了一个 Object.values 和 Object.entries 枚举函数的基本实现(ECMA2017 草本)。
	* 添加了 "Open in new private window" (在新的隐式窗口中打开)到书签、新闻供源和历史记录条目的菜单中。
	* 添加了 HTTP 请求方式 OPTIONS.
	* 添加了一个选项在遇到一个网络或安全错误时退出到一个无内容的页面。这个使用首选项 browser.escape_to_blank 控制 -- 当设为 true 时，"Get me out of here" (带我离开)按钮将加载一个空白页面而不是浏览器的主页。
	* 添加了试验性的 Brotli accept-encoding (代替 gzip/deflate 压缩的 http 数据传输)。现在按默认禁用，因为它会引起问题。
	* 改进了多个 CSS 选择器的处理。
	* 更改了会话存储来按默认记住用于 https 站点的表单数据。
	* 添加了(又一个)陷阱预防方式到 onbeforeunload 事件。
	* 修复了在选择“记住历史记录”时隐私首选项不正确的重置所有选项
	* 修复了在侧栏中不能取消选择加载书签。
	* 限制了在 HTTP 身份验证对话框中用户名和主机的显示为正常的长度，防止尺寸过大问题。
	* 修复了几个潜在的崩溃点。
	* 改进了 Windows dll 加载器模块的安全性。
	* 重新放置 "Open all in tabs"(在标签页中打开全部)的选项到实时书签(新闻供源)的文件夹上。
	* 使 URL 匹配在选择的文本中更自由，以便使得它更易于打开表示的地址。
	* 修复了一个其中的自动字体冲突修复并不总是有效的石墨字体渲染的问题。
	* 在 Linux 上现在对图像的颜色管理按默认是禁用的，因为许多发行版都没有带合理的默认 ICC 配置档的一个流线型设置，它使得在启用了颜色管理时图像看起来更差。
	* 加强了更新的安全性检查以防止已被通过 HTTPS 中间人攻击拦截/替换的更新 manifests 被接受。请注意 https 过滤式防毒软件可能会因此而干扰了未来的应用程序的更新。
	* 更新了 ANGLE 库以扩宽 WebGL 的支持并减少崩溃的潜在(由于垃圾被发送到视频驱动程序)。
	* 添加了用于 WebP 图像的内容嗅探(解决了 CloudFront 的不正确的 content-type 头信息)。
	* 修复了某些 H.264 媒体不能播放的问题 (SPS NAL)。
	* 改进了计时器效率(当不再需要高精度时切换回较低的精度，减少 CPU/电源消耗)。
	* 改进了在选择文本/链接上的上下文搜索。
	* 更新了使用 Alt 或 Shift 辅助键的地址栏处理，以便使用一个辅助键的 "switch to tab"(切换到标签页)可以打开已经打开的站点的多个副本。
	* 在 Linux 上添加了一个修复用于从 Enlightenment 启动浏览器。
	* 隐私修复: Pale Moon 现在将清除 QuotaManager 存储(asm.js 缓存/IndexedDB 数据)，作为清除离线网站数据的一部分。

### 27.4.2.1 (2017-08-28)
这仅仅是对便携版浏览器的超范围更新(Windows)。
这个修复了在备份及设置相关的便携 Shell 中的问题。

要更新，请遵循在 Pale Moon Portable 页上列出的建议更新过程。
### 27.4.2 (2017-08-22)
这是一个解决某些安全和稳定性问题的小更新。

**变化/修复**:

	* 修复了数个崩溃。
	* 启用了 opt-in(现在进入)调试功能以在所有的构建版中记录 SSL 密钥到一个文件。
	* 添加了对 TLS 1.3 握手导致浏览器挂起的一个修复。握手现在应该相当快并且不再会在错误的情况下拖延。

**安全修复**:

	* 更新 NSPR 为 4.15。
	* 更新 NSS 为 3.31.1。
	* 修复了一个在 URL 方案中使用过分长的用户名的 DoS 问题 (CVE-2017-7783)
	* 修复了一个问题，在其中(跨域) iframes 可能会打破范围 (CVE-2017-7787)
	* 修复了 WindowsDllDetourPatcher 中的一个问题(CVE-2017-7804)
	* 修复了一个在混合的 Jacobian-affine 坐标中的椭圆曲线加法的问题 (CVE-2017-7781)
	* 修复了一个在 nsImageLoadingContent 中的 UAF (CVE-2017-7784)
	* 修复了一个 WebSockets 中的 UAF  (CVE-2017-7800)
	* 修复了在 RelocateARIAOwnedIfNeeded 中的一个 heap-UAF (CVE-2017-7809) DiD (可访问性被禁用)

### 27.4.1 (2017-08-03)
这是一个解决了某些媒体和网络兼容性问题的小更新。

**变化/修复**:

	* 修复了一个媒体播放在使用 MSE 时将不能正确使用硬件加速的问题。
	这个可能导致高 CPU 占用以及在如 YouTube 上的高清视频的卡顿回放。
	* 修复了 ES6 迭代链以符合规范。
	* 修复了 ES6 矢量附加调用和某些相关的内存泄露。
	* 添加了一个解决方式来减少一个潜在少见的(计时关键)崩溃的可能性。

### 27.4.0 (2017-07-12)
这是一个清理掉大部分媒体流问题的主要更新，同时还添加了必需的增强，错误修复和安全修复到浏览器。

**变化/修复**:

	* 完全再加工的 Media Source Extensions(媒体源扩展)代码使得它符合规范，并按照 MSE 配合 MP4 的规范来进行异步。这应该修复了在 YouTube, Twitch, Vimeo 以及其它先前有某些问题的网站上的播放问题。非常感谢 Travis 为实现这个目标而做出的不懈努力!
	请注意 MSE+WebM (按默认禁用)还不是使用这个新代码的(计划下一发行版)，因此如果你不使用默认设置的话则仍要记住一套临时的东西:
		* 如果你先前已启用了 MSE+WebM，这个设置在你更新时就会被重置，已避免和更新的 MSE 代码冲突的设置。
		* 我们已经在选项中添加了一个额外的设置来禁用更新的 MSE 代码(异步使用)于你需要使用 WebM 的情况，或者在使用更新代码有问题的额外情况(在这种情况下请让我们知道)。
		* 再次说明，MSE+WebM 和异步 MSE 使用当前是互斥的。你只可以使用其一而不能是两者，直至我们整顿好 WebM 的代码。要启用 MSE+WebM 你将首先必须在设置中禁用异步 MSE (否则 WebM 设置将会变灰并禁用)。
	* 在选项/首选项中添加了一个控件用于 HSTS 和 HPKP 的使用。
	* 在 Windows 把 HTML 书签导出更改为写入 CRLF 行尾符到文件。
	* 促进 libVPX 的多核心渲染(VP8/VP9 WebM 解码)。
	* 修复了某些访问 DeviantArt 的问题(useragent-sniffing)。
	* 使 CSS text-align 符合规范。
	* 添加了一个还原模块用于浏览器初始化问题(例如在使用了错误的语言包时)。
	* 修复了 spurious console errors for XHR requests with certain http response codes.
	* Enabled v-sync aligned refresh for a smoother scrolling experience.
	* Removed support for CSS XP-theme media queries.
	* 改进了 console error reporting.
	* 修复了 resetting toolbars and controls from the safe mode dialog.
	* 修复了 bookmark recovery option from the safe mode dialog.
	* 修复了 innerText getters for display:none elements.
	* 修复了 a GL buffer crash that might occur with certain combinations of drivers and hardware.
	* 添加了 some more details to about:support.
	* 修复了 a potential crash when the last audio device is removed during playback.
	* 修复了 a crash on about:support when windowless browsers are created.
	* 更新了 <select> elements to blank if the actively set value doesn't match any of the options.
	* 更新了 the interpretation of 2-digit years in date formats to match other browsers:
	* 0-49 = 2000-2049, 50-99 = 1950-1999.
	* 添加了 "q" units to CSS (quarter of a millimeter).
	* 添加了 .origin property to blobs.
	* 修复了 several minor layout issues.
	* 修复了 disabled HTML elements not producing the proper JS events.
	* Implemented web content handler blacklist according to the spec, allowing more than feeds to be registered.
	* 修复了 a spec compliance issue with execCommand() on HTML elements.
	* 修复了 a problem with table borders being drawn uneven or being omitted when zooming the page.
	* 添加了 devtools "filter URLs" option in the network panel.
	* 添加了 visual sorting options to the Network inspector.
	* 添加了 importing of login data from Chrome profiles on Windows (Chrome has to be closed first).
	* 添加了 importing of tags from bookmark export files (HTML format).
	* 更新了 usage of SourceMap headers with the 更新了 spec (SourceMap header, keeping X-SourceMap as a fallback).
	* 修复了 several cases of wrongly-used negations in JS modules.
	* 添加了 the auxclick mouse event.
	* 添加了 a control to not autoplay video unless it is in view (media.block-play-until-visible).
	* 更新了 the Graphite font library to 1.3.10.
	* 更新了 how image and media elements respond to window size changes (responsive design).
	* 添加了 parsing and use of rotation meta data in video.
	* 修复了 several crashes in a number of modules.
	* 修复了 performance regression for scaling large vector images (e.g. MSIE Chalkboard test) \o/
	* 修复了 some issues with notification icons.
	* 修复了 some internal errors with live bookmarks.
	* 更新了 SQLite to 3.19.3.
	* 修复了 several reported issues with devtools (cli-cookies, cli help, copying cURL, inspecting SVGs, element size calculations, etc.)
	* 修复了 an issue where a server response was allowed to override add-ons' specified version ranges even for add-ons that have strict compatibility (e.g. themes, language packs).

**安全修复**:

	* Removed preloading of HPKP hosts and enabled HPKP header enforcement.
	* 添加了 support for TLS 1.3, the up-next secure connection protocol.
	* 修复了 an issue with TLS 1.3 not supporting renegotiation by design.
	* Relaxed some restrictions for CSP to temporarily work around web compatibility issues with the CSP-3 deprecated `child-src` directive.
	* 更新 NSS 为 3.28.5.1-PM to address some security issues.
	* 更新了 the installer selfextractor module to address unsafe loading of libraries.
	* 更改了 the way certain resources are included to reduce effectiveness of some common fingerprinting techniques. (e.g. browserleaks.com)
	* 修复了 a regression in the display of security information in the page info dialog for insecure content.
	* 修复了 two potential issues with allocating memory for video. DiD
	* 修复了 a potential issue with the network prediction algorithm. DiD
	* Restricted the use of Aspirational scripts in IDNs to prevent domain spoofing, in anticipation of the UAX#31 update making this official.
	* Prevented a Mac font specific issue that could be abused for domain spoofing (CVE-2017-7763)
	* 修复了 several potentially exploitable crashes. (CVE-2017-7751) (CVE-2017-7757) and some that do not have a CVE designation.

### 27.3.0 (2017-04-28)
A major development update. Many things have 更改了 in the media back-end, but please understand that some things are still a work in progress, and you may still encounter some html5 video playback issues with MSE.

**变化/修复**:

	* 修复了 up, checked and enabled vertical text writing modes!
	* Pale Moon will now be able to display vertical, right-to-left script.
	* 添加了 the option to reset non-default profiles.
	* 修复了 various issues in the WebP image decoder.
	* 添加了 internally-supported document types to allowed <embed> types.
	* 修复了 locale selection in ICU after update to ICU58.
	* (Note: Pale Moon uses the system locale for date formatting, not the browser locale)
	* Re-implemented the previous spellchecker dictionary logic (allow user override of document/element language, improve logic and make it unambiguous).
	* 不断进行 fixes for the MP4 parser and MSE.
	* Made HTML Media Elements' preload attribute MSE-spec compliant.
	* The preload attribute on HTML media elements is now ignored in the case of an MSE source. This prevents an issue with sourceopen not firing when preload="none".
	* 修复了 some issues with Windows WMF media playback.
	* 修复了 an issue with Synced preferences sometimes overwriting stored individual preferences.
	* 修复了 display of RSS folder icons.
	* 修复了 issues with custom context menus.
	* 修复了 an issue importing bookmarks with separators losing their extra data.
	* 更改了 the way numeric addresses are handled in the address bar so it doesn't perform a search when it shouldn't.
	* 添加了 an option (browser.sessionstore.cache_behavior) to control from which source restored tabs pull their page content:
	* 0 = load restored tab data from cache (current behavior, default)
	* 1 = refresh restored tab data from the network
	* 2 = refresh stored tab data from the network and bypass any cached data.
	* 改进了 upon a v27 performance regression with SVG scaling.
	* 改进了 performance by being more selective which CSS animations to process.
	* As a side-effect, elements changing their display from "none" to something visible now also animate.
	* Increased memory allocation for the use of very large PAC files.
	* 添加了 menu entries for the permissions manager and improvements to its function and display.
	* 添加了 preferences to control "highlight all" behavior of the find bar:
	* accessibility.typeaheadfind.highlightallbydefault = true/false highlight all found words by default.
	* accessibility.typeaheadfind.highlightallremember = true/false remember the last-used state of Highlight All.
	* 添加了 devtools command-line options.
	* 添加了 remote IP and protocol to Devtools->Network entry details.
	* 添加了 support for <details> and <summary> HTML tags.
	* 修复了 a regression in the MSIE profile migrator.
	* Removed migration of browser-specific settings when migrating data from IE/Safari.
	* Implemented optional parameters for permessage-deflate in preparation for RFC7692 errata making acceptance of them mandatory (and to prevent web compat issues due to the current conflicting text of it).
	* Made the image document favicon skinnable.
	* Aligned DOM selection addRange with the spec.
	* Exposed mozAnon constructor js binding to system scopes for XHR.
	* Enhanced form data handling from JavaScript.

**安全/隐私变化**:

	* 更新 NSS 为 3.28.4-RTM to address a number of issues.
	* 添加了 support for RSA-AES(-GCM)-SHA256/384 suites to broaden compatibility.
	* Reconfigured networking security: disabled static DHE suites by default, enabled all RSA-AES(-GCM)-SHA256/384 suites in their stead.
	* 修复了 referrer policy keyword to align with the current spec ("cross-origin" vs "crossorigin").
	* 添加了 an option to display punycode domain for IDN websites to combat phishing.
	* This is enabled by default for domain-validated https sites.
	* Preference: browser.identity.display_punycode
	* 0 = Display IDN name in identity panel (previous behavior)
	* 1 = Display punycode name for DV SSL domains (default)
	* 2 = Also display punycode for HTTP sites if IDN name used
	* 修复了 an issue to prevent contacting remote servers when a connection might get blocked.
	* 修复了 3 public security flaws in libevent, which may affect Mozilla-based products. DiD
	* 修复了 several memory- and thread-safety hazards.
	* 修复了 an address bar spoofing issue. (CVE-2017-5451)
	* 修复了 a potentially exploitable crash with HTTP/2. (CVE-2017-5446)
	* 修复了 several security hazards in XSLT processing. (CVE-2017-5438) (CVE-2017-5439) (CVE-2017-5440)
	* 修复了 several security hazards in old protocols. (CVE-2017-5444) (CVE-2017-5445)
	* 修复了 out-of-bounds access in text formatting. (CVE-2017-5447)
	* 修复了 a potentially exploitable issue with innerText. (CVE-2017-5442)
	* 修复了 a potentially exploitable issue in graphite font shaping.
	* 修复了 a potentially exploitable crash with credential-authentication.
	* 修复了 out-of-bounds access with text selection in rare cases.
	* 修复了 a security hazard in the ANGLE library.

### 27.2.1 (2017-03-24)
This is a small update to fix some stability and usability issues.

**变化/修复**:

	* 修复了 an issue with planar alpha handling (transparency) when drawing JXR images.
	* 修复了 a crash related to a change JavaScript array handling introduced in 27.2.0.
	* This became apparent with the pentadactyl extension, but could happen in other situations as well.
	* 修复了 a crash when opening ridiculously large images with HQ scaling enabled (default).
	* Pale Moon will now only apply HQ scaling for images within reasonable limits (64 Mpix or smaller). Images larger than that may not display properly when zooming in, or may not display at all, even scaled down (e.g. >256 Mpix large) and show a "broken image" placeholder instead; please use dedicated image viewer applications for those kinds of images; it is outside the scope of a web browser to handle such large images.
	* 更改了 the way URL hashes are handled, and will no longer %-decode anchor hash identifiers by default.
	* Note that this is against RFC 3986, which states that any part of the URL scheme that isn't data should be decoded.
	* This is required for web compatibility because several sites use hash links to pass actual data to web applications (Please don't do this! Hashes ar part of the URL address, should only consist of "safe" characters, and aren't suited to pass arbitrary data) and the most common browsers no longer follow the RFC in that respect.
	* If you want RFC compliance, switch dom.url.getters_decode_hash to true
	* Restored 2 RSA Camellia cipher suites that were missing: TLS_RSA_WITH_CAMELLIA_128_CBC_SHA and TLS_RSA_WITH_CAMELLIA_256_CBC_SHA
	* 修复了 an issue with custom toolbars getting deleted during upgrade from 27.0/27.1 to 27.2

### 27.2.0 (2017-03-18)
This is a major update to the browser with a focus on back-end improvements and security.

**变化/修复**:

	* 更新了 the ICU lib to 58.2 to fix a number of issues.
	* 添加了 proper control for the user for offline storage for web applications.
	* 添加了 a check to prevent auto-filled URLs from copying the auto-filled selection to clipboard/primary.
	* 添加了 the feature to pass a URL to open in a private window from the command-line.
	* 改进了 the display of the downloads indicator on the button in bright-text situations.
	* DOM storage now honors the "3rd party cookie" setting in that it will not allow 3rd party data to be stored if 3rd party cookies are disallowed.
	* Allowed toolbar button badges to be properly styled.
	* 更新了 the hunspell spellchecking library to 1.6.0 to fix a number of issues.
	* 修复了 desktop notifications being off-screen if fired in rapid succession.
	* 添加了 Element.insertAdjacentElement and Element.insertAdjacentText DOM functions.
	* 添加了 support for JPEG-XR images.
	* This makes Pale Moon have the broadest support for image formats of all web browsers.
	* (enabled by default; you can disable this with media.jxr.enabled).
	* Completely removed the use of GStreamer on Linux.
	* 添加了 support for element.innerText.
	* Custom toolbars should now properly remember their state.
	* 修复了 some more playback issues with MP4/MSE videos.
	* Please be aware that we are still working on further improving MSE video handling.
	* 更改了 media processing to reduce dangerous processing asynchronicity.
	* This should also make media elements and playback more responsive.
	* 修复了 a useragent string regression always displaying the minor Goanna version as .0
	* 更新 NSPR 为 4.13.1.
	* 更新 NSS 为 3.28.3-RTM.
	* 修复了 unrestricted icon sizes in PMkit buttons.
	* 修复了 unresponsive buttons on support page when not building the updater.
	* 修复了 the use of "View image" and "Save image as" on extremely large images.
	* 更改了 the way "View Image" and "Save image as" work on canvas elements.
	* Made checking for dangerously large resolution PNG images smarter.
	* It will now accept larger "strip"-aspect ratio images while reducing unsupported large image resolutions.
	* This will e.g. fix Gmail's "emoji" window that uses a ridiculously long but very narrow single image to store all the emoticon pictures.
	* Converted several hard-coded URLs to preferences.
	* 更新了 the google.com override so it would not cripple services based on UA sniffing.
	* 添加了 Inner and Outer Window ID administration.
	* 修复了 the add-on discovery pane detection.
	* 添加了 support for canvas ellipse.
	* 改进了 drawing of certain MathML elements at problematic zoom levels.
	* No longer building gamepad support.
	* 更新了 Harfbuzz font shaper to 1.4.3 to fix a number of issues.
	* 修复了 数个崩溃。(layout, plugins, uncommon navigation, bad URLs).
	* Aligned SVG specular filters with the spec.

**安全/隐私变化**:

	* 添加了 support for 256-bit AES-GCM encryption.
	* 添加了 support for ChaCha20-Poly1305 encryption.
	* Removed support for Camellia-GCM since nobody seems interested in it.
	* (Camellia in 128/256-bit CBC block mode is still fully supported).
	* 添加了 support for SHA-224, SHA-256, SHA-384 and SHA-512 to Crypto utils.
	* 改进了 status handling of secure sites to be less sensitive to "insecure" items that are local.
	* 修复了 print preview hijacking. (CVE-2017-5421)
	* 修复了 a potentially exploitable crash in OnStartRequest. (CVE-2017-5416)
	* 修复了 potential cross-origin content-stealing through a timing attack. (CVE-2017-5407) DiD
	* 修复了 a denial-of-service problem with view-source. (CVE-2017-5422)
	* 修复了 crash in directional controls. (CVE-2017-5413)
	* 修复了 a perceived problem with chrome manifests. (CVE-2017-5427)
	* 修复了 the use of an uninitialized value. (CVE-2017-5405)
	* 修复了 a buffer overflow. (CVE-2017-5412)
	* 修复了 a UAF situation. (CVE-2017-5403)
	* 修复了 a potential spoofing issue with the address bar. (CVE-2017-5417)
	* 修复了 a potential issue in libvpx. (CVE-2017-5402) DiD
	* 修复了 a potential issue with HTTP auth. (CVE-2017-5418)
	* 修复了 several memory safety hazards and potentially exploitable crashes. DiD

### 27.1.2 (2017-03-03)
This is a small update adding a workaround for potential deadlocks happening in media elements.
### 27.1.1 (2017-02-21)
这是对浏览器的一个稳定性和错误修复的更新。

**变化/修复**:

	* Implemented a fix in media handling to prevent crashes with concurrent videos and/or rapidly starting/stopping video playback in the browser.
	* 修复了 the way the Adobe Flash plugin is detected to prevent confusion with other plugins that identify themselves as "Flash" (e.g. VLC).
	* Windows: Solved stability issues caused by the release build process, resulting in unexpected behavior (e.g. hangups).

### 27.1.0 (2017-02-09)
This is a major update with lots of development and bugfixes. It also introduces the so-called "PMkit" modules, our effort to restore compatibility with Jetpack/SDK extensions and making it possible for extension developers to convert their SDK extensions with little effort to a Pale Moon compatible format. For more details please check the PMkit documentation on the developer wiki.

**变化/修复**:

	* Reworked the media back-end completely (thanks Travis!) to use FFmpeg (including support for FFmpeg v3 and MP3 playback) and our own MP4 parser, and no longer relying on gstreamer on Linux, as well as adding some improvements on Windows for media parsing and playing.
	* On Linux, Apple .mov files of the correct type will also be played through FFmpeg now, for those rare occasions where they are still in use, considering there is no Quicktime plug-in available on that operating system.
	* Restored the classic about:config styling.
	* 添加了 a fallback to US-ASCII if the autoconfig UTF-8 conversion fails.
	* 改进了 cross-compartment wrapper handling when managing a large number of tabs (fixes a performance regression with v27).
	* 更改了 the way audio and video synchronization is calculated to account for (slow) device latency, preventing things from getting out of sync on e.g. BlueTooth-connected speakers.
	* 更改了 the way scripts are handled when they are stopped from the "unresponsive script" dialog, to prevent browser lockup. We will now stop all scripts in the affected compartment in one go.
	* 修复了 several errors in the devtools.
	* 修复了 a nasty crash caused by cross-origin referrers.
	* 修复了 the installer to allow 64-bit versions of the browser to be installed on Vista again.
	* 添加了 HTML5-spec clipboard handling for content (cut&copy only -- paste is not allowed for security reasons).
	* Made multiple changes to the toolkit jetpack modules to cater to PMkit extensions.
	* This should make running SDK-based modules as PMkit extensions fairly simple for extension developers. See the introductory text to these release notes.
	* 修复了 a css layout issue: make max-width affect contributions to intrinsic min-width.
	* Implemented several updates to the permissions manager. Among others, 改进了 the permissions manager (about:permissions) with a more complete set of permissions for pages.
	* Removed otherwise unused Metro browser platform/widget code.
	* Removed support for non-standard/deprecated let blocks and expressions.
	* Made the use of let as a keyword versionless and ES6 compliant.
	* Made the privacy category in preferences a tabbed setup to better fit the current options.
	* 修复了 a regression preventing certain MP4 video files from playing.
	* 修复了 a regression where seeking in media files would halt playback/jump to the end of the stream.
	* 修复了 a crash caused by certain downloadable fonts with DirectWrite in use.
	* 改进了 downloads-button indicator legibility on some combinations of Windows versions and system theme colors.
	* 更改了 the Facebook user-agent override to be our native one, based on reports from users that it is (finally) working acceptably.
	* 修复了 site-specific useragents being ignored if a global override is defined.

**安全/隐私变化**:

	* 更改了 CORS handling to allow data: sources, assuming they are same-origin. This should fix the infamous "Facebook endless reload" issue and may make some other sites that assume this particular (unspecified) CORS behavior happy with Pale Moon.
	* Reinstated the network.stricttransportsecurity.enabled preference so people who choose privacy over HSTS can do so again.
	* 添加了, In HSTS "off" state, prevention of HSTS site status from being written to disk.
	* 更新了 the IDN blacklist with more extended unicode characters that "look very similar to" normal ASCII characters, to prevent spoofing of well-known domains. If blacklisted characters are found, the IDN domain name will be displayed in its punycode form. (CVE-2017-5383 and similar)
	* 修复了 an exploitable crash when using MP4 video. (CVE-2017-5396)
	* 修复了 an exploitable crash in XSL parsing. (CVE-2017-5376)
	* 修复了 a potential security issue when exporting certificates with specially-crafted credentials. (CVE-2017-5381)
	* 修复了 a potential use-after-free situation in frame selection. (CVE-2017-5380) DiD
	* 修复了 a leak of window details through the Ion compiler in certain situations.
	* 修复了 the potential for an exploitable crash involving Javascript GC. DiD
	* 修复了 a potential overflow situation in (non-released) WebRTC code. DiD
	* 修复了 a potentially unsafe situation in websockets. DiD
	* 修复了 several memory and other safety hazards (BMO bugs 1318766, 1325877, 1328834 DiD, 1288561 DiD, 1322420 DiD, 1293327 DiD, 1322315, 1325344, 1285960).

### 27.0.3 (2016-12-16)
这是一个错误修复和安全更新。

**变化/修复**:

	* 修复了 certain network errors not displaying.
	* 修复了 network error page styling.
	* 修复了 the writing of DOM storage data to tabs (should solve the "tabs not loading their contents" issue when migrating a profile and some other situations).
	* Disabled downloadable font unicode-ranges on non-Windows platforms.
	* 添加了 a Google Fonts user-agent override for non-Windows platforms so they don't send unicode-ranged composite fonts (Feature detection? Google apparently still doesn't know what that is).
	* Re-enabled the reporting of CSS errors to the console by default to prevent issues with some extensions who rely on this (e.g. Stylish).
	* 修复了 and 更新了 preferences for location bar suggestions.
	* 修复了 several x64-specific issues in memory allocation code (regression fix).
	* 修复了 timer issues when resuming a computer from stand-by (regression fix).
	* 修复了 a number of branding and textual issues in the browser.
	* 修复了 prompting for the saving of off-line data (previously always allowed without prompting).
	* 修复了 a layout regression that would cause block elements following left floats to not wrap to the next line if there wasn't enough clearance.
	* 修复了 a mismatch in Firefox extension compatibility-mode installation where Firefox extensions served by addons.mozilla.org would be marked incompatible when trying to install.

**安全相关和崩溃修复**:

	* 修复了 use-after-free while manipulating DOM events and removing audio elements (CVE-2016-9899).
	* 修复了 CSP bypass using the marquee tag (CVE-2016-9895).
	* 修复了 a vulnerability in the internal Jetpack modules (CVE-2016-9903). DiD
	* 修复了 use-after-free in Editor while manipulating DOM subtrees (CVE-2016-9898).
	* 修复了 an error in the buffer logic in http-chunked decoder.
	* 修复了 a crash in generational GC code (not in use by default) DiD
	* 修复了 a compartment mismatch bug in plug-in code
	* 修复了 a crash trying to get a nonexistent property.
	* 改进了 MediaRecorder's observer safety.
	* 修复了 a crash related to document history.

DiD 这意味着这个修复是 "Defense-in-Depth"(深度防御): 这是一个并非应用于 Pale Moon 中的(潜在的)活跃的可利用漏洞， 而是用于防止相同的代码在周边的代码发生变化而暴露问题从而导致未来的漏洞的修复。
### 27.0.2 (2016-12-02)
This is a minor update to address usability and security issues:

	* Enabled Firefox Compatibility mode by default for the useragent string.
	* Unfortunately too many websites (and especially the big players who should know better like Google, Apple and Microsoft) still require the "we must pretend to be Firefox if we want this site to work" status quo to be maintained, because people still insist on using useragent sniffing to determine "browser features", or even worse, discriminate against free choice of browser by flat-out refusing service (I'm looking at you, banking industry and cloud services!) when visiting websites just because companies don't want to provide assistance to any but users on the main 3.
	* HTML offers plenty of ways to do proper feature detection; site owners should use them.
	* Seriously people, it was a bad idea 20 years ago, and it's a worse idea in 2016.
	* The built-in devtools are back, and with a facelift!
	* Thanks to some consistent community help, the built-in devtools, sorely missed by a number of our users, are back. They've received a code and style update and should be fully functional on the new platform. This was originally planned for 27.1, but it was decided to include this as soon as possible, not in the least to assist extension developers in their efforts to adapt to Pale Moon 27.
	**安全修复**:
	* 修复了 a crash in SVG, related to CVE-2016-9079, as a defense-in-depth measure.

### 27.0.1 (2016-11-28)
This is a bugfix release for some of the issues that popped up with the new milestone.

**变化/修复**:

	* 修复了 removal of distribution/bundles/ copies of status bar code and ruby annotations code.
	* This should clean up everything on install/upgrade that currently causes double code to create intermittent/odd behavior.
	* Backed out some media back-end changes to fix MSE playback on Twitch.tv and other similar sites.
	* Disabled pop-up network status in full screen by default (since video detection is rather iffy at the moment).
	* 修复了 a regression causing the "reset profile" button to not appear in about:support on the default profile.
	* 解决了 bad Netflix interface changes - it will now use a more compatible web UI.
	* Please note that these Netflix changes were unrelated to the actual release of Pale Moon (26.5 is also affected).
	* Aligned base status bar colors with default prefs.
	* 修复了 status bar options not being remembered.
	* 添加了 an override for Amazon Prime videos so they won't stop us at the front door any longer when not using the Firefox Compatibility user agent mode.
	* Re-applied proper branding text to in-app licensing.

### 27.0.0 (2016-11-22)
After about 8 months of development, we now have a new milestone release with literally too many changes to list even concisely. These release notes will therefore only highlight the most important parts of this release.
In this release we've done a full upgrade of our back-end platform, meaning many things work different "under the hood" and you may run into a number of extension compatibility issues as a result.

**新增和更新功能**:

	* Support for DirectX 11 and Direct2d 1.1 on Windows. This will bring Pale Moon more in line with the capabilities for current-day operating systems and graphics hardware.
	* Update of the Goanna engine to 3.0 - with many changes to layout and rendering for the modern web.
	* Pale Moon now fully supports HTTP/2.
	* Ruby Annotations are now an integral part of the HTML parser, controllable with CSS.
	**媒体** Source Extensions have been implemented to solve many video playback issues.
	* This can be enabled/disabled and configured in Options. It's recommended at this time to not enable MSE for WebM since there are a few issues with it on services like YouTube (e.g. losing audio when looping/skipping).
	* Support for reading and playing so-called "fragmented" MP4 files has been 添加了, further solving media playback issues.
	* Support for SSL/TLS connections to proxy servers.
	* Support for the WOFF2 font format for downloadable fonts.
	* The JavaScript engine has been 更新了 with support for many landmark ECMAScript6 features (chief among them promises and generators). This will solve many of the web compatibility issues that people have started to run into in the past few months (e.g. webmail interfaces, some sites coming up blank because they are script-generated).
	* The way web content is cached has been 更改了 to be more efficient. If you want to immediately take advantage of this, clear your cache.

**移除的支持/功能**:

	* Removed support for Windows XP. If you are still running Windows XP, then your only option is to continue using Pale Moon 26.
	* Removed the internal PDF (pre)viewer. This module was not maintained, was unable to display even half of the PDF documents correctly, and could not reasonably remain included in the browser. Please use a separate reader and/or install a PDF reader plugin.
	* Disabled building of the devtools. They will not be included in release versions of Pale Moon from this point forward. If you are a web developer or otherwise need those tools, fear not! They are available as a browser extension.
	* Removed the active XSS filter. This feature, although effective, was prone to some instability and needs to be rewritten for the update of our platform. It may or may not return in the future, depending on whether the original author has time to rewrite parts of this filter implementation.
	* Removed support for Add-on SDK extensions (JetPack extensions), considering the Mozilla/Gecko SDK is no longer compatible with our combination of application and platform code.

**安全突显**:

	* All relevant **安全修复** up to and including Firefox 50 have been ported across from Mozilla to continue to provide an as secure as possible browser.
	* Several libraries have been 更新了 to their latest versions to pick up any important vulnerability fixes.
	* There's a new option and control to determine whether to save zone information (marking files as "downloaded from the Internet") on downloaded files (Windows+NTFS). You can find this in Options.

**其它重要事项**:

	* When first upgrading your browser to v27, your profile will be migrated to the new format for the browser. This is a one-time conversion and unfortunately this migration can cause some issues. Please see the forum FAQ for more details.
	* Pale Moon 27 will initially only be available in English. We are working on getting localization done to have language packs available over time.
	* Important: You can not use the previous language packs since many strings have 更改了. Trying to do so will likely prevent the browser from starting or functioning. Pale Moon will automatically disable language packs for the previous version, but if you have explicitly disabled add-on compatibility checking you may run into trouble.
	* We will continue to fully support the following:
		* NPAPI plugins
		* Extensions with binary/XPCOM components
		* XUL/Overlay and bootstrapped extensions
		* Complete themes
		* Unsigned and author-signed extensions
		* The Camellia encryption cipher (also in GCM mode)
		* Graphite font shaping
		* Sync 1.1 (albeit without support for syncing add-ons)
		* Full customization of the UI as before

Release notes for version 26 releases
### 26.5.0 (2016-09-28)
**修复/变化**:

	* Implemented a breaking CSP (content security policy) spec change; when a page with CSP is loaded over http, Pale Moon now interprets CSP directives to also include https versions of the hosts listed in CSP if a scheme (http/https) isn't explicitly listed. This breaks with CSP 1.0 which is more restrictive and doesn't allow this cross-protocol access, but is in line with CSP 2 where this is allowed.
	* 修复了 an issue with the XML parser where it would sometimes end up in an unknown state and throw an error (e.g. when specific networking errors would occur).
	* 改进了 the performance of canvas poisoning by explicitly parallelizing it.

**安全修复**:

	* 修复了 a potentially exploitable crash related to text writing direction. (CVE-2016-5280)
	* Made checking for invalid PNG files more strict. Pale Moon will now reject more PNG files that have corrupted/invalid data that could otherwise lead to potential security issues.
	* 更改了 the way paletted image frames are allocated so the space is cleared before it's used. DiD
	* 修复了 a crash in nsNodeUtils::CloneAndAdopt() due to a typo. DiD
	* 修复了 several memory safety issues and crashes.

DiD 这意味着这个修复是 "Defense-in-Depth"(深度防御): 这是一个并非应用于 Pale Moon 中的(潜在的)活跃的可利用漏洞， 而是用于防止相同的代码在周边的代码发生变化而暴露问题从而导致未来的漏洞的修复。
### 26.4.1 (2016-09-12)
This is a minor bugfix and security release.

**变化/修复**:

	* 修复了 a crash in the XSS filter.
	* Slightly 更改了 the address bar shading on secure sites to be more subtle and easily-blended.
	* 修复了 the occurrence of "null" titles in bookmarks dragged from special folders.
	* 修复了 an error initializing the browser due to trying to restore scratchpad data from a stored session when having switched from a version with devtools to a version without devtools, and the previous version had scratchpad data saved.
	* 修复了 some minor issues in scratchpad and gcli devtools.

**安全修复**:

	* 更新了 the HSTS preload list to a much more 更新了 source list, and performing our own checks on validity from now on to have the list be as accurate as possible.
	* Disabled Triple-DES cipher suites by default (mitigating SWEET32).

Portable-only: 更改了 the behavior to, by default, allow it to start a new copy or multiple copies without checking if Pale Moon is already running on the system. You will need separate profiles to run multiple browsers concurrently.
### 26.4.0.1 (2016-08-23) - Linux only
This Linux-only release is once again using GStreamer 0.10 for video support, which should prevent Pale Moon from crashing when playing some HTML5 videos.

Additional **变化/修复**:

	* A blacklist for GStreamer has been implemented and enabled by default (can be disabled with the media.gstreamer.enable-blacklist about:config pref).
	* The flump3dec GStreamer plugin (known to be crashy) & h264parser element (a potential security risk) have been blacklisted.
	* 修复了 a couple other GStreamer related crashes.
	* No longer force Link Time Optimization with GCC 6

### 26.4.0 (2016-08-17)
**变化/修复**:

	* Removed Google Search as a bundled search provider. If desired, you can manually install it (or other search engines) after the update by following the steps in the Manage Search Engines topic.
	* 修复了 the URL API to allow "stringification" of the object per specification. This should make a number of websites happy.
	* 添加了 the ES6 string .includes() function in addition to the pre-existing .contains() function for checking if a string contains another string. The .contains() function is retained for compatibility with web and extension scripts that adhere to the ES6 pre-release specification up to and including RC3.
	* 修复了 the calculation of standalone SVG embeds width and height, which should solve some reported issues with html5 graphs being displayed incorrectly.
	* Linux: 改进了 memory allocation.
	* 更新了 the graphite font library to 1.3.9.
	* 添加了 a blocking rule for F-Secure's 64-bit deepguard library to prevent crashes.
	* 更新了 the SQLite library to 3.13.0.
	* Download= properties of links are now honored from the context menu "Save" option.
	* 修复了 a crash in the XSS filter.
	* 修复了 a crash in the DOM error module.
	* 解决了 a crash on Linux
	* Linux: 改进了 optimization and GCC6 compatibility (Note: compiling with GCC 6 is still not recommended and it may or may not work, depending on your environment)

**安全修复**:

	* (CVE-2016-5251)Potential URL spoofing in the address bar.
	* (CVE-2016-0718) Context-dependent crash in expat 2.1.0.
	* (CVE-2016-5266) Outgoing dataTransfer items are not properly filtered.
	* 修复了 potentially exploitable crash in the array splice implementation.
	* 修复了 potentially exploitable crash caused by badly formatted ICO files.
	* (CVE-2016-5254) Heap-use-after-free in nsXULPopupManager::KeyDown

### 26.3.3 (2016-07-01)
Another small bugfix update to address some breaking issues. Sorry for the rapid-fire releases, everyone; this is not our intention.

**变化/修复**:

	* 修复了 an additional issue found that could cause menu text on Windows 10 to be white-on-white (and therefore unreadable).
	* 修复了 an issue with news feeds not showing up when embedded in web pages.
	* Removed recently-添加了 parsing of the child-src content security policy directive, after some web compatibility issues with it came to light, as well as it becoming clear that the CSP spec will see it removed in favor of the previous directive for embedded content. This should fix some intermittent issues people have reported on e.g. the main google.com page and phpMyAdmin installations.

### 26.3.2 (2016-06-27) - Windows only
This release only has pertinent changes for Windows. Other operating systems do not need this update.

**变化/修复**:

	* 修复了 a rare issue where the browser would not initialize properly (missing bookmarks and menu entries) if certain Windows registry values were missing (Windows 8 only).
	* 修复了 an issue on Windows 10 where the classic menu bar would become unreadable (white on white).
	* Update: There's apparently a different issue still remaining that can cause the same trouble. Please see the Known Issues page for status and workaround.
	* Portable only: Switched to non-compressed binaries to prevent issues with antivirus packages, to prevent issues with browser run-time operation, and to simplify code signing.

### 26.3.1 (2016-06-25)
**变化/修复**:

	* 修复了 an issue with new tab button theming on dark toolbars.
	* Reverted the useragent identification of Firefox compatibility mode to 38.9 to avoid WOFF2 font issues for sites that don't use proper font deployment as recommended by the W3C.
	* 添加了 a site-specific override for Google fonts to make sure it always works even if not using Firefox compatibility mode.
	* (workaround pending for a proper solution on Google's side)
	* Adjusted the "dark color" detection routine to switch text to white at higher relative contrast levels.
	* This will more closely match Windows 10's "flip point" for different accent colors and is within the recommended range determined by the WCAG.

### 26.3.0 (2016-06-21)
**变化/修复**:

	* 添加了 detection for dark system themes on Windows 10 and re-worked Windows 10 specific theming to better integrate into the OS and provide more clarity.
	* HTML5 media controls have been reworked to a horizontal volume control on all media, including HTML5 audio that was previously without an element-control for volume.
	* Default HTML5 media volume preference 添加了 as media.default_volume -- fractional, default 1.0 (=100%).
	* String.prototype.match() and .replace() are now fully spec compliant.
	* NSPR and NSS now correctly no longer enforce IA32 architecture compatibility, getting the advantage of SSE2 like the rest of the code.
	* 解决了 crashes in the XSS filter when navigating back in history due to document fragments.
	* Instated a hard minimum of 10,000 places entries regardless of free disk space and total memory to prevent undesired expiration of history. That is around 16MB for an average entry size, which should be sane enough even on low-memory machines.
	* 修复了 a typo in networking code introduced in 26.2.2 that would cause issues on some sites due to adding extra forward slashes to the URL.

**安全修复**:

	* 修复了 a number of memory safety hazards and potentially exploitable crashes.
	* 修复了 CVE-2016-2821 Use-after-free in the mozilla::dom::Element class
	* 修复了 netaddr deserialization for AF_UNSPEC and AF_LOCAL.
	* 修复了 a memory overrun error in the VP8 encoder. DiD
	* 修复了 non-threadsafe re-use of pixman images to prevent potential race conditions. DiD
	* 修复了 CVE-2016-2825 Partial Same Origin Policy violation

### 26.2.2 (2016-05-10) & Android 25.9.2
This is mainly a security update.

**变化/修复**:

	* 添加了 a detection routine for dark window colors on Windows 8 and later (system themes using dark window frames) to better adapt to dark system colors. Theme developers can take advantage of this by checking for darkwindowframe="true" on #main-window in CSS selectors.
	* CSS classes pre修复了 with "--" no longer stop parsing of the selectors.
	* Several crash fixes.

**安全修复**:

	* Made GC suppression more aggressive to prevent issues when actually out of memory.
	* 修复了 a memory safety hazard in jpeg decoding.
	* 修复了 a potentially exploitable crash when using bi-directional text.
	* 更新 NSS 为 3.19.4.2-PM, fixing CVE-2016-1938 among other things.

### 26.2.1 (2016-04-08)
This is a small update to fix a problem with keyboard navigation of the user interface.
### 26.2.0 (2016-04-05)
This is a major update and bugfix release.

Changes:

	* Implemented the URL API that's needed for a number of websites.
	* 更改了 internal keystroke handling within the spec to better align with generally expected behavior.
	* This should fix the infamous "backspace" issue on Facebook.
	* Web developers please note: calling preventDefault() in a "keydown" event handler will now prevent most keypress events from firing.
	* Linux: gstreamer 1.0 support has been implemented and enabled by default (hats off to Travis!)
	* From this version forward you will need to have gstreamer 1.0 libraries for video playback (0.10 is no longer supported).
	* Re-styled about:sessionrestore to use more available screen real estate for tab info.
	* 添加了 an option to use the mousewheel for horizontal scrolling (mouse action value 4).
	* (e.g. setting mousewheel.with_shift.action to 4 makes Shift+wheel scroll horizontally)
	* Bumped max icon size for search engine icons to 32 KB to cater to more common use of HiDPI icons.
	* 修复了 some hard-coded branding strings in Sync still reading "Firefox", and similarly 更改了 sync information URLs to point to our relevant pages.
	* Removed default profile bookmarks pointing to Firefox/Mozilla since the information there no longer applies to us.
	* 更新了 UA overrides and XSS configuration to deal with some problematic sites (e.g.: Google, Embedly)
	* 修复了 several issues with the default theme causing problems with behavior due to styling (thanks, Antonius32) (Issue #384 and friends)
	* 修复了 some miscellaneous issues in the internal jemalloc implementation.
	* 添加了 a configure option to use the full jemalloc lib (jemalloc v3) if the builder so wishes (used for Linux, sys mallocs are not happy there either, so for our generic binaries we switched to this lib now)
	* 解决了 a crash caused by the XSS filter on some fora by bailing on too short and empty strings.
	* 修复了 layout of reflowed comboboxes without enough space.
	* 修复了 a crash related to flexboxes overflowing themselves. (Issue #396)
	* 添加了 a simple implementation for Weak Messagelisteners. (Issue #399)
	* 修复了 a crash for losing our cache entry while finishing up compression.
	* (re-apply after unintentional back-out switching to Goanna)
	* Linux: 解决了 driver bugs with Intel drivers that falsely report what they can support in max texture size.
	* Portable only: Removed compression of the browser components library after some reports that in certain configurations and environments it was causing issues with the browser.

**安全修复**:

	* 更新了 the graphite font library to 1.3.7+ to solve CVE-2016-2796 and no less than 14 of its friends.
	* 更新 NSS 为 3.19.4.2-PM to address several vulnerabilities (UAF, heap overflow).
	* 更新了 libvorbis to a much more recent version to fix multiple issues.
	* Crash fix and DiD fixes by holding strong references to objects in suspect places in the HTML parser. (CVE-2016-1961) (ZDI-CAN-3574)
	* 修复了 several out-of-bounds issues in the VP8 decoder.
	* 修复了 a potentially exploitable crash in XML/XSLT handling.
	* Applied some Kung Fu to HTML animations and transitions to prevent memory hazards.
	* 修复了 applicable Mozilla code vulnerabilities CVE-2016-1965, CVE-2016-1960 (ZDI-CAN-3545), CVE-2016-1966, and CVE-2016-1963.


### 26.1.1 (2016-02-24)
This is a bugfix release to improve stability and extension compatibility.

**变化/修复**:

	* 修复了 a few oversights in the Firefox extension compatibility changes in 26.1.0 that should improve compatibility with a number of Firefox extensions.
	* 更改了 memory handling to (hopefully) address the memory inflation issues some people have experienced with 26.1.0.
	* 更新了 YouTube compatibility, which should once again allow users to choose between Flash and HTML5 players on YouTube.

### 26.1.0 (2016-02-16)
This is a web compatibility, stability and bugfix release.

**变化/修复**:

	* Disabled our ES6 Promise implementation introduced in 26.0 since there were some severe issues with its implementation that caused a lot of inexplicable failures on websites. This means that some sites that insist on using Promises without checking availability and that do not provide sufficient web client compatibility by way of server-side libraries or polyfills will currently not work as-intended. Apologies for any inconvenience this may cause; providing a perfectly-working implementation will be our top priority going forward.
	* 改进了 website compatibility with many sites and web applications by making our cookie gate less strict.
	* 修复了 web compatibility with Google Hangouts and Yahoo Calendar.
	* 更改了 the memory allocator on Windows platforms to a much more modern full-library implementation of jemalloc, with miscellaneous additional fixes. This should give comparable speed to the system one and will allocate free memory more dynamically. This should fix issues like "huge animated gif choking" and inexplicable pauses when using many tabs, scrolling (extremely) long pages, or viewing media.
	* 修复了 a few rare crashing issues on Windows due to the build process.
	* Reduced so-called "jank" on inner frame scrolling reflows.
	* Extension compatibility: partial implementation of Firefox 26 download js modules as shims; this should make more Firefox extensions compatible with us out-of-the-box. (Thanks, Chaoskagami!)
	* 添加了 a "superstop" key combination (Shift+Esc) that will stop all (foreground and background) network activity, stop animated gifs, etc. even after the page itself has fully loaded (and the stop button not being available) - some web applications may not like this if you use it since it will also cancel XHR requests, etc.
	* 更新了 NTLM authentication, deprecating v1 and adding a proper v2 implementation (Thanks, Trava90!)
	* 更新了 the default theme to tweak/improve it some more (Thanks, Antonius32!)

**安全修复**:

	* 更新了 the Graphite2 font library to 1.3.5+ to fix a number of vulnerabilities (and some font bugs).

### 26.0.3 (2016-02-05)
This is a small bugfix release:

	* 更改了 our cookie gate to allow cookie names with spaces in them, to improve web compatibility.
	* Critical note: if your site uses cookie names with spaces in them, please consider moving away from doing that so you are no longer in the "grey" area of cookie behavior.
	* 更改了 the configuration of our XSS filter to address some known, harmless filter hits that have been reported.

### 26.0.2 (2016-02-03)
This is a bugfix, security and web compatibility release.

**变化/修复**:

	* Removed the sanity check for unsupported point-of-sale XP-based operating systems by user request.
	* Please see the forum for information on which operating systems we can reasonably support.
	* 更改了 the way "transparent" is handled in Goanna to improve transparent gradients using this keyword.
	* Made sure that dom.disable_beforeunload is predefined in about:config.
	* 修复了 web compatibility issues with Youtube, Youtube Gaming, Yuku fora and Netflix.
	* 修复了 web compatibility with Comcast/XFinity webmail and other sites or web applications that expect older JavaScript versions as default.
	* Reinstated the about:config warning by default.
	* 修复了 2 potential browser crashes.

**安全修复**:

	* 更新 NSS 为 3.19.4.1-PM to fix a potential UAF and CVE-2015-7575.
	* Crash fix: Prevented queueing multiple media sources that could lead to unsafe memory access.
	* Prevented unsafe memory manipulations in zip archives. (CVE-2016-1945) DiD
	* Prevented a potential buffer overflow in WebGL. (x64 only) (CVE-2016-1935) DiD
	* 更新了 the way binaries are code-signed. Not only does v26.0 use a new SHA256-signed digital certificate, but starting this version will also be signed with both SHA1 and SHA256 digest algorithms to satisfy later Windows' code-signing requirements.

DiD 这意味着这个修复是 "Defense-in-Depth"(深度防御): 这是一个并非应用于 Pale Moon 中的(潜在的)活跃的可利用漏洞， 而是用于防止相同的代码在周边的代码发生变化而暴露问题从而导致未来的漏洞的修复。
### 26.0.1 (unreleased)
Internal development/test version.
### 26.0.0 (2016-01-26)
This is a new milestone release! It's been in the works for a good number of months, and has many hundreds of notable changes, fixes, and improvements that can't possibly all be listed here.

These release notes for this version are a concise summary, lifting out the most prominent and important changes. You may find slightly more detailed release notes on the forum.

**一般发行说明**:

	* Goanna logoPale Moon is now building on the new Goanna engine instead of Gecko. Although close relatives in terms of web technology, they are not the same under the hood and any reports of bugs with the layout/rendering engine should be as detailed as possible to allow us to pinpoint the cause of the bugs and fix them (just stating "it works in Firefox" really doesn't help us!). If you wish to report issues, please either use the issue tracker on GitHub or report a detailed description and steps to reproduce on the forum.
	* We've had to reduce the number of supported languages for our language packs. With the need to move to our own full localization and lacking translators to support and maintain less common languages in use around the world, we've reduced our number of offered languages to a little over 30. The languages still supported should more than cover the common languages spoken around the globe. You will need to update your language packs!
	* Although we've given this release extensive testing, it is still possible you run into some website compatibility issues (usually because of websites doing useragent sniffing) and e.g. some sites displaying a mobile version if they do not recognize or incorrectly recognize the new browser engine. Please always try contacting the webmasters first before posting support requests at our address, since this is usually not something we can provide solutions for, ourselves, and we end up having to redirect you anyway.

**修复/变化**:

	* The layout parser/renderer has received many updates with this change over to Goanna, improving web compatibility and standards compliance in many areas.
	* The browser user interface has received updates, making it more compatible with Windows 10 in many respects and more in line with the general styles of the operating system version it is run on in terms of the shapes of controls and color setting.
	* 更新了 graphics/media support: Pale Moon now supports the WebP image format, properly scales EXIF rotated JPEGs, has 更新了 support for different WebGL texture formats, 改进了 scaling of vector images, 更新了 libpng, libjpeg-turbo, libvpx, and misc other upstream libraries/modules, and more!
	* Library changes:
		* The library now has a scope bar (pops up when searching) with the option to select what you want to search in (either bookmarks or history) and the option to save your searches.
		* By default, there will be a history menu drop-down in the browser's user interface next to the bookmarks one.
		* 添加了 "Containing folder" and "Containing folder path" columns so you can see exactly where a bookmark is located at a glance when searching (after enabling the columns).
	* 添加了 support for Ruby annotations. If you need this functionality, set the about:config preference browser.ruby.enabled to true, and restart the browser.
	* 添加了 conservative image decoding: it will now only decode images that are (almost) in view, greatly improving overall memory use and initial loading of graphics-heavy pages.
	* Aligned 3D CSS transforms and perspective with the spec.
	* JavaScript improvements: 添加了 basic support for ES6 Promises, 添加了 element.matches(), 更新了 property assignments, 添加了 Bin/Oct literals in Number(), 改进了 performance of TypeOf calls, 改进了 GC memory shrinking, 改进了 memory allocations, 改进了 RegEx performance and compatibility, and more!
	* 添加了 CSS media queries to determine the OS the browser is running on, allowing theme designers to make specific changes based on OS at run-time.
	* 添加了 a control preference for onunload= events as dom.disable_beforeunload. This allows you to completely disable events fired when leaving a page.
	* 更改了 the memory allocator to the (faster) system allocator on modern operating systems.
	* 改进了 the handling of very large numbers of tabs.
	* 添加了 Ecosia as a "green" search engine alternative for the environmentally aware surfer.
	* Autoplay of media now has a separate control preference for scripted content as media.autoplay.allowscripted, to block script-initiated autoplay of media.

**安全更新**:

	* 添加了 support for 128-bit Camellia-GCM ciphers in addition to the existing CBC ciphers to offer a more internationally diverse choice of secure encryption ciphers than just AES.
	* 添加了 an advanced, active XSS (cross-site scripting) filter. Pale Moon will now check for XSS attacks and block XSS content in the resulting pages. This is brand-new technology and feedback on this filter specifically (e.g. bugs, false positives, etc.) should be posted in the dedicated thread on the forum for this feature. Please also see that thread for details on how to use and control this filter.
	* Distrusted several root certificates in accordance with security best practice.
	* Aligned cookie acceptance with RFC 6265 §4.1.1. We still make an exception for allowing spaces and double quotes in cookie values, but this will be made more strict in the future for full spec compliance. If you are a web designer and use cookies, please verify that you are RFC compliant in terms of both cookie names and cookie values, or the browser may reject them.
	* Removed several hazardous modules like the maintenance service and the identity module.
	* Ported all security updates from Mozilla that are applicable/relevant to our code base (up to and including all security issues made known to us until now). Considering v26 has been kept 更新了 over its long development until release, the list of fixes/CVEs would be too exhaustive to list in these release notes individually.


Release notes for version 25 releases
### 25.8.1 (2015-11-28)
A small update to address two important issues:

	* Fix for a crash that could occur at random since the update to 25.8.0.
	* Fix for CSP (Content Security Policy) to be more lenient towards the incorrect passing of full URLs with all sorts of parameters in the CSP header, leading to misinterpretation of the header and incorrectly blocking the loading of content.

### 25.8.0 (2015-11-17)
This is a security, stability and usability update.

**修复/变化**:

	* 更新了 LibVPX to 1.4.x to be able to play more kinds of VP9-encoded videos.
	* 更新了 the JPEG decoder library to 1.4.0.
	* 修复了 and cleaned up XPCOM timer thread code to avoid intermittent issues with events not firing (especially after stand-by).
	* 更新了 overrides to work around issues with Facebook and Netflix.
	* 修复了 an issue where too-old system-supplied NSPR and/or NSS libraries would be accepted for use.

**安全修复**:

	* 更新了 the libpng library to 1.5.24 to address critical security issues CVE-2015-7981 and CVE-2015-8126
	* 更新了 the NSPR library to 4.10.10 to address several security issues.
	* 更新了 the NSS library to 3.19.4 to address several security issues.
	* 修复了 a memory safety hazard in SVG path code (CVE-2015-7199).
	* 修复了 an issue with IP address parsing potentially allowing an attacker to bypass the Same Origin Policy (CVE-2015-7188).
	* 修复了 an Add-on SDK (Jetpack) issue that would allow scripts to be executed despite being forbidden (CVE-2015-7187).
	* 修复了 a crash due to a buffer underflow in libjar (CVE-2015-7194).
	* 修复了 an issue for Android full screen that would potentially allow address spoofing (CVE-2015-7185).
	* 添加了 size checks in canvas manipulations to avoid potential image encoding vulnerabilities like CVE-2015-7189. DiD
	* 修复了 potential information disclosure vulnerabilities through the NTLM authentication mechanism. Insecure NTLM v1 is now disabled by default, and the workstation name is set to WORKSTATION by default (configurable with a preference for environments where identification of workstations is done by actual reported machine name). This avoids issues like CVE-2015-4515.
	* 修复了 a potentially vulnerable crash from a spinning event loop during resize painting. DiD
	* 修复了 several Javascript-based memory safety hazards. DiD


### 25.7.3.1 (Android only!) (2015-10-15)
A small update to the Android version only to fix an issue with the Sync setup still not working properly on Android clients.
### 25.7.3 (2015-10-14)
This is a usability update needed due to the fact that Mozilla has shut down their key exchange (J-PAKE) server along with the old Sync servers. This was unexpected and required us to set up our own key server (testing indicates this works as-expected, but please do report any issues on the forum) - which also required reconfiguration of the browser.
Please note that older versions of the browser will no longer be able to link devices to a sync account using the 12-character code since it requires a Mozilla server no longer present. If you need this functionality, you must update to this version or later.
### 25.7.2 (2015-10-02)
This is a stability update, addressing 2 critical hangs:

	* 修复了 a critical hang caused by recursive reloads that might happen in iframes if its hash 更改了.
	* 修复了 a critical hang caused by lazy-loading of stylesheets through a specific web programming technique as advocated by Google's PageSpeed.

### 25.7.1 (2015-09-28)
This is a security, stability and web-compatibility update. This also marks a security update for the Android version of Pale Moon to keep users of the otherwise currently unmaintained OS 更新了 regarding known security vulnerabilities.

**修复/变化**:

	* Code cleanup: Removed the majority of remaining telemetry code (including the data reporting back-end and health report) to prevent a few issues with partially removed code in earlier versions.
	* 修复了 a crash due to handling of bogus URIs passed to CSS style filters (e.g. whatsapp's web interface).
	* Permitted spec-breaking syntax in Regex character classes, allowing ranges that would be permitted per the grammar rules in the spec but not necessarily following the syntax rules. This impacts a good number of (also higher profile) sites that use invalid ranges in regular expressions (e.g. Cisco's networking academy site, Yahoo Fantasy Football).
	* 修复了 a crash due to the newly introduced WASAPI handling of audio channel mapping that doesn't like actual surround hardware setups (e.g. playing a video with quadraphonic audio on a 4-speaker setup).
	* 修复了 an issue where site-specific dictionary selections would be written to content preferences without the user's action, potentially overwriting or clearing a previously-chosen dictionary.
	* 添加了 support for drag and drop of local files from sources which use text/uri-lists. (Some Linux flavors/file managers)
	* 更新了 libnestegg to the most current version.
	* 修复了 an issue where setting the location to an empty string could cause a reload loop.

**安全修复**:

	* 更改了 the jemalloc poison address to something that is not a NOP-slide. DiD
	* 修复了 a memory safety hazard in ConvertDialogOptions (CVE-2015-4521)
	* 修复了 a buffer overflow/crash hazard in the VertexBufferInterface::reserveVertexSpace function in libGLES in ANGLE (CVE-2015-7179)
	* 修复了 an overflow/crash hazard in the XULContentSinkImpl::AddText function (CVE-2015-7175)
	* 修复了 a stack buffer overread hazard in the ICC v4 profile parser (CVE-2015-4504)
	* 修复了 an HTMLVideoElement Use-After-Free Remote Code Execution 0-day vulnerability (ZDI-CAN-3176) (CVE-2015-4509)
	* 修复了 a potentially exploitable crash in nsXBLService::GetBinding
	* 修复了 a memory safety hazard in nsAttrAndChildArray::GrowBy (CVE-2015-7174)
	* 修复了 a memory safety hazard for callers of nsUnicodeToUTF8::GetMaxLength (CVE-2015-4522)
	* 修复了 a heap buffer overflow/crash hazard caused by invalid WebM headers (CVE-2015-4511)


### 25.7.0 (2015-08-26)
This is a bugfix and maintenance release.

**修复/变化**:

	* Code cleanup: Removed the (otherwise unused) visual event tracer code.
	* Code cleanup: Removed reflow performance tracing code (telemetry).
	* 修复了 a key JavaScript bug where defining properties on an object would wipe the object.
	* This seems to be a common issue with "modern" libraries that use "define" instead of "change" and expecting the other properties on the object to be retained, resulting in "x is undefined" errors all over the place if the object is wiped.
	* This aligns the behavior with ES6's "Validate and apply property descriptor" pseudo-function.
	* 更新了 the SQLite library to 3.8.11.1.
	* 添加了 support for the element.matches() Web API function.
	* 添加了 support for BASE tag parsing in source view. Previously, when viewing the source of a document, clickable links would be incorrect if a base path was specified in the document with this tag.
	* 修复了 an issue with running timers after the computer would have been put to sleep with the browser opened.

**安全修复**:

	* 添加了 protection against potential bugs where our SVG mPositions is out of sync with the characters in the DOM. DiD
	* 修复了 use-after-free vulnerability in XMLHttpRequest::Open() (CVE-2015-4492)
	* 修复了 use-after-free vulnerability in the StyleAnimationValue class (CVE-2015-4488)
	* 修复了 crash or memory corruption in nsTArray (CVE-2015-4489)
	* 修复了 crash or memory corruption in nsTSubstring::ReplacePrep (CVE-2015-4487)
	* 修复了 potential escalation of privileges or crash (out-of-bounds write) via a crafted name in MARs (x64 only) (CVE-2015-4482)
	* 修复了 an issue that would allow man-in-the-middle attackers to bypass a mixed-content protection mechanism via a feed: URL in a POST request. (CVE-2015-4483)

### 25.6.0 (2015-07-27)
This release addresses some security issues and a range of usability improvements to the browser.

**修复/变化**:

	* Canvas anti-fingerprinting option: Pale Moon now includes the option to make canvas fingerprinting much more difficult. By setting the about:config preference canvas.poisondata to true, any data read back from canvas surfaces will be "poisoned" with humanly-imperceptible data changes. By default this is off, because it has a large performance impact on the routines reading this data.
	* 添加了 a feature to allow icon fonts to be used even when users disallow the use of document-specified fonts. This should retain full navigation for icon-font heavy websites (no more dreaded "boxes" with hex codes) when custom text fonts are disabled.
	* 添加了 a feature to prevent screen savers from kicking in when playing full-screen HTML5 video. This is currently not yet operational on Linux because of stability issues we've run into on that OS, but Windows should properly benefit from this change.
	* The "autocomplete=off" parameter for signon forms is now completely ignored by default, to keep the user in control of their browser's behavior and allowing credentials to be saved if wished. If you prefer the previous behavior, allowing a website to determine whether autocomplete should be allowed or not, then change the about:config preference signon.ignoreAutocomplete to false.
	* Reinstated the packaging of pre-compiled scripts in the browser. Hopefully this will fix the reports by some users who found that initial start-up after installation/upgrade of the browser was unacceptably slow. Unfortunately this means a slightly larger download/install size as a trade-off.
	* 添加了 the option to use Chrome://../skin/ overrides, in effect allowing the use of "Icon themes"; toolbar icon replacements to customize your browser icons without the need for any CSS or full-blown theming.
	* 添加了 a count for the number of matches in the find bar. it will now list the total number of matches found, and which match is the currently highlighted one.
	* 修复了 the issue where highlighted words after finding and highlighting them all in a page would remain highlighted when closing the find bar.
	* 添加了 support for CSP 'nonce' keywords (CSP 1.1/2.0). Please note that this is still experimental and may not work 100% as-expected. Please report any bugs you may find.
	* Aligned CSP more with the spec in terms of reporting and case-sensitivity of matches, and made it more app-friendly.
	* 添加了 -moz-os-version selectors for @media CSS queries to simplify theming on different operating systems (esp. Windows).
	* 更新了 and 改进了 several languages for the Status Bar code, and 添加了 Slovenian.
	* 修复了 an issue in the internal updater window not showing proper language strings.
	* 修复了 an issue where the unexpected use of "backface-visibility" on non-3D transformed elements (like the body) would break positioned elements on web pages.
	* 修复了 text positioning in the combobox display area when a non-default height is set for the combobox.
	* 修复了 a crash caused by bad Opus audio encoding in media files.
	* 修复了 a crash when trying to measure memory in about:memory while playing video.
	* 修复了 a rare crash in sLayersAccelerationPrefsInitialized
	* 修复了 miscellaneous other crashes.
	* 修复了 a DNS prefetching issue for the people using this feature.
	* 修复了 an issue with single-word searches from the address bar when a proxy is in use.
	* 修复了 a number of build issues on Linux when using system libs.
	* 添加了 support for link-time optimization on newer Linux compilers.
	* Removed more telemetry code (不断进行 project!).

**安全修复**:

	* 修复了 a memory safety bug due to a bad test in nsZipArchive.cpp (CVE-2015-2735).
	* 修复了 a memory safety bug in nsZipArchive::BuildFileList (CVE-2015-2736).
	* 修复了 a memory safety bug caused by an overflow in nsXMLHttpRequest::AppendToResponseText (CVE-2015-2740).
	* 修复了 a Use After Free in CanonicalizeXPCOMParticipant (CVE-2015-2722).
	* 修复了 off-main-thread nsIPrincipal use of various consumers in the tree (only grab the principal when needed).
	* 修复了 an issue where an IPDL message was sent off the main thread.
	* 修复了 a potentially exploitable TCPSocket crash due to a race condition.

### 25.5.0 (2015-06-10)
This is an important maintenance update with mostly under-the-hood changes.

**修复/变化**:

	* Logjam fix: Refuse DHE keys with less than 1024 key bits
	* Search plugin updates to re-enable Google suggestions and reduce tracking (Squarefractal)
	* Allow plugin-specific (.dll based) OOPP overrides also for npswf. This will not be used for the "master switch" for OOPP and Flash will still be in the plugin container, unless a specific dom.ipc.plugins.enabled.npswf*.dll boolean is set to override.
	* 修复了 a crash during WebGL Conformance Tests for undefined indices (Toady)
	* HSTS preload list updates (Squarefractal)
	* Status bar locale addition: cs
	* Implemented a fix for the toolkit update service so that the same version as the current application will not be offered as a valid update (Tobin)
	* Reorganized the AppMenu (give equal ease for windowed and tabbed browsing, deprioritize Sync)
	* Disabled the Sync promo box in doorhangers.
	* 更新了 libpng to version 1.5.22
	* 修复了 support for builds using newer freetype on Linux. (Axiomatic)
	* 修复了 --with-system-pixman builds. (Isaac Dunham)
	* 更新了 SQLite to version 3.8.10.1
	* 更改了 the after-upgrade page loaded to the release notes instead of the home page.
	* (and hoping people actually do take a moment to read them, preventing unnecessary support requests)
	* 修复了 navigator.geolocation - should never be null, to properly adhere to the specification (Travis)
	* Moved paintlock event delay to greprefs, and adjusted it for 2015's heavier sites
	* 修复了 the about dialog scripting for pre-release builds (includes build date now as-intended and no longer errors the script)
	* Reorganized how pushed floats are handled in layout flow
	* Implemented a change to run the updater from the install directory instead of copying it.
	* 修复了 transparency of the Pale Moon document icon for 256x256
	* 更新了 padlock code:
	* - 添加了 mixed-mode shading, and reorganized shading pref values more logically
	* (0=off, 1=secure only, 2=secure+mixed, 3=all)
	* - Cleaned up CSS
	* - Cleaned up padlock logic a little
	* Hard-coded internal UA sniffing values for the extension legacy of devtools
	* 更新 NSPR 为 4.10.8
	* 更新了 the NSS security lib to 3.19-RTM + re-worked Pale Moon changes
	* Bumped the built-in site-specific UA compat mode overrides to v38
	* 修复了 a compressed-cache crash due to losing our cache entry while finishing up compression.
	* 更新了 and patched libcubeb, the main media sound library, to fix a number of audio issues (e.g. when switching output device) and audio-related crashes
	* 添加了 the option to load modules into a named scope (see issue #88)
	* Removed quick access keys for buttons on the updater window (since it may pop up unannounced when people are typing, causing them to make unintended choices)
	* 更新了 jemalloc and mozjemalloc memory allocator libraries to improve performance
	* Removed implicit access to a whole range of internally-used interfaces and classes that page content has no business calling anyway
	* 添加了 a preference for always preferring a certain dictionary language.
	* To use this, create a new preference spellchecker.dictionary.override (string) and set it to your language code.

More information about changes in this version that would be important for extension developers and web programmers can be found here.

**安全修复**:

	* Fixes for miscellaneous memory safety hazards (relevant and applicable fixes from CVE-2015-2708 and CVE-2015-2709)
	* DiD (defense-in-depth) fix to prevent potential overflows in CSS restyling
	* Fix for updater hijacking (CVE-2015-2720)
	* Fix to prevent potential disclosure of sensitive information in Android logs (CVE-2015-2714)
	* Fix for a buffer overflow in the XML parser (CVE-2015-2716)
	* Fix for a potentially exploitable crash in DNS handling

### 25.4.1 (2015-05-10)
This is a small but important update to the previous major release to address some critical issues:

	* 修复了 loss of the browser's disk cache on startup due to incorrect corruption detection logic
	* 修复了 a browser crash on some HTML5 games

### 25.4.0 (2015-05-08)
IMPORTANT: If you use a language pack, make sure to update it to the latest version! We do have automatic updates enabled for language packs but please double-check that the version matches. If you are using an older language pack with this version of the browser, some dialog boxes may come up blank.

This is a major update - too much has 更改了 for this little blurb to do it justice so please see below for the most important **变化/修复** in this release:

**修复/变化**:

	* 更新了 SQLite from 3.7.17 to v3.8.8.3, improving history/bookmark/etc. performance by up to 50% depending on operation
	* 添加了 a new "mixed-mode" state for HTTPS connections. Clarified mixed-mode connections with a mixed-mode padlock and better tooltips.
	* 添加了 a conditional partial shading to the URL bar and made it default (shading only on secure sites, no red shading at all by default).
	* Dev: 修复了 file system mode flags for *nix systems, to make executable files like scripts actually flagged as executable
	* 添加了 native IPv6 lookups to NSPR to solve IPv6-only and dual-stack setups in some situations
	* 添加了 a pref to control the unloading of idle plugins from memory and lowered the default "idle" time to 60 seconds before plugins are unloaded
	* 修复了 version strings for e.g. flash on Linux being displayed with commas instead of periods - this should also fix the incorrect "your plugin is vulnerable" message while being on the latest version
	* Windows: Set the double-click/Ctrl+arrow word selection to not eat the space (only select the actual word)
	* Android: DNS fix for VPN connections, preventing the "server not found" issues people have been reporting for certain VPN providers on mobile
	* 更新了 a number of trusted root certificates, and distrusted the CNNIC root certificate by popular demand
	* Linux: 解决了 the slice memory allocator not being properly disabled on later GLib versions
	* Android: 更新了 the random number generator handling on later versions of Android
	* 添加了 fix to prevent spurious re-paints with plugins (performance/UX improvement)
	* Removed the plugin check link from the Addons Manager, since it's no longer reliable and not officially available for browsers except Mozilla Firefox. (Bonus: no user profiling/tracking through optimizely!)
	* Optimized the NSS callback for secure connections
	* 更新了 the domains that are whitelisted for installation of extensions/themes/personas, streamlining the use of addons.palemoon.org
	* 添加了 personas support to titlebar text (adopt the lightweight theme's coloring/shading) in custom titlebar mode (Pale Moon appmenu/button)
	* 添加了 display of HTTPS protocol (SSL/TLS) to the page info window (thanks Travis!)
	* 改进了 certificate display: Removed MD5 and 添加了 SHA256 fingerprint, and made them selectable/copyable
	* 更新了 classification of secure connections: Classify any encryption with less than 128 bits or including RC4 (if manually enabled, see previous version notes) as weak.
	* Dev: 添加了 availability of the full ciphersuite string for use in extensions to the nsISSLStatus interface (nsISSLStatus.cipherSuite)
	* 添加了 MAKE_UNLINKABLE to the about: page redirector and 添加了 that as default for the reader mode on Android
	* Removed the compilation and inclusion of a one-time-use pre-compiled startup cache in omni.ja, reducing overall application size significantly and avoiding a number of quirks of both the build process and the operation of the browser
	* 修复了 an NVIDIA specific GLX server vendor bug for pixmap depth and fbConfig depth
	* Removed most telemetry code, reducing code complexity and wasted CPU
	* Linux: 添加了 OSS support (mutually exclusive with ALSA): configure with --enable-oss
	* Made DNS caching a lot less aggressive to align the browser's behavior with the dynamic nature of the modern web.
	* Removed Mozilla-specific parameters for searches. Search suggestions should now work again for Google searches
	* 添加了 the option to allow users to use a 修复了 (JSON) file-based geolocation response in favor of a GeoIP service.
	* Dev: Improvements to Clang builds (thanks Axiomatic/BitVapor!). Clang is not currently producing stable builds on Linux, so please use GCC for that operating system.
	* Linux: removed GnomeVFS that's no longer in use
	* 修复了 the "double padlock while loading a secure site" niggle in the UI
	* Dev: 添加了 allowance of using -moz-appearance:none on drop-down lists to hide the arrow button (catering to custom styling of the control)
	* 添加了 some more ES6 math/number functions:
		* Implemented Math.fround(x)
		* Implemented Number.isSafeInteger(x)
		* Implemented Math.clz32(x)

**安全修复**:

	* 修复了 several memory safety hazards (UAF/DF/UU); applicable bugs covered by CVE-2015-0814 and CVE-2015-0815
	* 修复了 CVE-2015-0811 [qcms] heap info leak
	* 修复了 CVE-2015-0810 clickjacking attacks via a Flash object in conjunction with DIV elements
	* 修复了 CVE-2015-0801 a variant of CVE-2015-0818
	* 修复了 CVE-2015-0800 improve randomness of DNS resolver queries on Android
	* 修复了 CVE-2015-0798 access to privileged URLs through about: redirector

### 25.3.2 (2015-04-25)
This release is an emergency update to fix crashes that started occurring because of Mozilla improperly signing the extensions and extension updates as offered through the Firefox Add-ons site addons.mozilla.org. Any improperly signed extension would not be able to be installed, and would immediately crash the browser.

No other changes were made in this release - this is a bugfix for this particular issue only.
### 25.3.1 (2015-03-25)
This is a security update to the browser to address a critical vulnerability found in the pwn2own contest. Only one vulnerability found in this contest applies to Pale Moon, which has been addressed in this update.

**修复/变化**:

	* 修复了 security vulnerability CVE-2015-0818. This vulnerability would allow remote attackers to bypass the Same Origin Policy and execute arbitrary JavaScript code with chrome privileges via vectors involving SVG hash navigation.
	* 修复了 IPv6 DNS resolution regression in some less common cases.

### 25.3.0 (2015-03-13)
This is an important update to improve features and performance, as well as address important security issues.

**修复/变化**:

	* Overhauled WebGL. It now properly supports depth textures, shadow mapping and glow shaders.
	* Note that older operating systems or older/embedded video processors may be limited in their support of these features.
	* 更新了 the ANGLE library to a much more current version.
	* Removed the crash reporter code completely to improve overall browser responsiveness and operation.
	* Please note that a necessary victim of this has been the in-browser (devtools) SPS profiler because of its reliance on crash reporter data-gathering tools.
	* Removed the Mozilla Plugin Finder Service (no longer in use @Mozilla).
	* Android: removed the Mozilla "product announcements" service.
	* Re-添加了 control of the number of concurrent tabs to be restored from a session with browser.sessionstore.max_concurrent_tabs (accepted values 1-10)
	* Significantly 改进了 performance and accuracy of date/time/timer handling.
	* Significantly 改进了 performance of the creation of DOM elements with plain text content.
	* 添加了 several significant performance optimizations for arrays and strings in javascript.
	* 添加了 several code performance optimizations and bugfixes in SVG, the presentation shell, SCTP, style gradients and CSS parsing routines. (Thanks, Axiomatic!)
	* 添加了 an "Open link in current tab" context menu entry on links for UI consistency.
	* 更新了 styling of the browser with personas (lightweight themes) once more to improve display in tabs-on-top mode, improve overall legibility of tab text, and display of inverted close buttons on some controls on dark personas.
	* 添加了 a special case check for the Flash plugin version check on Linux failing due to commas instead of periods in the version string.
	* 添加了 Windows 10 compatibility in executable manifests.
	* Android: 修复了 a crash on GL canvas surfaces.
	* 修复了 incorrect Sync "howto" instruction links from the Sync dialogs.
	* 修复了 the color of selected tabs in Linux when personas (lightweight themes) are in use that do not match the overall tone of the OS system theme.
	* 修复了 a bug where a variable in parentheses would abort Javascript parsing.
	* 修复了 a bug where the address bar would incorrectly be cleared.
	* 修复了 padding issues for dropdown lists.
	* 修复了 DNS lookups so proper record types are requested for IPv4 and IPv6.

**安全修复**:

	* Disabled all RC4-based encryption ciphers by default. [More info]
	* 修复了 several miscellaneous memory safety hazards.
	* (applicable bugs related to CVE-2015-0835 and CVE-2015-0836)
	* 修复了 loading of locally stored DLL files through the internal updater. (CVE-2015-0833)
	* 修复了 a potential crash point in IndexedDB. (CVE-2015-0831) DiD
	* 修复了 a double-free situation when using non-default memory allocators and a 0-length XHR. (CVE-2015-0828)
	* Note: production builds of Pale Moon were never vulnerable.
	* 修复了 a crash using DrawTarget in the Cairo graphics library. (CVE-2015-0824)
	* 修复了 potential reading of local files through manipulation of form autocomplete. (CVE-2015-0822)
	* 修复了 a potential PNG heap-overflow crash. DiD
	* Followed up on research regarding CVE-2014-8639 (see 25.2) and made cookie handling through proxies more restrictive again.

DiD 这意味着这个修复是 "Defense-in-Depth"(深度防御): 这是一个并非应用于 Pale Moon 中的(潜在的)活跃的可利用漏洞， 而是用于防止相同的代码在周边的代码发生变化而暴露问题从而导致未来的漏洞的修复。
### 25.2.1 (2015-01-27)
This is a small update to address cookie handling through proxies causing issues for some authenticating proxies in corporate environments.
### 25.2.0 (2015-01-15)
This is an important update after rapid development on the back-end to extend browser capabilities and implement some ES6 draft functions for web programmers, as well as provide some important crashfixes, bugfixes and security updates.

**修复/变化**:

	* ES6: 添加了 the following functions:
		* Array.prototype.find and Array.prototype.findIndex
		* IsConstructor(arg)
		* Array.of(items...)
		* Number.parseInt and Number.parseFloat
		* Advanced math functions: hyperbolic sin/cos/tan/asin/acos/atan, hypotenuse, cube root, expm1, log1p, log10, log2, sign and trunc
		* Map.prototype.forEach and Set.prototype.forEach
	* ES6: 添加了 the following number constants: EPSILON, MIN_SAFE_INTEGER and MAX_SAFE_INTEGER
	* ES6: 添加了 the use of binary and octal numeric literals (&b... and &o...)
	* ES6: 更新了 behavior of accessing indexed values in accordance with the spec.
	* CSS: 添加了 overflow-clip-box:content-box|padding-box
	* DOM: 添加了 table.createTBody() function
	* 添加了 a clearer alltabs button for dark personas.
	* 添加了 a development tools toggle hotkey (F12)
	* 添加了 a preference prompts.tab_modal.focusSwitch to enable or disable tab switching when a modal dialog (e.g. javascript confirmation) is presented in a page.
	* IonMonkey on Android: 修复了 the implementation of AbsI.
	* IonMonkey: 修复了 a bug where actively used objects were discarded.
	* 修复了 register initialization to prevent incorrect detection of SIMD instructions on some CPUs.
	* Optimized some loops in the spell checker to increase performance.
	* Simplified cache handling, 更新了 cache parameters to better reflect current web use, and enabled automatic cache sizing by default.
	* Adjusted memory cache sizing to better reflect capacities of current hardware.
	* 更新了 UserAgent override workarounds for Netflix and FaceBook to fix some site issues.
	* Aligned programmatic access to geolocation with the spec.
	* 修复了 a crash when being fed a data file (XML) with too deeply nested tags.
	* 修复了 a crash in HTML5/WebAudio that affected some games.
	* 修复了 a crash when programmatically collapsing elements.
	* 修复了 a few non-breaking bugs related to e10s code.
	* 修复了 text input/padding issues.
	* 更新了 surround downmixing code for Vorbis.
	* 改进了 tolerance in WebAudio for loading multichannel audio files.
	* Android: 修复了 an issue with Flash, it should now run on more devices.
	* 更新了 the DDG search plugin to make the actual query be the last parameter in the address bar for easy editing after a search has been performed.
	* Removed some unused update channel code.
	* 更新了 branding to more clearly indicate Pale Moon's trademark.
	* 更新了 some licensing texts in-browser to properly reflect used code and rights.

**安全/隐私修复**:

	* 添加了 a preference network.stricttransportsecurity.enabled to enable or disable the use of HSTS (HTTP Strict Transport Security), allowing users to choose between privacy and security in this matter. (hidden pref)
	* 修复了 CVE-2014-1589 by whitelisting XBL bindings that may be applied to untrusted content.
	* Important: extension developers should read this related thread.
	* 修复了 CVE-2014-1593.
	* Mac: 修复了 CVE-2014-1595.
	* 修复了 CVE-2014-8639 by adjusting cookie handling through proxies.
	* 修复了 CVE-2014-8636.
	* 修复了 several memory safety hazards that do not have CVE numbers.

### 25.1.1 (2014-11-28) Android only!
This point release for Android only addresses critical browser issues (crash on startup) when trying to run Pale Moon on Android 5.0 (AKA Android-L or Lollipop). No other changes involved in this release.
### 25.1.0 (2014-11-14)
This is an important update after rapid development on the back-end to keep pace with the current changes on the web and improve compatibility with websites.

**修复/变化**:

	* New feature: multi-line flexbox support.
	* Pale Moon now supports more advanced multi-line and multi-column flex elements. This will allow websites to use these elements for easier responsive design of web pages and ordering/layout of multiple elements. This has been on Pale Moon's to-do list for a while but was rather complex to tackle, hence the delay in implementation. This should address layout issues on several recently-更新了 websites (e.g. the MSN home page).
	* New feature: 添加了 support for collapsed flex element items.
	* Enhanced feature: Content Security Policy (CSP)
	* Pale Moon now fully supports the CSP 1.0 specification allowing websites to set restrictions on content to prevent XSS (Cross-site scripting) attacks. Previously, the implementation in Pale Moon was partial, and did not support a number of features, resulting in some websites not rendering properly because Pale Moon was being too strict in enforcing the policy. This should address issues on websites enforcing CSP (e.g. the Dropbox web interface and FaceBook galleries).
	* New feature: 添加了 support for iframes with inline content.
	* 更新了 the Firefox Compatibility mode version to 31.9.
	* With the improvements in rendering and overall feature set, the Firefox Compatibility mode (as presented in the UserAgent string) has been bumped to prevent websites from complaining about "using a too old/unsupported version of Firefox" (e.g. Google websites).
	* Pale Moon no longer builds the so-called "media navigator" by default.
	* This module provides access to the user's webcam and microphone. Although it can be used for other purposes, in practice this is only used for WebRTC and, in fact, its support (GetUserMedia) is often mistaken for actually supporting WebRTC in a browser (causing errors since Pale Moon does not support WebRTC). No longer including these features reduces input complexity and overhead for a feature not actively used. This also circumvents privacy concerns/confusion like CVE-2014-1586.
	* 改进了 tab handling on lightweight themes (personas) some more to enhance contrast on certain themes and to make the tab hover effect slightly more distinct.
	* 修复了 oversized/blocky menu arrows on Windows 8.1 in HiDPI mode.
	* 修复了 incorrect operating system being passed on to addons.mozilla.org.
	* 修复了 an error being thrown in the error console/web console when opening a new window.
	* Removed the NVidia 3D Vision auxiliary utility library.
	* This library has been the likely cause for 数个崩溃。on NVidia cards, and is completely unnecessary for Pale Moon.
	* Made the installer less aggressive for file type associations, to prevent "stealing" of globally associated file types.
	* Android: 改进了 restoring of session tabs.
	* Android: 添加了 an option to automatically restore tabs.
	* An important thing to note with this new option is the following: with the option enabled, Pale Moon will now automatically restore tabs you had open previously when the app gets suspended (pushed out of memory by other apps, closed by swipe, etc.). The "quit" main menu option, however, completely shuts down your session, unloads Pale Moon from active memory, and tabs will not be automatically restored when you launch Pale Moon again. This is by design. To restore tabs in that situation, use the link from the home screen.
	* 修复了 memory security hazards CVE-2014-1574 and CVE-2014-1575 security fix
	* 修复了 CVE-2014-1581. security fix
	* 修复了 bug 1069584: Bail if a cairo surface is in an invalid state. security fix
	* Made sure to initialize surfaces for draw targets. security fix
	* 修复了 CVE-2014-1594: Use AsContainerLayer() in order to avoid a bad cast. security fix
	* 修复了 several problems in the HTML parser. security fix
	* 改进了 security of XHR by filtering out types of requests that can potentially be abused. security fix

### 25.0.2 (2014-10-24)
This is a small update to address a number of teething problems with the new milestone release.

**修复/变化**:

	* 添加了 a "Firefox compatibility mode" selection in Options -> Advanced.
	* This mode is enabled by default (reluctantly so), because too many websites (including some very big players who, themselves, promote an Open Web...) still use very poor browser detection methods based on arbitrary User Agent string comparisons, not catering to alternative browsers, and the resulting user experience being poor (being presented with mobile site layouts, broken pages, or even being flat-out refused service because someone exercises freedom of choice for web browser used). This should alleviate most, if not all, issues with browser-discriminating websites.
	* 改进了 active tab display on particularly dark personas.
	* People using "black" personas/lightweight themes should now have a lot less difficulty distinguishing the active tab.
	* Disabled SSL 3.0 by default (to put a muzzle on the POODLE).
	* Please note that this may cause issues with some poorly configured web servers (usually ones with a hopelessly broken security setup that do not support TLS 1.2 or secure (re)negotiation of the protocol).
	* 修复了 add-on update issue (that was preventing update checking through addons.palemoon.org).
	* 修复了 the redundant redundancy in asking redundantly if the browser would be allowed to ask to install an extension when not on addons.mozilla.org.
	* 修复了 the internal UA-sniffing insanity that broke devtools in a few different and colorful ways.

### 25.0.1 (2014-10-15)
This is a small update to address an important Jetpack extension compatibility issue and includes a number of **安全修复**.

**修复/变化**:

	* Update of the add-on SDK to add missing "Pale Moon" engine entries to lists. This should fix extension compatibility issues for jetpack extensions that otherwise already work with the new GUID.
	* About box release notes link corrected
	* Fix for VP9 decoder vulnerability security fix
	* Fix for direct access to raw connection sockets in http security fix
	* Fix for unsafe conversion to JSON of data through the alarm dom element security fix
	* Update of NSS to 3.16.2.2-RTM security fix

### 25.0.0 (2014-10-10)
Pale Moon 25.0 is a new major release with a large number of changes. A summary of the most important changes can be found here; for more details about this release, please check the forum.

**修复/变化**:

	* Change of the browser's GUID (Globally Unique Identifier) to properly differentiate from Firefox.
	* The new GUID is {8de7fcbb-c55c-4fbe-bfc5-fc555c87dbc4}.
	* Allow extensions with both Pale Moon GUID and Firefox GUID to be installed natively (dual-ID system).
	* Pale Moon GUID blocks will have preference over Firefox (compatibility) blocks.
	* Disconnect of Pale Moon's "Firefox compatibility" version from Pale Moon's application version to maintain Firefox 24.* extension compatibility regardless of Pale Moon version.
	* Disable Firefox Compatibility mode by default.
	* This means Pale Moon will no longer have a Firefox/xx.xx indicator in its UserAgent string.
	* This may impact some websites that check browsers by UserAgent and possibly warn, complain or block you. You should contact the site's owners and request support for Pale Moon. Pale Moon will allow you to override the UserAgent on a per-site basis if you absolutely must visit the site and they absolutely won't cater to your freedom of browser choice.
	* Use the alternative sync implementation on a new server.
	* Current Pale Moon sync accounts cannot be ported over, so you will have to create a new account when updating to v25.
	* The previous server implementation has already been shut down due to continued issues, and will be retired on the very short term to free up infrastructure and reduce expenses. The alternative sync implementation is Sync 1.1 compatible, like before.
	* Stop building the WebApp runtime by default.
	* The use of "Web Applications" started from the command-line is such a niche feature that it has no business being in Pale Moon's main-line builds.
	* If you need the WebApp runtime for your specific organization and want to use Pale Moon, you can build Pale Moon from source with the feature enabled.
	* Stop supporting Windows XP. As mentioned a few times before, Pale Moon's support for Windows XP (and any other NT 5.x based operating system) has now ended. An exception to this is the specialized Atom build because of limited operating system availability on netbooks and the like. More details on the dedicated page for this change.
	* By default, do not sync add-ons.
	* Syncing between different devices will likely not want you to sync the add-ons in use. There's a reason you're using different devices, after all.
	* Un-prefix CSS box-sizing.
	* You can now use box-sizing:border-box, box-sizing:padding-box and box-sizing:content-box to switch box-sizing mode on elements using CSS.
	* Implement image-orientation in CSS.
	* You can now use image-orientation: {angle} [flip] in CSS to rotate images in 90 degree steps and optionally flip them.
	* Improve bookmark menu item-dragging.
	* Dragging bookmarks in the bookmarks menu is now more convenient (allow diagonal dragging, prevent tooltips from interfering, etc.).
	* (Fixes bugs 225434, 419911 and 555474)
	* Move the option to "use the classic downloads window" from status bar preferences to the main options window.
	* This way, it's easier for people to find and it's in a much more logical place. The classic downloads window will not go away any time soon in Pale Moon.
	* Update branding images for official/unofficial logo, and some about: pages.
	* Add a new type of "blank new tab" page with logo-styling.
	* This logo page will be the default setting (instead of about:blank).
	* Add Opus audio to WebM.
	* Add VP9 codec to WebM on both desktop and Android/ARM.
	* Allow absolute-in-relative positioning in table and CSS table-cell elements.
	* Allow the user to override the use of accessibility colors in the browser with browser.display.ignore_accessibility_theme
	* Improve the display of tabs when lightweight themes (personas) are in use for both light and dark themes.
	* Enable cache compression by default to more efficiently use disk cache.
	* When shutting down the browser while you still have downloads in progress, Pale Moon will now by default warn you that the downloads will be cancelled.
	* 添加了 language packs for Acholi, Assamese, Kashubian, Pulaar Fulfulde, Armenian, Khmer, Ligure, Mongolian, and Swahili.

Bug/regression fixes:

	* Prevent error in removeobserver() for the padlock code when closing a window
	* Hang fix: Release XPCOM timer immediately after firing to prevent a race condition. (CVE-2014-1553)
	* Android & any ARM processor: Always use integers for audio instead of floats.
	* Properly apply the use of high contrast themes on Windows 8/8.1
	* Prevent the accumulation of hidden about:blank windows in some situations.
	* Android: prevent deadlocks due to invalidations when using plugins (Flash)
	* Re-enable high-quality downscaling of particularly large images (selective HQ downscaling) and improve fast image scaling method (use Lanczos instead of Hamming)
	* Hang/DoS fix: Avoid uninterruptable infinite loops in IonMonkey in some situations. (CVE-2014-1548)
	* Android: improve the handling of zooming to input fields

**安全修复**:

	* Properly derive/insert the host of a URL
	* Avoid negative audio ratios (can lead to crashes) (CVE-2014-1565)
	* Avoid some root hazards in the style parser
	* Add is-object check to IonBuilder::makeCallHelper (CVE-2014-1562)
	* Clear the jumplist icon cache when history is cleared (隐私修复)
	* Crash fix on Windows (JS JIT) (CVE-2014-1554)
	* Prevent buffer overrun in text directionality component (CVE-2014-1567)
	* Update NSS to 3.16.2.1-RTM (CVE-2014-1568)

Release notes for version 24 releases
### 24.7.2 (2014-09-11)
This is a small bugfix and security update.

**修复/变化**:

	* Use (i) icon for error console informational messages instead of (?)
	* Properly derive and insert the host of a URL security fix
	* Avoid negative audio ratios. security fix
	* Release XPCOM timer immediately after firing to prevent a race condition.
	* Add is-object check to IonBuilder::makeCallHelper. security fix

### 24.7.1 (2014-08-06)
This is a bugfix release for some outstanding issues in 24.7.0.

**修复/变化**:

	* 修复了 a text rendering issue with the new back-end on overdraw layers when hardware acceleration is in use on Windows. This may also solve some additional small issues in the user interface that weren't present before 24.7.0.
	* 修复了 the use of Google Maps.
	* If you previously used the workaround in 24.7, then please remove the user-set preference (right-click -> reset).

### 24.7.0 (2014-07-29)
This is a large update to address a good number of different things across the board. If you want more details about these changes, check the more detailed announcement on the forum.

**修复/变化**:

	* 修复了 some performance issues with the new rendering engine on Windows. Rendering should be faster for all objects on hardware-accelerated layers now.
	* Font rendering on Direct2D will no longer fall back to greyscale in some situations, preserving ClearType.
	* CSS outlines will now properly outline the object, and not the overflow area (e.g. box shadow).
	* The delay for hiding the default status has been increased from 10 to 30 seconds to keep it on screen sufficiently long but not permanently.
	* Queries for "can play type" on WebM videos now get an HTML5-compliant response ("maybe" instead of "yes" as per the specification when a codec is not included in the request).
	* Pale Moon's gecko rendering engine and Firefox compatibility version now properly follows the minor version of Pale Moon again instead of always returning .0 - this should help UA sniffing websites to more easily detect Pale Moon or adapt to further-developed gecko 24 versions.
	* When using dark/black personas (lightweight themes), the tab close buttons would be almost invisible. They have been lightened a little to make them clearer.
	* Linux: the click behavior on the address bar has been unified with that on Windows, aiming for current-day desktop-clipboard use (select-when-clicked). This is configurable with a preference.
	* "In-content" preferences (preferences displayed in a tab instead of the normal dialog box) has been removed because of redundancy and incompleteness.
	* Checking for updates from the about box now always puts the user in control and never downloads anything directly from the about box. It will pop up the larger update window when an update is found.
	* Google SafeBrowsing, which is defunct, has been removed from the browser. 隐私修复
	* Made the building of the Web Developer tools optional when compiling Pale Moon through --disable-devtools.
	* The Atom-optimized version no longer ships with the Web Developer tools to slim down the browser for limited platforms where these tools are considered generally unneeded.
	* 修复了 domain highlighting in the address bar. It should no longer randomly lose this formatting when switching tabs or otherwise updating the browser UI.
	* 修复了 missing click-to-play overlay on some zoom levels for plugins embedded in an iframe.
	* 修复了 large delays in print enumeration on Windows, especially when printing to file: ports.
	* 更新了 the list of known domain suffixes.
	* 更新了 site-specific user-agent strings to prevent incorrect complaints from websites (google.com, aol.com, etc.) that use poor detection scripts.
	* 添加了 granular referer control. See the release announcement on the forum for more details on how to use this.
	* 添加了 gr locale to the status bar options.
	* Disabled HQ image downscaling. This is a workaround for the broken Mozilla HQ downscaling back-end causing constant invalidations and redrawing if 2 downscaled images with the same source were in view.
	* 更新了 the NSS library to 3.16.2 RTM to address a few critical SSL issues. security fix
	* There was a possibility to lose the source frame for raster images if images had to be discarded in low-memory situations. This has been 修复了. security fix
	* Made refcounting logic around PostTimerEvent more explicit. security fix
	* Prevented an invalid pointer state in docloader. security fix
	* 添加了 proper refcounting of font faces. security fix
	* Android: lots of branding updates to make it more release-ready.
	* Android: explicitly set the Pale Moon Sync server in preferences.
	* Android: IonMonkey (ARM): guarded against branches being out of range and bail out if so. security fix
	* Android: enabled Firefox compatibility mode on Android to allow the installation of extensions from AMO.
	* Android: 添加了 a "Quit" option to the app menu to properly immediately close the browser.
	* Android: IonMonkey (ARM): prevented a performance issue due to clobbering the primary scratch register.
	* Android: enabled mobile-specific optimizations to increase performance on mobile devices.
	* Android: enabled AES-128 and AES-256 in addition to RC4 for Sync.

### 24.6.2 (2014-06-16)
A point release to address some further outstanding issues with the overhauled rendering engine.

**修复/变化**:

	* Automate rendering back-end selection and use cairo as appropriate.
	* This should fix start-up problems on all types of graphics cards regardless of vendor.
	* Fix font subpixel rendering in menus when on cairo backend (D2D off)
	* Cairo: Prevent falling back to padding when not strictly needed.
	* Performance regression fix if D2D isn't used.
	* Azure: Use correct device offsets.
	* Prevent crashes due to the allocation of source surfaces to errored surfaces
	* This prevents some miscellaneous browser crashes occurring with cairo on azure.

### 24.6.1 (2014-06-08)
A quick point release update mainly to address startup crashes.

**修复/变化**:

	* Update to address startup crashes if users previously 更改了 the setting for Azure for Content
	* Update for texture handling to restore GDI compatibility (should fix some graphics glitches)
	* Fix to handle invalid PDF plugin overlay state
	* Misc. additional **安全修复** ported over from Firefox (bug #s 991981, 995679, 999651, 1009952, 1011007)

### 24.6.0 (2014-06-06)
This is a major update including a rendering engine overhaul and a number of very important fixes. For details about the changes, please see the detailed changelog on the forum.

**修复/变化**:

	* Allow animated personas (lightweight themes)! You will need to set a preference for this.
	* Fix regularly occurring browser crashes with hardware acceleration enabled on DirectWrite 6.2/6.3 (Win 7 with Platform Update, Windows 8/8.1).
	* Fix font rendering issues on DirectWrite 6.2/6.3, especially on legacy AMD hardware. (KB2670838 issues).
	* Fix Windows version detection issues on Windows 8.1.
	* Shuffle reported plugin installation order to confuse trackers.
	* Clean up jumplist icons so they no longer pile up on disk on some systems (also a privacy concern).
	* Change the sync server to a (new) Pale Moon sync server.
	* Update the status bar code: Full-screen HTML5 video will no longer have status pop-ups overlaid.
	* Add code to selectively ignore "autocomplete=off" on signon input fields.
	* Linux: reduce gstreamer CPU overhead.
	* Fix styled HTML buttons to address misaligned button contents (wrong baseline), e.g. gmail account chooser.
	* Fix an old IonMonkey bug resulting in incorrect math results in some cases.
	* Improve the performance of editor initialization.
	* Update the Pale Moon icon for better display on lower color depths.
	**媒体**: use a simpler way to discard superfluous audio packets.

**安全修复**:

	* Bug #994907 - imgDecoderObserver does reference counting on different threads, so should be using thread safe reference counting.
	* Bug #992274 - Tweak an edge case in line number handling.
	* Bug #995603 - Ensure mouse-enter/exit events are sent to plugins as appropriate.
	* Bug #1005552 - Stop binding marquee event handlers + misc related fixes.
	* Bug #1000185 - Fix several issues with SMIL.
	* Bug #978811 - Fix isFakeExitFrame to return true for entry frames.
	* Bug #996715 - IonMonkey: Remove the code that bails when determining if the second instruction in a chunk is a branch.
	* Bug #967354 - Fix incorrect usage of UpdateWebGLErrorAndClearGLError();

In addition, Pale Moon also has a public Git repository now:
https://github.com/MoonchildProductions/Pale-Moon

### 24.5.0 (2014-04-25)
This is a security and bugfix release, to address outstanding known issues and streamline browser identity.

**修复/变化**:

	* Fix plugin doorhanger code for removed-node confusion.
	* Remove Mozilla Corp specific details from search plugins, to clearly indicate the client is Pale Moon, and to make sure searches are not counted by search providers towards any other browser's search totals by mistake.
	* Make sure to set both "warnOnClose" and "warnOnCloseOther" prefs to false when users choose to disable this check in the popup prompt.
	* Update branding: Remove nightly branding altogether - only have unofficial+official,  and fix the broken About dialog branding.
	* Bugfix: Clamp level of WebGL TexImage operations to 32-bits to avoid issues on x64 architectures.
	* Update Linux theme: feed icon
	* Bugfix: Add Firefox Compatibility flag to unofficial branding.
	* Workaround for several prominent websites complaining about an "outdated browser".

**安全修复**:

	* Bug #987003 - Be more careful sandboxing javascript: URLs.
	* Bug #952022 - Add missing detachAsmJSModule.
	* Bug #986843 - Replace AutoHoldZone with AutoCompartmentRooter.
	* Bug #989183 - Check for nsXBLJSClass.
	* Bug #980537 - Only store FakeBackstagePass instances in mThisObjects.
	* Bug #986678 - Fix type check in TryAddTypeBarrierForWrite.
	* Bug #966006 - Fix security issue in DNS resolver.
	* Bug #944353 - Avoid spurious decoding of corrupt images.
	* Bug #969226 - Avoid buffer overflow in corrupt ICC profiles.
	* Bug #991471 - Fix offset when setting host on URL.
	* Bug #993546 - Don't try to malloc-free 0-size memory chunks.
	* Bug #992968 - Avoid OOM problems with JIT code caching

### 24.4.2 (2014-04-02)
A small bugfix release, and implementing OCSP-stapling for SSL connections.

**修复/变化**:

	* 添加了 OCSP-stapling.
	* Removed download status indicator from default set in status bar code to fix erroneous pop-up locations of the downloads panel.
	* 修复了 errors with synchronous OCSP-stapled calls.
	* Reduced the timeout for OCSP requests to 2 seconds unless OCSP is required by the server.
	* 添加了 proper handling of fragment loading (Bug #s 895557&987140). security fix
	* 更新了 status bar localizations: kn-IN and pt-PT.

### 24.4.1 (2014-03-19)
A small security and bugfix release.

**修复/变化**:

	* Bugfix: the new status bar code in 24.4.0 had a bug, preventing the downloads panel/window from opening when clicking on the download status indicator. There may have been a few other, similar small usability bugs in the same code that have now been 修复了.
	* Feature update: Selecting "Warn me when closing multiple tabs" in the Options window will now apply both to closing a window and closing other tabs in the tab bar.
	* Bug #940714 - Add an RAII class to make synchronous raster image decoding safer.
	* Bug #896268 - Use a stateless approach to synchronous image decoding. security fix
	* Bug #982909 - Consistently use inner window when calling OpenJS. security fix
	* Bug #982957 - Fix crash if certain sweeps run out of memory. security fix
	* Bug #982906 - Remove option for security bypass in URI building. security fix
	* Bug #983344 - JavaScript: Simplify typed arrays and fix GC loops. security fix
	* Bug #982974 - Be paranoid about neutering ArrayBuffer objects. security fix

### 24.4.0 (2014-03-10)
This update changes the new title behavior slightly and updates a lot of things under-the-hood.

**修复/变化**:

	* By popular request: the new page title (when using the Pale Moon App button) will now follow the operating system default alignment (in most cases), meaning it will align left on Windows Vista and Windows 7 by default instead of center. If you want to hide the title or align it differently, please see the FAQ section on the forum.
	* 更新了 status bar code to the latest "non-australis" version and license change to MPL 2.0 to bring it in line with the rest of the browser code, making it an integral part of the source tree to streamline building (also for 3rd parties).
	* 更改了 the way Pale Moon handles file and protocol associations. This will prevent interoperability issues if you have both Firefox and Pale Moon installed on the same system. A side effect is that Pale Moon will ask you (once) to make it the default browser again when you install this update, because of the new associations to be made.
	* 更改了 the search default to DuckDuckGo.
	* 添加了 DuckDuckGo logo to about:home.
	* 更改了 some things in the build system, back-end code and build configuration to improve overall performance of the browser.
	* Switched to the use of a more compact browser filesystem layout, improving overall start-up speed.
	* Precompiled script cache in the application, improving overall start-up speed at the expense of some disk space.
	* 添加了 MPS detection for non-windows operating systems (NSPR fallback method) instead of always "1".

Bugfixes ported over:

	* Bug #968461 - Fix imgStatusTracker.h to build with gcc 4.4.
	* Bug #912322 - Make sure document.getAnonymous* is no longer available to web content.
	* Bug #894448 - Move IsChromeOrXBL to xpcpublic.h.

**安全修复**:

	* Bug #963198 - Don't mix up byte-size and array-length.
	* Bug #966311 - Calculate frame size for stereo wave.
	* Bug #958867 - Consistent OwningObject handling in IDBFactory::Create methods.
	* Bug #925747 - Patch file extraction cleanup.
	* Bug #942152 - Fix error handling on NSS I/O layer.
	* Bug #960145 - IonMonkey: Don't ignore OSR-like values when computing phi ranges.
	* Bug #965982 - Clean up client threads before I/O on shutdown.
	* Bug #950604 - Backport of a small typed array bugfix.
	* Bug #967341 - Fix up URI management.
	* Bug #963974 - Null mCurrentCompositeTask after calling Cancel() on it.

### 24.3.2 (2014-02-11)
An update to implement TLS v1.2, implement a few new features and fix some minor bugs.

**修复/变化**:

	* New feature: Implemented the TLS v1.1 (RFC 4346) and TLS v1.2 (RFC 5246) protocols for 改进了 https security.
	* 更改了 the list of supported encryption ciphers and order of preference to provide you with secure, speedy connections wherever possible.
	* New feature: 添加了 CSS background-attachment:local
	* New feature: 添加了 dashed-line stroke support for canvas drawing (set/get/offset)
	* Adjusted geolocation timings to prevent IP bans in testing mode and to give you a slightly faster response to the request.
	* Adjusted the new window title position some more to account for edge cases.
	* 修复了 the installer to use the proper class for checking if Pale Moon is already installed/running.
	**安全修复**: bug #966021 - Fix load_truetype_table in the cairo dwrite font backend.

### 24.3.1 (2014-01-31)
A minor bugfix release to address some issues with new code in 24.3.

**修复/变化**:

	* Fine-tuned the title-bar title text position to work a little better on Windows 8 systems.
	* 修复了 a problem with the classic download manager window not opening and/or downloads not starting when using the classic download manager.
	**安全修复**: Bug 945334 - Fix runnable pointer holding.
	* Merged Linux-specific theme code into the source tree for the pm4linux project.

### 24.3.0 (2014-01-28)
A fairly significant update with feature updates, bugfixes, and **安全修复**.

Changes and bugfixes:

	* New build: Atom-optimized Pale Moon
	* After some thorough testing, the Atom/netbook builds are being released as final. These builds are specifically made for PCs with Intel Atom processors. More information can be found on the Atom builds page.
	* New feature: the title has been brought back to the title bar
	* When using the Application Menu (Pale Moon button), the title bar of the browser window would be blank. Considering this is wasted space, the page title will now be displayed in the title bar again (it's called a title bar for a reason, after all!). Several different styles have been implemented to cater to different OS version layouts.
	* Removal of the services tab in the Add-on Manager
	* It will be visible only if someone actually has a service extension installed (similar to how language packs work)
	* Improvement of UI consistency
	* Removal of illogical selective hiding of the navigation bar and toolbars when in tabs-on-top mode (Add-ons manager, permissions manager, etc.). Browser chrome will now never be hidden.
	* Bugfix: When using the classic downloads window, downloads in private windows were not shown
	* If you use the classic downloads window and would open a Private Browsing (PB) window, there was no easy way to see which downloads were done in the PB window. When checking the downloads, it would open up the (non-PB) classic downloads window which does not have downloads listed from the PB session. This has been 修复了, and PB windows will now open a new tab in the PB window with the downloads from that private session.
	* Bugfix: Geolocation didn't work in Pale Moon
	* This was caused by the Firefox standard geolocation provider (Google Inc.) now requiring an API key to request geolocation coordinates. Only official Mozilla Firefox builds will have working geolocation from Google.
	* Pale Moon has switched provider to IP-API.com to address this issue, with the required re-write of code for the different type of request. More information on the forum.
	* Bugfix: The "More information" link for blocked add-ons didn't work
	* Bugfix: Certain scaled fonts would have malformed letters
	* On Vista and later with hardware acceleration enabled, certain letters of some font families would become malformed and difficult to read because of a Direct2D scaling issue. These fonts should now render sharp and more legibly.
	* Romanian has been 添加了 to the status bar localizations

Bugfixes ported over:

	* Bug #903274 - Have the search bar binding's initialization callback bail out if the binding is destroyed.
	* Bug #951142 - Check for a close method to be present on the binding before invoking it.
	* Bug #908915 - Fix compartment mismatch in shell decompileThis and disassemble functions.
	* Bug #950909 - Forward native aggregation to the root XPCWrappedJS.
	* Bug #937152 - Remove XPCWrappedJS::mMainThread and mMainThreadOnly.
	* Bug #948134 - Fix "value is not defined" in PlacesDBUtils.jsm.
	* Bug #822425 - Expose a few simple compartment assertions in jsfriendapi.
	* Bug #932906 - Observer no longer called when using overlay

**安全修复**:

	* Update of the NSS library to 3.15.4 RTM
	* Bug #936808 - Serialize calls to PK11 routines in SSLServerCertVerification.
	* Bug #945939 - Use the pre-split value when numbering values.
	* Bug #911864 - Fix several XBL issues
	* Bug #921470 - Remove hasFallbackStub_ check in resetMonitorStubChain.
	* Bug #950590 - Use nsRefPtr for gfxFontGroup's reference to the user font set, and support changing it from canvas context.
	* Bug #937697 - Simplify some BoundsCheckRange code.
	* Bug #936056 - Be consistent about the thisobj we pass to getters.
	* Bug #953114 - Fix GetElementIC typed array issue.
	* Bug #937132 - SpiderMonkey: Check for overflows in LifoAlloc.
	* Bug #932162 - Dispatch IndexedDB FileInfo releases to the main thread.
	* Bug #951366 - Use AutoDetectInvalidation for disabled GetElement caches.
	* Bug #950438 - IonMonkey: The intersection of two ranges that both contain NaN is not empty.
	* Bug #950268 - Fix leak in nsCertTree::GetDispInfoAtIndex.
	* Bug #932906 - Exempt Remote XUL from CanCreateWrapper checks.
	* Bug #882933 - Copy treatAsRunOnce bit when cloning scripts, don't clone scripts unnecessarily for arrow lambdas.
	* Bug #901348 - Duplicate symbol errors building --with-intl-api.
	* Bug #925896 - Properly reference session data
	* Bug #943803 - Use monitor instead of mutex locking for raster images
	* Bug #942164 - Use weak references to imgRequest consumers
	* Bug #947592 - Streamline ReportLoadError.

### 24.2.2 (2013-12-11)
Mainly a security update:

	* Implementation of all remaining applicable **安全修复** from Firefox 26.0 that were not implemented yet in previous versions.
	* Update of the Security library (NSS) to 3.15.3.1.
	* Fix of new js zone writes/zone barrier bugs.
	* The Sync configuration allows users to input their own recovery key again. Please note that letting the browser generate its own secure recovery key is still strongly recommended, as this recovery key should be impossible to guess and of sufficient length and complexity to keep your data safely encrypted.

### 24.2.1 (2013-12-04)
A minor bugfix update:

	* Fix for some status bar localizations not working and giving an error.
	* Implementation of an optimized QuickFind routine.
	* Implementation of per-zone user data handling.
	**安全修复** in the JPEG library.
	**安全修复** in web workers.

### 24.2.0 (2013-11-26)
This update implements the following changes:

	* Update of the new-tab routine: When opening a new tab, focus will now only be on the address bar if you open a blank tab or the Quick Dial page, and focus will be on the page content otherwise (Pale Moon start page or custom URL).
	* Compatibility issues between QuickFind/Find-as-you-Type and HTML5 input fields in forms 修复了.
	* New advanced feature: Later versions of the Firefox code will automatically place the browser window fully on a visible portion of the screen. If you prefer having the browser window positioned partially off-screen and want to prevent this automatic resizing and repositioning when starting a new session, create a new boolean preference in about:config called browser.sessionstore.exactPos and set it to true.
	* 更新了 the localization of the status bar code with the following locales: en-GB, es-MX, es-AR, it, pl.
	* Fix for a security issue with script event handlers.

### 24.1.2 (2013-11-19)
This update implements the following changes:

	* Update of the NSPR library to 4.10.2 RTM.
	* Update of the Security library (NSS) to 3.15.3 (alternative branch) to pick up a number of fixes.
	* Fix (finally) of the menu list of tabs when browser.allTabs.previews is set to false. It would stick the top entry, not properly highlight the selected tab, and would generally be unpleasant and stubborn when tabs were moved or closed. This should all be corrected now.
	* Additional feature: Previously, tabs would immediately resize to fill the tab bar when you would close them. Mozilla 更改了 this a (long) while back to cater to "rapidly closing multiple tabs without moving the mouse" and to resize you have to move the mouse out of the tab bar. A good number of Firefox/Pale Moon users don't like this behavior, but the fix to make this configurable was in the end rejected by the Mozilla UX team, so I opted for my own implementation in Pale Moon. New pref: browser.tabs.resize_immediately - set this preference to true to immediately resize other tabs when closing a tab.
	* Many thanks to David for doing the required research for this feature!
	* Rework of the multi-core routine and removal of OpenMP code and the related library (Microsoft's implementation is old, limited, and won't be updated/改进了; in addition it prevented some compiler optimizations that could now be used again).
	* The accessibility back-end for automatically starting "Find as you type" (an accessibility feature) has been disabled completely to prevent this setting from breaking websites with HTML5 input fields (not compatible with autostarting FAYT).

### 24.1.1 (2013-11-05)
This is a minor update to 24.1.0 to revert the change of disabling 2 specific SSL ciphers by default, since it broke more web sites than anticipated (including external elements pulled in from third-party sites using SSL). No other changes were made.
### 24.1.0 (2013-11-04)
This update fixes a number of security and user interface issues, and adds the feed icon in the address bar.

Fixes:

	* MFSA 2013-102 Use-after-free in HTML document templates.
	* MFSA 2013-101 Memory corruption in workers.
	* MFSA 2013-100 Miscellaneous use-after-free issues found through ASAN fuzzing.
	* MFSA 2013-99 Security bypass of PDF.js checks using iframes.
	* MFSA 2013-98 Use-after-free when updating offline cache.
	* MFSA 2013-97 Writing to cycle collected object during image decoding.
	* MFSA 2013-96 Improperly initialized memory and overflows in some JavaScript functions.
	* MFSA 2013-95 Access violation with XSLT and uninitialized data.
	* MFSA 2013-94 Spoofing addressbar though SELECT element.
	* MFSA 2013-93 Miscellaneous memory safety hazards.
	* Security + cleanup fix: No longer store empty event handlers.
	**用户界面**: Fix for the classic downloads window having a blank title with no running downloads.
	**用户界面**: Fix of the drop-down menu "double entry" in the all-tabs list as-a-menu setup.

Changes:

	* Extensions are now set to automatically update by default. Because many users fail to do the occasional check to see if there are updates available to their extensions, the default is to automatically check and install available updates to extensions from this version forward to give the best possible browsing experience. If you prefer to check manually, make sure to change the setting accordingly in your add-on manager.
	* Two SSL ciphers that are considered weak are disabled by default (RSA-RC4-128-MD5 and RSA-RC4-128-SHA). If you are having trouble reaching certain encrypted sites that exclusively use these encryption methods, you should ask the site owners to update their SSL configuration to allow stronger encryption. As a workaround, you can enable the ciphers by installing the Pale Moon Commander add-on and changing the available ciphers there, or by setting security.ssl3.rsa_rc4_128_md5 and security.ssl3.rsa_rc4_128_sha to true in about:config
	* (Note: this change was reverted in 24.1.1)

New Features:

	* When there is a web feed available on a website, Pale Moon will now display a feed indicator on the right side of the address bar to indicate that feeds are available. You can click this icon to subscribe to feeds.
	* If you don't want this indicator, set browser.urlbar.rss to false in about:config
	* Note: more technical information on the forum!

### 24.0.2 (2013-09-27)
This is a small update to address a few issues with standalone images:

	* In some cases when having an image open, the User Interface would not properly redraw resulting in blank controls and tab headers.
	* In some cases, having an image open would cause 100% processor use on one core.
	* Drawing thumbnails of standalone images in the tab headers would often be slow and processor-intensive.

### 24.0.1 (2013-09-18)
This is a small update to address some small issues with the new major version:

	* Fix for unreadable address bar text when visiting a broken or mixed-mode SSL site.
	* Fix for an incorrect browser cache size default when first starting the browser. (regression)
	* Note: If you have used version 24.0, then please check your Options -> Advanced -> Network tab, and if the cache size is set to "1024", change it back to its default "250" to prevent unnecessary use of disk space and potential slowing of the browser.
	* Fix for themes not applying to Private Browsing windows. (regression)
	* A small update to the new icon to fix some visual issues with it.
	* Reduction of visual friction and CPU usage on some operations by disabling smooth scrolling on it by default (e.g. Home/End keys).

### 24.0 (2013-09-13)
This is a new major release with many changes and improvements. A concise summary of the changes follows. There are too many changes and updates (both resulting from the code base update and from the additional Pale Moon development on top) to list all of them in detail.

	* Switch to a new Mozilla code base (Gecko 24.0).
	* Update of the Pale Moon icon/logo. Special thanks go to Roger Gómez del Casal for providing me with an interesting concept design image to use as a base for it!
	* Fixes for all relevant security vulnerabilities.
	* Many changes and updates in the rendering, scripting and parsing back-end to provide significant improvements in overall browser performance (including benchmark scores).
	* Addition of a number of HTML5 elements, improving overall HTML5 standards compliance.
	* Implementation of the webaudio API (most features that are no longer draft).
	* Removal of Tab Groups (Panorama). If you actively used this functionality, I have also made an add-on (Mozilla dev sourced) available to restore this feature to the browser. If you have issues with the supplied add-on or want to give other tab grouping methods a try, you can use alternatives found on AMO.
	* Removal of a few additional Accessibility options.
	* Inclusion of an 更新了 version of the Add-on SDK and loader to solve recent issues with SDK/Jetpack add-ons.
	* Adjustment of the Quickdial "new tab" feature to have better layout.
	* Extension of the address bar shading functionality to more clearly indicate when there is a problem with a secure site (red shading on broken SSL/mixed content).
	* New way of handling plugins with control on a per-site basis. An extensive description can be found on the forum.
	* Restored/maintained a number of features that were removed from recent Firefox versions:
		* Graphical tab switching feature with quick search (Ctrl+Shift+Tab).
		* Removing the tab bar if there is only one tab present.
		* Options for the loading of images.
		* More recovery options in the Safe Mode startup dialog box than just nuking your profile.
		* Send Link/E-mail Link mail client integration functionality.
	* Unification of version numbers. x86 and x64 will from this point forward use the same version number (and icon) without an architecture designation. This will solve potential compatibility issues on new major versions, as well as the superfluous compatibility check when switching between x86 and x64 on the same profile.

Release notes for version 20
### 20.3 (2013-08-13)
This update addresses performance/resource use and also tackles some security vulnerabilities.

Changes:

	* A change to how tab histories are cached to improve the overall memory footprint and make browsing smoother, especially when using a large number of tabs with extensive active use.
	* A change to the networking pipelining back-end to use a more aggressive fallback if there are issues with pipelining requests, to minimize delays when loading pages and prevent time-outs.
	* Update of the compiler to Visual Studio 2012 Update 3, to fix a few compiler issues.
	* Removed the double entry for smooth scrolling selection in preferences (leaving just the one in the scrolling tab)

Fixes:

	* (CVE-2013-1704) ASAN heap-use-after-free in nsINode::GetParentNode
	* (CVE-2013-1708) Non-null crash at nsCString::CharAt
	* (CVE-2013-1712) Code injection through internal updater
	* (CVE-2013-1713) InstallTrigger can use the wrong principal when validating URI loads
	* (CVE-2013-1714) Cross Domain Policy override using webworkers
	* Fix for Updater crash
	* Fix for XSS vulnerability/URI spoofing
	* Fix for newly allocated WebGL array buffers (prevent the use of uninitialized memory)
	* Several fixes for the SSL crypto library (CVE-2013-1705 and others)
	* Fix for do_QueryFrame support
	* x64: Fix for Yarr error
	* Update to the installer's 7zsfx module to prevent dll hijacking

Portable version:
Important note for updating the portable version: it's recommended you make a fresh install of the portable and copy over your user profile to the new install with this update. Do not use the internal updater. Remember to check your user.ini if you have created one or 更改了 .ini entries, and re-implement your changes in the 20.3 palemoon-portable.ini (don't just copy it over!)

	* Fix for safebrowsing
	* Enabled the XUL cache to improve startup times

### 20.2.1 (2013-07-08)
A small update to address issues with the new Aero glass theme, e.g. Tab Groups not showing.
### 20.2 (2013-07-01)
This is a maintenance update, focusing on visual improvements and security.

Changes:

	* Implementation of some conservative additional multi-core support (mainly in graphics/media) using OpenMP. I'm taking baby steps here and will remain conservative in the use of multiple cores so stability of the browser isn't needlessly endangered.
	* Update of the navigation button icons (again). Users have clearly indicated that the inverted color icons on glass and dark themes were less desirable. I've listened, and 更改了 the icons for glass back to the pre-20 style but with 添加了 contrast, and made a distinction for dark personas (themes) where the icons are now simply inverted white (like in Firefox).
	* Change for the color management system (CMS) so that Pale Moon now supports more types of embedded ICC profiles (including the already decade-old version 4 spec) and in the process fixing potential color issues on screens with images that embed such profiles.
	* Update of the browser padlock code. You can now choose both a "modern" look (as introduced in version 19) and a "classic" look (as introduced in version 15, when this padlock feature was first 添加了). It also removes some phantom spacing in locations where the padlock isn't used (thanks for the pointer, Sowmoots!).

Fixes:

	* (CVE-2013-1692) Fix for the inclusion of body data in an XMLHttpRequest HEAD request, making cross-site request forgery (CSRF) attacks via a crafted web site more difficult.
	* (CVE-2013-1697) Fix to restrict use of DefaultValue for method calls, which allows remote attackers to execute arbitrary JavaScript code with chrome privileges.
	* (CVE-2013-1694) Fix to properly handle the lack of a wrapper, which allows remote attackers to cause a denial of service (application crash) or possibly execute arbitrary code.
	* (CVE-2013-1690) Crash fix (MFSA 2013-53) used to crash Tor users on certain Tor sites.
	* Fix to prevent arbitrary code execution from the profiler developer tool.
	* Fix for a crash when rapidly reloading pages.
	* Fix for cross-document selections.
	* Fixes for several crashes in JavaScript.
	* Fixes for several memory safety hazards and uncommon memory leaks.

### 20.1 (2013-05-23)
This is a security and stability update with a few additional changes and improvements.

Changes:

	* Update of the libpixman graphics library to improve performance for SSE2 CPUs
	* Change to the "Clear download history" setting for use with the panel-based download manager (classic UI unaffected)

Fixes:

	* (CVE-2013-1674) Fix for UAF with video and onresize event (crash fix)
	* (CVE-2013-1675) Fix for parameters being used uninitialized
	* (CVE-2013-1676) Fix for out-of-bounds read in Selection迭代::GetNextSegment
	* (CVE-2013-1679) Fix for heap use-after-free in mozilla::plugins::child::_geturlnotify
	* (CVE-2013-1680) Fix for heap-use-after-free in nsFrameList::FirstChild (crash fix)
	* (CVE-2013-1681) Fix for heap-use-after-free in nsContentUtils::RemoveScriptBlocker (crash fix)
	* Fix for out-of-bounds read crash in PropertyProvider::GetSpacingInternal (crash fix)
	* Fix for out-of-bounds read in gfxSkipChars迭代::SetOffsets
	* Fix for assertion failure in nsUnicharStreamLoader::WriteSegmentFun with ISO-2022-JP
	* Fix for crash with inline script in an XML doc (crash fix)
	* Fix for "ASSERTION: Out of flow frame doesn't have the expected parent" and crash  (crash fix)
	* Fix for nsScriptSecurityManager::CheckLoadURIWithPrincipal being broken
	* Fix for a problem where the IPC Channel could overwrite the stack
	* Fix for Crash in MediaDecoder::UpdatePlaybackOffset (crash fix)
	* Fix for Crash [@ nsTextFrame::HasTerminalNewline()] with splitText (crash fix)
	* Fix for FTP use-after-free crash  (crash fix)

More details can be found in the release announcement post on the forum.
### 20.0.1 (2013-04-11)
This is mostly a bugfix, security and performance update, but with a number of new features as well, based on the Firefox 20 code base:

New/updated/更改了 major features:

	* Per-window Private Browsing. Learn more.
	* Panel-based download manager. See the detailed changelog for more information.
	* Ability to close hanging plugins, without the browser hanging.
	* Performance improvements related to common browser tasks.
	* Pale Moon specific Cairo performance fix for scaling/panning/zooming of HTML5 drawing surfaces.
	* Pale Moon specific fixes for performance of drawing elements (gradients, etc.).
	* HTML5 canvas now supports blend modes.
	* Various HTML5 audio and video improvements.
	* Update of the Status Bar code to work with the new code base.
	* ECMAScript for XML (E4X) is kept available for add-ons. Note that this will be removed in future versions as E4X is obsolete.
	* Developer tools have been enabled by default, considering the code is practically impactless unless actually used.
	* Theming has been worked on to provide better contrast on glass/dark themes and to work around styling issues present in v19.
	* 更新了 fallback character sets to Windows-1252.
	* Restored legacy function key handling (uplifted from Firefox 22).
	* 修复了 UNC path handling (Chemspill Firefox 20.0.1).
	* Always enable the use of personas, also in Private Browsing mode.
	* Experimental: support for H.264 videos (disabled by default)

**安全修复** relevant to Pale Moon:

	* MFSA 2013-30 A fairly large number of memory safety hazards (crashes/corruption/injection).
	* MFSA 2013-31 Out-of-bounds write in Cairo library (CVE-2013-0800)
	* MFSA 2013-34 Privilege escalation through Mozilla Updater (CVE-2013-0797)
	* MFSA 2013-36 Bypass of SOW protections allows cloning of protected nodes (CVE-2013-0795)
	* MFSA 2013-37 Bypass of tab-modal dialog origin disclosure (structural fix)
	* MFSA 2013-38 Cross-site scripting (XSS) using timed history navigations (CVE-2013-0793)
	* MFSA 2013-39 Memory corruption while rendering grayscale PNG images (CVE-2013-0792)
	* MFSA 2013-40 Crash fix: Out-of-bounds array read in CERT_DecodeCertPackage (CVE-2013-0791)

Detailed descriptions for these changes and fixes can be found in the detailed changelog/announcement post on the forum.

### 20.0 -- Internal testing release, unpublished.
Release notes for version 19
### 19.0.2 (2013-03-09)
A minor update prompted by a security update @Mozilla:

	* Fixes a critical security vulnerability in the browser (MFSA 2013-29)
	* Slightly improves HTTP pipelining
	* Update to the integrated status bar feature (German localization updated)

### 19.0.1 (2013-02-24)
A minor update to address a few issues with the initial major release:

	* Fix for bookmarks giving an "XML parsing error" when set to "load in the sidebar"
	* Fix for a double padlock display if a secure site would not supply a favicon
	* Redone the mixed content https padlock image in 32bpp to prevent potential UI rendering issues
	* 修复了 a setting so no unnecessary code walking is done for the otherwise disabled accessibility features
	* Fix (inherent) for add-ons and themes being marked as incompatible in Pale Moon x64 when they have a minimum version of 19.0

### 19.0 (2013-02-22)
This is a new major release with a lot of changes and improvements:

Changes in this version:

	* Update of the underlying Firefox (gecko) code to v19. This has a number of consequences:
		* Add-ons and themes may need to be 更新了 since the UI code has 更改了.
		* HTML5-implementation is more complete
		* A number of CSS statements have their prefix removed (-moz*)
		* Javascript now uses the IonMonkey engine by default, which is a new (faster) engine
		* Improvements to the layout and rendering engines
		* If you are using a language pack, you need to update it to the new version
	* Update of the browser style. Main browser controls and the padlock look slightly different.
	* Several Pale Moon specific improvements to the rendering engine, noticeable in general use and certain benchmarks, to prevent browser stalls or high CPU usage on certain pages.
	* The builds no longer use PGO (Profile Guided Optimization) but are globally speed-optimized.

For details about each of these points, see the detailed changelog post on the forum.
Release notes for version 15
### 15.4.1 (2013-01-28)
This is a bugfix and security release. Changes in this version:

	* 更新了 the C runtime library included to a later version for security/stability purposes.
	* 更新了 the Windows SDK version to 8.0 for better Windows 8 compatibility and slight overall improvements.
	* Implemented a fix to prevent unwanted automatic opening of the plugin check window on startup on some systems.
	* Corrected the milestone marker from 15.4pre to 15.4.

In addition, this version was built on a fresh build environment to prevent possible code pollution and improve profiling efficiency.
### 15.4 (2013-01-16)
Several security and stability issues have been 修复了 in this update:

	* Deal with bogus Turktrust certs MFSA 2013-20
	* Several memory security hazards 修复了 MFSA 2013-01
	* 更新了 OTS library to r95 to fix potential font-related exploits
	**安全修复** for libpixman stack buffer overflow
	* Fix for certain types of input lag on Twitter/Facebook & other sites with unnecessary DOM invalidations
	* Fix for HTTP pipelining re-use (improve pipelining logic)
	* Performance&stability updates to cairo and direct2d back-end
	* 改进了 performance for repeat gradients

### 15.3.2 (2012-12-05)
This update fixes an important issue in the JavaScript engine (MethodJIT) that would make particularly large/complex pieces of JavaScript (e.g. Mandreel) fail. (Thanks, Ryan, for catching this one!)
### 15.3.1 (2012-11-30)
This update is a bugfix and performance release with a number of security, stability and efficiency fixes:

Bugfixes:

	* Fix for font rendering issues on Windows 8 (cairo+azure)
	* Status bar options: Russian locale 修复了
	* Fix for status bar address bar linkover ghosting
	* Fix for browser hang in some WebM video content
	* Don't allow alert/confirm/prompt in onbeforeunload, onunload and onpagehide (bug# 391834)

Improvements:

	* Reduce non-incremental GC occurrences (reduce lag in Javascript)
	* More efficient CPU usage for JS and Canvas
	* Pale Moon x64: Performance improvements

**安全修复**:

	* **安全修复** for CVE-2012-5840, CVE-2012-5839, CVE-2012-4210, CVE-2012-4207 and CVE-2012-4214.
	* Fix for methodjit assertion issue (bug #781859)
	* Fix for potentially exploitable crash in XPConnect (bug #809674)
	* Fix for potentially exploitable crash in layout engine (bug #791601)
	* Fix for potentially exploitable crash in JS string handling (bug #778603)
	* Fix for potentially exploitable crash in GIF decoder (bug #789046)
	* Fix for potentially exploitable crash in image decoder (bug #802168)
	* Fix for use-after-free in editor lib (bug #795708)
	* Fix for potentially exploitable crash in SVG (bug #793848)
	* Fix for out-of-bounds read when blurring (bug #783041)
	* Fix for potentially exploitable crash in text editor (bug #798677)
	* Prevent URL spoofing through prompts (bug #700080)

### 15.3
This is an important update that sees a number of under-the-hood changes. The are no functional changes in this update.

Changes:

	* The compiler has been 更改了 to a newer version (Visual Studio 2012). This has a few consequences:
		* Better handling of the browser overall: things like smooth scrolling, the user interface and page loading should be noticeably smoother on the vast majority of computers.
		* Automatic vectorization: If your hardware supports it, more advanced processor instructions are used.
		* Support for multiple cores.
		* The 64-bit version of Pale Moon will no longer support Windows XP. More details in this post.
	* Incremental garbage collection for Javascript.

Bugfixes:

	* Minimize intermediate surface size in Azure to mitigate performance regression.
	* Fix SVG clip paths in Azure.
	* Fix drawing artifacts in Azure.
	* Fix fuzzy equal function.
	* Some fixes for the Windows Aero user interface that popped up with the new compiler.

A slightly more detailed description can be found in the changelog on the forum.
### 15.2.1
This update incorporates critical **安全修复** back-ported from Firefox 16.0.2 (MFSA 2012-90)
### 15.2
This is an update to address a number of performance, stability and security issues, as well as some 添加了 features.

Fixes:

	* Important performance regression fix. Both javascript and the layout engine should now have the speed and stability that is to be expected from an optimized browser.
	* Fix for the "tabs on top" menu entry not showing when tabs are already set on top, making it very difficult to switch them back to bottom.
	* Crash: Fix for a browser crash with certain types of invalid gradients. (bug #792903)
	* Security: Prevent private browsing data leakage through popup windows (bug #795015)
	* Security: Detect IC purging (bug #794025)
	* Security: Prevent mRules from dying in DoInsertHTMLWithContext (bug #788950)
	* Security: Drain the parent frame's overflow list before insert/append (bug #765621)

Features:

	* Redesigned the identity panel and the way secure sites are handled in the UI
	* You will now always get the favicon in the address bar, and on secure sites you will have an 添加了 padlock (indicating ssl, extended verification or a broken/insecure/mixed-content site) to the identity panel and colored shading around the URL to indicate the status. (see detailed changelog)
	* After evaluating the new address bar autocomplete algorithm, it is now switched on by default.
	* 添加了 an option to easily switch address autocompletion on or off (see detailed changelog)
	* Partial implementation of Japanese "status bar" preferences text

More details can be found in the detailed changelog on the Pale Moon forum.
### 15.1.1
This is a minor update to address some important performance (high CPU usage) and stability (browser hang) issues in Pale Moon 15.1. Specifically, some of Tete009's patches were backed out.
Azure acceleration with his patches is still in place, but the multi-threaded box blur and cairo patches were removed to fix the CPU and browser hang issues, respectively.
### 15.1
This is a major update to the new v15.0 release, to address a fairly large number of issues with the initial version.

Important note:

	* From this release onwards, the system requirements for your operating system have 更改了: If you are still running Windows XP, you are required to have Service Pack 3 installed on it, or the browser will not start.

Bugfixes:

	* Restore Windows XP Professional x64 compatibility in the installer.
	* Fix the mouse wheel smooth scrolling preferences in the preferences dialog box (did not work in v15.0)
	* Prevent memory inflation on some integrated graphics drivers in canvas games
	* Fix for private browsing mode (Firefox 15.0.1 top fix)
	* Fix for Javascript stability issues on 32-bit versions

Regression fixes:

	* Restore the favicon in the URL bar. (Behavior change: new logic)
	* Fix for top level images with transparency (white background)
	* Remove noise from top level image background
	* Undo the redesign of the Safe Mode dialog box
	* Restore Alt-Click save dialog box
	* Restore proper identity panel for domain-verified sites (blue panel)
	* Restore support for the browser.identity.ssl_domain_display setting
	* Restore address bar autofill preference to its desired default state (no autofill)

添加了 features:

	* Add control for a custom top level image background color
	* Implement Direct2D brush caching (performance win)
	* Implement multi-threaded box blur (performance win for multi-core systems)
	* Add a Profile Reset feature (from Help -> Troubleshooting information)
	* Build with a faster floating point method

To keep these release notes concise, this is just a plain list of changes. You are encouraged to read the extended changelog post on the Pale Moon forum if you have any questions or want clarification about any of the items mentioned.

### 15.0

This is a new release based on the Gecko 15.0 code base with additional branch development. It incorporates many changes under the hood that go far beyond the scope of this document.

A few highlights, in addition to **安全修复**:
Performance improvements for the rendering engine
More HTML 5 implemented
Better handling of memory, resulting in smoother operation of the browser
More responsive user interface when the browser is busy
Prevention of memory leaks through add-ons
Better implementation of the Quickdial page
Localization of Pale Moon specific preferences and options (work in progress)
Reinstatement of the previous user interface, keeping it in line with version 12 (Firefox 15 has UI changes that makes the controls flat, monochrome and borderless, which isn't desired for Pale Moon)
The padlock has returned for secure pages! It can be found in front of the URL when you browse to a secure page, with optionally company information if supplied by the server
Some things new to the Firefox code base that are excluded or disabled by default:
Built-in PDF reader in javascript - use a standalone, dedicated reader
(this is both a security and functionality consideration)
Additional advanced web development tools - the average user never needs these
Web apps on the desktop - Pale Moon is a browser, not a pseudo-OS
Windows Metro UI

Release notes for version 12
### 12.3 r2

This is a rebuild of Pale Moon 12.3 to address some performance regression in the 32-bit version of Pale Moon 12.3. No functional changes have been implemented in this release, and updating the browser is completely optional, but recommended if you experience lesser performance in Pale Moon 12.3 than you are used to.
This build should give overall smoother operation of the browser and better HTML5 video playback (WebM/Theora) than the original release.

Note: once again, this is to address a regression that was only present in the 32-bit (x86) version of Pale Moon 12.3 and does not affect Pale Moon x64. Pale Moon 12.3r2 is an update for the 32-bit version only and completely optional if you are already on v12.3.
### 12.3

This is a maintenance release to address a number of potential security vulnerabilities.

Most notably among them:
Use-after-free while replacing/inserting a node in a document
Content Security Policy inline-script bypass
A few additional memory safety hazards and crashes that could theoretically be exploited
Additional note: the initial binaries as-published had a missing component that caused saving of a session to malfunction and not properly restore. If you have downloaded 12.3 x86 between 12:00 and 17:00 Central European Summer Time (Z+2) on 17/7/2012, or x64 on the same day between 12:00 and 19:00, you may have a faulty browser and you should download and re-install the browser. Apologies for the inconvenience!
### 12.2.1

A minor update to fix stability issues:
Fix for Flash 11.3 crashing the plugin container or browser upon shutdown.
Note: Flash 11.3 introduces "protected mode", an internal plugin sandbox, that can still cause other issues, e.g. for full-screen video playback. Please check the forum announcement for more information, workarounds and advice if you experience issues.
Fix for double entries for "recent tags" and "recently bookmarked" in the bookmarks menu on a new profile.
Fix for build instability issues in javascript due to the Microsoft compiler producing incorrect machine code in some cases. This fix will cause a slight performance loss on 32-bit builds to prevent crashes and scripting problems in the GUI and on web pages. Pale Moon x64 is not affected.
### 12.2

A minor update but introducing some new features.

Most important changes:
Privacy issue: clear the QuickDial page when history is cleared
Better, neutral background color for raw image viewing
Smooth scrolling 改进了; also disabled smooth scrolling for page-by-page by default
Smooth scrolling can now be configured/tuned in detail in Advanced Options
Some changes to the build method for x64 for potentially better performance on some systems
### 12.1

A major update to the browser, implementing a number of visual and under-the-hood changes.

**安全修复**:
Bug #745580 Thebes: handle bad results from Core Text shaping more robustly.
Bug #744541 XPCOM i/o: Charset conversion issue.
Bug #748613 Javascript: Scope vulnerability
Bug #747688 Layout engine: Drop references for all destroyed frames
Security update of the included MSVC runtime libraries
Enhancements and fixes:
Dynamic smooth scrolling algorithm for mouse/keyboard implemented. Smooth scrolling is now also enabled by default.
Update to the status bar code to fix pop-up status not switching sides on mouse-over, as well as using a safer allocation/destruction mechanism for controls (potentially preventing memory leaks).
修复了: cache size override on new profiles (would be set to 1GB instead of the application default of 200MB). Bug 20120512-GN.
Addition of a number of preferences in the Tabs category of the options dialog box:
A checkbox for inserting related tabs next to the current tab when opening a link;
A checkbox for closing the browser window when the last tab is closed;
A selection for new tabs: Choose from a blank page, the Pale Moon start page or the Quickdial page.
Some slight color has been re-introduced in the navigation elements to improve clarity of the UI.
Disabled an image decoding library with hazardous code. This has no impact on the browser's image decoding capabilities or performance as alternative methods for decoding are used by default.
Some changes to memory handling which potentially keep memory use better within bounds.
A change to the build environment to improve stability of Javascript. Note that this is a trade-off and may result in a slight drop in synthetic benchmarking performance of the browser compared to the previous version of Pale Moon. The impact of this on overall real-world performance of the browser is negligible.
### 12.0

A new release built on the Firefox 12 code base. This is mostly a maintenance release.
Of special interest is that Pale Moon, unlike Mozilla Firefox in its version 12, does not move to a silent install method.

Fixes and changes in all versions:
A number of security and stability fixes imported from Firefox 12
Update to the status bar code and a finalization of the integration of this functionality
Localization of the status bar preferences and messages into 3 additional common languages: German, French and Spanish. This will automatically follow your locale setting
Update to the HTML5 media controls
Some under-the-hood changes that will further improve performance of Pale Moon on some systems
Pale Moon Portable:
An update to the launcher and script. More information on the Pale Moon Portable page. It is recommended for everyone using the portable to make a fresh install (with a copy over of your profile files if desired) and not use an in-place upgrade.
A fix for backups not being properly created and stored
This version marks the start of a different release schedule for Pale Moon.

Instead of following the rapid release schedule of Mozilla, the browser will use version 12, a properly matured build with essential functionality, as a base to make incremental updates upon.

The reasons for this are multiple, not in the least it will allow Pale Moon to implement things that have been on the "to-do" list for a while but which have been pushed back because of lack of time "keeping up" with the (too) fast releases of new versions by Mozilla. The rapid releases often little more than maintenance updates and one or two new features (sometimes even just partially implemented), but requiring a full development/testing cycle for Pale Moon because of the lumped-together patches. Another reason is that from this point on, Firefox will receive a few user interface overhauls to go off on the "Web OS"/"Metro"/"Desktop integration" tangent that goes against Pale Moon's goals of being and remaining a web browser.

Release notes for version 11
### 11.0.1

A small maintenance release to address a few annoyances in the original new release of v11.0:
Tone down the rather too aggressive network settings that were introduced in Firefox 11:
Maximum concurrent connections opened by Pale Moon lowered to 48 (was 256) to make sure it doesn't easily saturate the networking layer of Windows, to prevent residential NAT gateways from being overloaded and to lower strain on wireless networks
Maximum concurrent connections to a single server lowered to 6 (was 15). In tandem with pipelining this is still plenty, and it actually promotes the proper intended use of pipelining
Fix the installer to properly check for the minimum required operating system version: Windows XP for both x86 and x64 versions
Switch off OpenGL as preferred engine for WebGL again to fix compatibility problems
Switch off DirectWrite font rendering again to fix compatibility issues with certain graphics cards
Properly implement the removal/blocking of status bar add-ons when upgrading/installing
In addition, Pale Moon 11 will:
Save open session information less often (once a minute)
No longer store form data and other entered information in the browser session store when pages are viewed over SSL, to increase security - the data entered in secure pages is no longer committed to disk.
### 11.0

A new major release building on the Firefox 11.0 code base. This sees many, many bugfixes and a good number of performance improvements that would be too extensive to list in detail.
In summary

All versions:
Integration of the Status Bar functionality. You can now access the status bar configuration directly from the Tools or Options menu, and it is no longer a separate add-on[note]
Implementation of the SPDY protocol to improve load times on websites that support it
Improvements to the rendering engine, and specific improvements to the hardware acceleration of font rendering and WebGL
Implementation of more advanced HTML5 (including IndexedDB improvements and support for more HTML5 elements) and CSS features (including CSS 3D transforms)
Add-on compatibility: add-ons now default to being compatible
Cosmetic updates to the Pale Moon icon and some included artwork
The (limited feature) web developer tools as 添加了 to Firefox 11.0 have mostly been disabled since they are not intended to be present in future builds of Pale Moon. Web developers are encouraged to make their own choices about which development tools they wish to use at the Mozilla Add-ons repository (Web development section)
Pale Moon Portable:
The automatic backup method has been simplified and the resulting backups will take (a lot) less space. Bookmarks and passwords are backed up, but history no longer gets backed up which saves many MB on your stick or other portable medium
Additional compression further reduces space requirements for the 32-bit portable
Release notes for version 9
### 9.2

This update implements **安全修复** from Firefox up to 10.0.2 in terms of security and stability.
Fix for a critical vulnerability in the libpng graphics library
Update to the add-ons blocklist and its handling
New 64-bit application icon (32-bit icon update in the next version)
Minor updates to cache handling settings
### 9.1

This update implements relevant fixes from Firefox 10 in terms of security and stability. Additional new functionality found in Firefox 10 has not been implemented.
In addition, the following fixes:
Update to the status bar component to fix pop-up status and links, as well as a few other small issues
Update to the add-on compatibility assistant to no longer display the status bar core add-on as selectable
Update to a few default settings based on usage metrics
Removed some commercial search engines (e.g. Amazon) and 添加了 DuckDuckGo/SSL
### 9.0.1

An update incorporating the Firefox 9.0.1 code base.
In addition, the following changes:
Under the hood changes and improvements to the way memory is handled by the Javascript engine
WebGL has been 更改了 to use ANGLE by default instead of using native OpenGL to give better performance on a number of systems that would otherwise suffer from high CPU usage and lower frame rates
Change in compiler: from this point on, Visual Studio 2010 will be used for all "next gen" builds
Build environment 更改了 to cater to the ever-growing XUL dll size without having to compromize on what modules to optimize. (Prevent running into the 3GB address space limit)
DNS prefetching disabled by default to prevent router hangups
Changes to timings for UI script execution and content script execution to prevent unnecessary dialog popups about unresponsive scripts
Some image decoding tweaks
Eye candy: animated preferences dialogs (resize when switching category)
### 9.0

Development version (unreleased).
This version was not considered acceptable for release due to performance regressions.
Release notes for version 8
### 8.0

A major update building on the Firefox 8.0 code base, with improvements that were planned for the (unreleased) version 7.0.2.
This version sees the following improvements in addition to those inherent to Firefox 8:
改进了 cache handling: this will make the browser handle system resources more efficiently on most systems
改进了 networking: communication with web servers should be noticeably faster and smoother
Fix for a rare image decoding bug (garbage, possible crashes)
It should be noted that the shift in focus of development has been towards the back-end of the browser (background resource handling and background networking), considering the rendering and scripting speed is not the bottleneck for current versions of the browser. Inherently, this may result in less of a clear difference in benchmark scores when comparing to its vulpine sibling or previous versions of Pale Moon because of rebalancing of code priority when building. Maximum benchmark scores are nice, of course, but the main goal of Pale Moon remains to be as efficient as possible when taken as a whole, including those parts that aren't measured in limited benchmark tests.
Release notes for version 7
### 7.0.1

This update fixes a very important speed regression issue for Pale Moon 7.0. It impacts mostly the page content layout engine and DOM handling, which will be on par again with what they should be for Pale Moon in this point release. Bug: 20111001-CCBug
Benchmarking scores will see a significant jump from 7.0 to 7.0.1 因此， as well.
There are no other functional or UI changes for this release.
### 7.0

A new release building on the Firefox 7.0.1 code base. This version sees a large number of performance increases, as well as lower resource use than the previous version.

Additional changes:
Introduction of the Tab Groups (panorama) button in the user interface for easy access (Next to the All Tabs button)
Several additional performance improvements on individual browser components
A change of the Application Menu button color to blue shades instead of a "foxy orange"
Release notes for version 6
### 6.0.2

A security update seeing the following changes:
Removed trust exceptions for certain certificates (bug 683449)
Resolved an issue with gov.uk websites (bug 669792)
Revoked permissions for the root certificate for DigiNotar in the built-in certificate store (bug 682927)
In addition, there has been some work done on the x64 build method to prepare for performance fixes in a future release.

### 6.0

New release based on Firefox 6.0!
Of course the necessary bugfixes and changes as part of the new code base, with a number of additional changes:
Add-ons will no longer automatically update by default the moment they are checked and found to have a newer release, giving the user the choice to accept or reject the update, read release notes, etc.
Update of the status bar add-on to v2.2, fixing compatibility issues and extending some configurability
Link right-click menu has "Open in new tab" on top now, like Firefox. If you are having trouble retraining yourself for this behavior, please download a menu editing Firefox add-on to customize your menus. This change was made based on user feedback
添加了 ak, ast, br, bs, en-ZA, gd, lg, mai, nso, and son language packs
Release notes for version 5
### 5.0

New release based on Firefox 5.0!
Of course a large number of bugfixes were applied as part of development on the Mozilla trunk, compared to 4.x

**变化/修复**:
Performance issues 修复了 on some systems
Instability problems 修复了 on some systems
更新了 artwork for the new about box
Cosmetic changes: more occurrences of "palemoon" in the UI should now read "pale moon"
Zulu language 添加了 for the language packs
Release notes for version 4
### 4.0.7

Fixes:
Windows 7 jumplists 修复了
Fix for errors in the error console when closing tabs in certain situations
Potential fix for printing problems (no text printed) Still an issue
### 4.0.6

Update of the source base to Firefox 4.0.1, fixing a large number of bugs.

Additional updates:
Performance fix: Switched back globally to fast floating point model, with a patch to prevent rounding errors in javascript
Compensated for a number of internal compiler errors causing build issues and potential browser stability problems on some systems
### 4.0.5

A number of fixes and a cosmetic update:
Performance fix: Javascript performance 改进了
Crash fix: Prevent crashes in optimized builds of JS due to 20110410-CCBug
Updater fix: Internal updater should function again from this version onward
Add-ons window shows the proper add-ons page when loading it
Shell integration 修复了 for Vista and 7: The browser should no longer complain that it's not the default program when it, in fact, is. See bug 20110408-SHBug
Main Pale Moon program icon 更新了 with a higher-res version of the logo image
### 4.0.3

Some stability bugfixes and improvements:
Fix for a potential crash of the browser due to 20110406-PRBug
Fix for the internal manual updater when a language pack is installed
DirectWrite now default OFF (gfx.font_rendering.directwrite.enabled=false) to provide better compatibility with problematic (integrated) graphics processors. If it worked for you for 4.0, feel free to switch it back on (set to true)
Improvements to GUI/chrome speed
If you use a language pack, you will have to update it to the latest version for it to work.
### 4.0

This is a brand new release!

Built on Gecko 2.0, the browser has the following new features:
Hardware acceleration of browser windows using Direct3D
Direct2D rendering on operating systems and hardware that support it
DirectWrite font rendering on systems that support it
WebGL 3D graphics, either using native OpenGL (default) or DirectX (via ANGLE)
HTML5 support
New Jaegermonkey javascript engine
Blazingly fast DOM handling
Of course, the well known features from version 3.x are still present, as well:
Graphical tab previews (on a nice glass pane if you have Windows 7) with search
Dynamic/downloadable fonts (including WOFF)
Support for personas and Firefox themes
Support for Firefox 4 compatible add-ons
Support for OOPP (Out-of-process plug-ins)
Able to use existing Firefox profiles, bookmarks and settings (either using the migration tool or using Sync)
Since this is a new release, it may be a little less stable than the tried-and-tested 3.x releases, but no major issues have been found thus far.