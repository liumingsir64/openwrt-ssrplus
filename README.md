#openwrt-ssrplus
方法 3 - 将此存储库添加为 OpenWrt 源
添加新源：

sed -i "/helloworld/d" "feeds.conf.default"
echo "src-git helloworld https://github.com/fw876/helloworld.git" >> "feeds.conf.default"
拉取上游提交：

./scripts/feeds update helloworld
./scripts/feeds install -a -f -p helloworld
删除

sed -i "/helloworld/d" "feeds.conf.default"
./scripts/feeds clean
./scripts/feeds update -a
./scripts/feeds install -a
mkdir -p package/helloworld
for i in "dns2socks" "microsocks" "ipt2socks" "pdnsd-alt" "redsocks2"; do \
  svn checkout "https://github.com/immortalwrt/packages/trunk/net/$i" "package/helloworld/$i"; \
done
