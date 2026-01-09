## 这个规则集
 - RULE-SET,Google,Google #中间的都是规则集,后面的这个是策略组名称,策略组名称就是proxy-groups里面的



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
