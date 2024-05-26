## clash-rule
online clash rule cache

## clash rule 语法规则
> 通常以YAML格式编写，每条规则由条件列表、值、动作组成，条件列表用逗号分隔

    1. 条件类型
        . DOMAIN-SUFFIX：域名后缀匹配
        . DOMAIN-KEYWORD：域名关键字匹配
        . DOMAIN：域名匹配
        . GEOIP：基于 IP 地址的地理位置匹配
        . IP-CIDR：IP 地址范围匹配
        . IP-CIDR6：IPv6 地址范围匹配
        . SRC-IP-CIDR：源 IP 地址范围匹配
        . SRC-PORT：源端口匹配
        . DEST-PORT：目标端口匹配
        . PROCESS-NAME：基于进程名称匹配
        . PROCESS-PATH：基于进程路径匹配
        . IP-SET：基于 IP 集合匹配
        . RULE-SET：基于三方规则集（rule-providers）匹配
        . SCRIPT：基于脚本匹配z`
        . MATCH：自定义匹配（通常与其他工具或脚本结合使用）
    2. 动作类型
        . REJECT：拒绝请求，不发送流量
        . DIRECT：直接发送流量，不使用代理
        . [PROXY/PROXYGROUP]：将流量发送到指定的代理服务器
    3. 其他规则
        . 顺序规则：匹配规则按照顺序进行匹配，一旦找到匹配的规则，就会执行相应的动作，并且不再检查后续规则
        . 排除条件：可以使用!符号来排除某些条件
        . 通配符和正则表达式：在某些条件下，可以使用通配符（如*）或正则表达式进行更复杂的匹配
    4. Rule Providers配置
        rule-providers:
            [provider_name]:
            type: http
            behavior: classical
            url: "https://cdn.jsdelivr.net/gh/Loyalsoldier/clash-rules@release/reject.txt"
            path: ./ruleset/[provider_name].yaml
            interval: 864000
        
## rule 示例
```yml
payload:
  - DOMAIN-SUFFIX,example.com,PROXY
  - DOMAIN-KEYWORD,example,PROXY
  - GEOIP,CN,DIRECT
  - IP-CIDR,192.168.0.0/16,DIRECT
  - MATCH,PROXY
```

