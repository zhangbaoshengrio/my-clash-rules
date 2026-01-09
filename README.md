# 为什么要自己维护规则集呢
因为有一些特有的域名你想让它特定的策略组,再比如有一些域名走了Final或者兜底分组,你想让它走Direct(直连)…… 类似于这样的自我定制化的需求就需要自己去维护自己的规则集了.



# 配置建议：
建议将规则集 Fork 到个人的 GitHub 仓库，以确保配置的长期稳定性。在编写 YAML 配置文件时，请引用规则集的 Raw（原始链接） 地址。

语法说明： RULE-SET,Google,Google

参数一： RULE-SET 标识符。

参数二： 远程规则集名称（或引用别名）。

参数三： 策略组名称（需与 proxy-groups 中定义的名称保持一致）。



# 配置模板：

YAML

请将下方的 URL 替换为你自己的 GitHub Raw 链接

方案二：步骤拆解式（适合零基础教程）
配置步骤：

获取链接： 进入你的 GitHub 仓库 -> 点击 Auto.yml -> 点击页面右侧的 [Raw] 按钮 -> 复制浏览器地址栏 URL。

填入参数： 将该 URL 粘贴到配置文件的 url: "" 之中。

代码示例： Auto: {type: http, behavior: classical, url: "在此处填入你的Raw链接", path: ./ruleset/Auto.yaml, interval: 86400, format: yaml}

注意： 必须使用以 raw.githubusercontent.com 开头的链接，直接使用仓库页面链接会导致配置加载失败。


```  
rules:

  # 1. 拦截所有包含 stun 关键词的域名
  - DOMAIN-KEYWORD,stun,REJECT
  # 2. 拦截所有包含 turn 关键词的域名
  - DOMAIN-KEYWORD,turn,REJECT
  # 3. 拦截 UDP 3478 端口（这是 WebRTC 探测最常用的端口）
  - AND,((NETWORK,udp),(DST-PORT,3478)),REJECT  
  - RULE-SET,野比(AD_Block),REJECT
  - RULE-SET,野比(AD_Block_Plus),REJECT
  - RULE-SET,毒奶特供,REJECT
  - RULE-SET,Auto,Auto
  - RULE-SET,Apple,Apple
  - RULE-SET,Twitter,Twitter
  - RULE-SET,BiliBili,DIRECT
  - RULE-SET,Direct,DIRECT
  - RULE-SET,Google,Google
  - RULE-SET,GoogleVoice,GoogleVoice

  - RULE-SET,Microsoft,Microsoft
  - RULE-SET,OpenAI,AI
  - RULE-SET,Telegram,Telegram
  - RULE-SET,YouTube,YouTube
  - RULE-SET,Reject,REJECT
  - 'MATCH, Others'
rule-providers:
  Auto: {type: http, behavior: classical, url: "https://raw.githubusercontent.com/zhangbaoshengrio/my-clash-rules/main/Auto.yml", path: ./ruleset/Auto.yaml, interval: 86400, format: yaml}
  Apple: {type: http, behavior: classical, url: "https://raw.githubusercontent.com/zhangbaoshengrio/my-clash-rules/main/Apple.yml", path: ./ruleset/Apple.yaml, interval: 86400}
  BiliBili: {type: http, behavior: classical, url: "https://raw.githubusercontent.com/zhangbaoshengrio/my-clash-rules/main/BiliBili.yml", path: ./ruleset/BiliBili.yaml, interval: 86400}
  Direct: {type: http, behavior: classical, url: "https://raw.githubusercontent.com/zhangbaoshengrio/my-clash-rules/main/Direct.yml", path: ./ruleset/Direct.yaml, interval: 86400}
  Google: {type: http, behavior: classical, url: "https://raw.githubusercontent.com/zhangbaoshengrio/my-clash-rules/main/Google.yml", path: ./ruleset/Google.yaml, interval: 86400}
  Microsoft: {type: http, behavior: classical, url: "https://raw.githubusercontent.com/zhangbaoshengrio/my-clash-rules/main/Microsoft.yml", path: ./ruleset/Microsoft.yaml, interval: 86400}
  OpenAI: {type: http, behavior: classical, url: "https://raw.githubusercontent.com/zhangbaoshengrio/my-clash-rules/main/OpenAI.yml", path: ./ruleset/OpenAI.yaml, interval: 86400}
  PayPal: {type: http, behavior: classical, url: "https://raw.githubusercontent.com/zhangbaoshengrio/my-clash-rules/main/PayPal.yml", path: ./ruleset/PayPal.yaml, interval: 86400}
  Telegram: {type: http, behavior: classical, url: "https://raw.githubusercontent.com/zhangbaoshengrio/my-clash-rules/main/Telegram.yml", path: ./ruleset/Telegram.yaml, interval: 86400}
  TikTok: {type: http, behavior: classical, url: "https://raw.githubusercontent.com/zhangbaoshengrio/my-clash-rules/main/TikTok.yml", path: ./ruleset/TikTok.yaml, interval: 86400}
  YouTube: {type: http, behavior: classical, url: "https://raw.githubusercontent.com/zhangbaoshengrio/my-clash-rules/main/YouTube.yml", path: ./ruleset/YouTube.yaml, interval: 86400}
  Twitter: {type: http, behavior: classical, url: "https://raw.githubusercontent.com/zhangbaoshengrio/my-clash-rules/main/Twitter.yml", path: ./ruleset/Twitter.yaml, interval: 86400}
  GoogleVoice: {type: http, behavior: classical, url: "https://raw.githubusercontent.com/zhangbaoshengrio/my-clash-rules/main/GoogleVoice.yml", path: ./ruleset/GoogleVoice.yaml, interval: 86400}
  Reject: {type: http, behavior: classical, url: "https://raw.githubusercontent.com/zhangbaoshengrio/my-clash-rules/main/Reject.yml", path: ./ruleset/Reject.yaml, interval: 86400}
  毒奶特供: {type: http, behavior: classical, format: yaml, url: "http://limbopro.xyz/Adblock4limbo.list", path: ./ruleset/limbopro.yaml, interval: 86400}
  野比(AD_Block_Plus): {type: http, behavior: classical, format: text, url: "https://raw.githubusercontent.com/NobyDa/ND-AD/master/QuantumultX/AD_Block_Plus.txt", path: ./ruleset/NobyDa_AD_Plus.yaml, interval: 86400}
  野比(AD_Block): {type: http, behavior: classical, format: text, url: "https://raw.githubusercontent.com/NobyDa/ND-AD/master/QuantumultX/AD_Block.txt", path: ./ruleset/NobyDa_AD.yaml, interval: 86400}
```  
