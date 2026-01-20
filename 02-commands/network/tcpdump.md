# tcpdump

## 常用场景
- 抓包分析
- 网络调试
- 安全审计

## 常用命令
```bash
tcpdump -i eth0
tcpdump port 80
tcpdump -w file.pcap
```

## 常用参数
- -i: 指定网卡
- -w: 保存到文件
- -r: 读取文件
- -n: 不解析域名

## 易错点
- 需要 root 权限
- 抓包可能产生大量数据

## 实战示例
```bash
tcpdump -i eth0 -n port 80
tcpdump -w capture.pcap host 192.168.1.1
```
