# 解构勒索病毒杀伤链

> 原文：<https://medium.com/codex/deconstructing-the-ransomware-kill-chain-e22390362705?source=collection_archive---------28----------------------->

![](img/3dadb90f10a5f864b5d8c1b357b80e69.png)

从设计上来说，勒索软件是一种相对“嘈杂”的恶意软件，其杀伤链为网络防御人员提供了成功检测和缓解这种类型威胁的多种机会。通过绘制勒索软件入侵的步骤，我们可以更好地了解恶意软件本身，并提高我们在该过程的各个阶段绘制控制、对策和防御技术的能力。

这篇文章将引用一个名为 TeslaCrypt 的广泛传播的加密勒索软件的杀伤链，但也是一个常见勒索软件攻击的基本结构。

第一步:侦察

攻击者收集目标的信息；这可以通过查看网上公开的信息或社会工程技术来实现。这是在实际攻击之前完成的，可以主动或被动地在幕后发生。对于大多数勒索软件攻击来说，受害者不是特定的目标，因此可能不会受到传统意义上的侦察。但是，一些勒索软件团伙确实会扫描和识别易受攻击的组织，以便针对它们进行攻击。此外，在更广泛的网络犯罪市场背景下，网络犯罪分子不断进行侦察，以识别易受攻击的基础设施，这些基础设施可以适应恶意软件杀伤链各个阶段的不同需求。

步骤 2:武器化

攻击者创建恶意漏洞并发送给受害者。这一步也发生在攻击者一方的幕后，不与受害者接触。例如，一个漏洞利用工具包可以对受害者计算机进行分析，以便利用它们易受攻击的特定漏洞，还有一个 Office 文档带有可以作为电子邮件附件发送的恶意宏。

第三步:交付

攻击者使用诱饵发起攻击；这可以通过钓鱼电子邮件、链接、受感染的附件、恶意广告或受损网站将恶意软件发送给受害者来实现。目前，所有网络钓鱼电子邮件中有 93%是勒索软件，这使得它成为有效载荷传递中最广泛的恶意软件变体。尽管一些 IT 部门为员工提供了严格的反网络钓鱼培训，但社会工程仍然是一种非常成功的方法。如果用户接受了攻击者使用的入侵方法之一的“诱饵”,如跟踪链接或打开恶意附件，则会触发下一阶段。

步骤 4:安装或利用

当攻击者使用恶意软件作为其攻击的一部分时，安装是相关的。受害者点击或打开恶意文件，在用户设备上执行恶意软件。在许多情况下，受害者并不知道恶意软件正在被执行，也不知道设备正在被感染。

步骤 5:密钥交换和呼叫总部(命令和控制)

创建了一个命令和控制(C&C)通道，使攻击者能够远程控制其内部资产，并且可以提前几个月或在运行中设置。在恶意软件执行和系统感染后，恶意软件会联系或“呼叫总部”服务器，以生成和检索密钥对。与非对称密钥加密方案中的公钥不同，只有成对私钥的持有者才能解密文件系统。从服务器接收加密密钥，以便对文件进行加密，然后在受害者支付赎金后用相同的密钥对解密。请注意，并非所有勒索软件都会向 C&C 服务器获取加密密钥，因为加密密钥可能是在机器上本地生成的，具体取决于勒索软件的变种。

步骤 6:加密和持久性

在机器上首次执行勒索软件后，恶意软件开始搜索与被硬编码到恶意软件的目标文件扩展名列表中的扩展名相匹配的文件。勒索软件递归地在任何安装的驱动器上执行这些搜索，无论是本地驱动器、USB 驱动器、网络共享等。当找到与扩展名匹配的文件时，会创建一个临时文件来加密原始文件内容。然后，原始文件被相应的加密文件覆盖和替换，以限制访问。这种方法有效地阻止了受害者获取数据。硬编码到恶意软件中的文件扩展名通常包括 300 多个目标文件扩展名，确保机器上的每个有用文件都在此过程中被加密。该恶意软件利用持久性技术，如创建注册表项，使其能够在启动时运行，并在系统重启时以安全模式继续加密。

第七步:赎金和勒索

在加密过程完成之后，为了重新获得对数据的访问，攻击者要求付费来用他们唯一的解密密钥解密数据。该请求通常是在加密过程之后通过弹出窗口发出的，通知受害者他们的数据被加密。在这个弹出窗口中，受害者将找到提交付款的指令，包括创建比特币钱包和提交付款的 URL，通常通过 Tor 匿名网络，网址为. onion。请注意，支付赎金并不保证攻击者会遵守交易。

利润？