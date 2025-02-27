## [[Linux]] [[PVE]] [[compress and extract]]

取得PVE運行資訊
pvesh get /cluster/resources

pvesh get /nodes/pve/qemu/101/status/stop

101->替換要關閉的ip  然後這個指令要在純shell才有用 不能在網頁版下

配置PVE網路配置指令
識別主機板管理網口（如eno1)  
通常跟多網卡網口長的不一樣
同一張網卡的的網口名稱會長的類似(如enp1s0f0 enp1s0f1 ...etc)

WAN也可改成指定的網口
nano /etc/network/interfaces

改界面ip
nano /etc/issue

重新配置完後 要重新啟動PVE


