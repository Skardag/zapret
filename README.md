
# Для версии Zapret 71.***

## Для установки

- AX3000T плагин 2 файла! [Первый файл](https://www.dropbox.com/scl/fi/ft2aro8o2mlc9nn1843ev/zapret_71.20250708_aarch64_cortex-a53.ipk?rlkey=0luxx1s6vei1jxjlutca61ncv&st=znpaobyf&dl=1) ||| [Второй файл](https://www.dropbox.com/scl/fi/bxpx4lgkpve7ponhh9m2s/luci-app-zapret_71.20250708-r1_all.ipk?rlkey=2lx2axrjnylcpqyklktv9lzz8&st=ep7zlrts&dl=1)
- -----
- 4C плагин 2 файла! [Первый файл](https://www.dropbox.com/scl/fi/u7n8y6c6dwz0jlhxurx1e/zapret_71.20250708_mipsel_24kc.ipk?rlkey=isnc7knzab6d2c5e9b8uckz3i&st=v1vmjwui&dl=1) ||| [Второй файл](https://www.dropbox.com/scl/fi/3azom96ktzmdgaxpdn0zs/luci-app-zapret_71.20250708-r1_all.ipk?rlkey=icq3vsz598shvvotelvabib13&st=tqkbe1vp&dl=1)

____
### Заходим по адресу

+ AX3000T [192.168.32.1](http://192.168.32.1)
+ 4C [192.168.31.1](http://192.168.31.1)
+ У вас возможно другой адрес зависит того кто прошивал 

NFQWS_PORTS_TCP = 80,443<br>
NFQWS_PORTS_UDP = 443<br>
MODE_FILTER = hostlist<br>

1. Заходим раздел `Службы` > `Zapret`
2. Переходим вкладку `Настройки` > `NFQWS options`
3. Изменить `NFQWS_OPT` удаляем то что есть
4. Вставляем текст который ниже копируйте вставте в NFQWS_OPT

```
--filter-tcp=80 <HOSTLIST>
--dpi-desync=fake,fakedsplit
--dpi-desync-autottl=2
--dpi-desync-fooling=badsum

--new
--filter-tcp=443
--hostlist=/opt/zapret/ipset/zapret-hosts-google.txt
--dpi-desync=fake,multidisorder
--dpi-desync-split-pos=1,midsld
--dpi-desync-repeats=11
--dpi-desync-fooling=badsum
--dpi-desync-fake-tls-mod=rnd,dupsid,sni=www.google.com

--new
--filter-udp=443
--hostlist=/opt/zapret/ipset/zapret-hosts-google.txt
--dpi-desync=fake
--dpi-desync-repeats=11
--dpi-desync-fake-quic=/opt/zapret/files/fake/quic_initial_www_google_com.bin

--new
--filter-udp=443 <HOSTLIST_NOAUTO>
--dpi-desync=fake
--dpi-desync-repeats=11

--new
--filter-tcp=443 <HOSTLIST>
--dpi-desync=multidisorder
--dpi-desync-split-pos=1,sniext+1,host+1,midsld-2,midsld,midsld+2,endhost-1
```

5. Переходим вкладку `Настройки` > `Host list`
6. Изменить `zapret-hosts-google.txt`

```
googlevideo.com
youtubei.googleapis.com
ytimg.com
yt3.ggpht.com
yt4.ggpht.com
youtube.com
youtubeembeddedplayer.googleapis.com
ytimg.l.google.com
jnn-pa.googleapis.com
youtube-nocookie.com
youtube-ui.l.google.com
yt-video-upload.l.google.com
wide-youtube.l.google.com
yt.be
youtubegaming.com
youtubeeducation.com
youtu.be
ggpht.com
l.google.com
play.google.com
nhacmp3youtube.com
googleusercontent.com
i.ytimg.com
i9.ytimg.com
youtube.googleapis.com
yt3.googleusercontent.com
medium.com
google.com
gstatic.com
google-analytics.com
googleapis.com
doubleclick.net
googletagmanager.com
dl.google.com
dl-ssl.google.com
android.clients.google.com
googleplay.com
play-fe.googleapis.com
play-games.googleusercontent.com
play-lh.googleusercontent.com
play.googleapis.com
xn--ngstr-lra8j.com
s.youtube.com
android.com
gvt1.com
gvt2.com
gvt3.com
```

7. Изменить `zapret-hosts-user.txt`

```
royal-match.top
royalmatch.fandom.com
fandom.com
openwrt.org
cloudflare.com
www.cloudflare.com
cdninstagram.com
ig.me
z-p42-chat-e2ee-ig.facebook.com
scontent.cdninstagram.com
api.instagram.com
i.instagram.com
graph.instagram.com
instagram.c10r.instagram.com
gateway.instagram.com
www.instagram.com
i-fallback.instagram.com
z-p42-instagram.c10r.instagram.com
graph-fallback.instagram.com
star.fallback.c10r.instagram.com
edge-chat.instagram.com
b.i.instagram.com
platform.instagram.com
l.instagram.com
instagram.com
web-chat-e2ee.instagram.com
iglite-z.instagram.com
lookaside.instagram.com
api.instagram.com
b-fallback.i.instagram.com
help.instagram.com
b.secure.instagram.com
iglite-p42.c10r.instagram.com
iglite-d.instagram.com
accountscenter.instagram.com
applink.instagram.com
include:instagram-ads
achat-followers-instagram.com
acheter-followers-instagram.com
acheterdesfollowersinstagram.com
acheterfollowersinstagram.com
bookstagram.com
carstagram.com
chickstagram.com
igcdn.com
igsonar.com
igtv.com
imstagram.com
imtagram.com
instaadder.com
instachecker.com
instafallow.com
instafollower.com
instagainer.com
instagda.com
instagify.com
instagmania.com
instagor.com
instagram-brand.com
instagram-engineering.com
instagram-help.com
instagram-press.com
instagram-press.net
instagramci.com
instagramcn.com
instagramdi.com
instagramhashtags.net
instagramhilecim.com
instagramhilesi.org
instagramium.com
instagramizlenme.com
instagramkusu.com
instagramlogin.com
instagramm.com
instagramn.com
instagrampartners.com
instagramphoto.com
instagramq.com
instagramsepeti.com
instagramtakipcisatinal.net
instagramtakiphilesi.com
instagramtips.com
instagramtr.com
instagran.com
instagranm.com
instagrem.com
instagrm.com
instagtram.com
instagy.com
instamgram.com
instangram.com
instanttelegram.com
instaplayer.net
instastyle.tv
instgram.com
intagram.com
intagrm.com
intgram.com
kingstagram.com
lnstagram-help.com
theinstagramhack.com
oninstagram.com
online-instagram.com
onlineinstagram.com
web-instagram.net
wwwinstagram.com
facebook.com
facebook.net
fbcdn.net
fbstatic-a.akamaihd.net
fbstatic-b.akamaihd.net
fbstatic-c.akamaihd.net
fbstatic-d.akamaihd.net
fbstatic-e.akamaihd.net
fbstatic-f.akamaihd.net
fbstatic-g.akamaihd.net
fbstatic-h.akamaihd.net
fbstatic-i.akamaihd.net
fbstatic-j.akamaihd.net
fbstatic-k.akamaihd.net
fbstatic-l.akamaihd.net
fbstatic-m.akamaihd.net
fbstatic-n.akamaihd.net
fbstatic-o.akamaihd.net
fbstatic-p.akamaihd.net
fbstatic-q.akamaihd.net
fbstatic-r.akamaihd.net
fbstatic-s.akamaihd.net
fbstatic-t.akamaihd.net
fbstatic-u.akamaihd.net
fbstatic-v.akamaihd.net
fbstatic-w.akamaihd.net
fbstatic-x.akamaihd.net
fbstatic-y.akamaihd.net
fbstatic-z.akamaihd.net
fbcdn-profile-a.akamaihd.net
fbcdn-profile-b.akamaihd.net
fbcdn-profile-c.akamaihd.net
fbcdn-profile-d.akamaihd.net
fbcdn-profile-e.akamaihd.net
fbcdn-profile-f.akamaihd.net
fbcdn-profile-g.akamaihd.net
fbcdn-profile-h.akamaihd.net
fbcdn-profile-i.akamaihd.net
fbcdn-profile-j.akamaihd.net
fbcdn-profile-k.akamaihd.net
fbcdn-profile-l.akamaihd.net
fbcdn-profile-m.akamaihd.net
fbcdn-profile-n.akamaihd.net
fbcdn-profile-o.akamaihd.net
fbcdn-profile-p.akamaihd.net
fbcdn-profile-q.akamaihd.net
fbcdn-profile-r.akamaihd.net
fbcdn-profile-s.akamaihd.net
fbcdn-profile-t.akamaihd.net
fbcdn-profile-u.akamaihd.net
fbcdn-profile-v.akamaihd.net
fbcdn-profile-w.akamaihd.net
fbcdn-profile-x.akamaihd.net
fbcdn-profile-y.akamaihd.net
fbcdn-profile-z.akamaihd.net
fbcdn-sphotos-a-a.akamaihd.net
fbcdn-sphotos-b-a.akamaihd.net
fbcdn-sphotos-c-a.akamaihd.net
fbcdn-sphotos-d-a.akamaihd.net
fbcdn-sphotos-e-a.akamaihd.net
fbcdn-sphotos-f-a.akamaihd.net
fbcdn-sphotos-g-a.akamaihd.net
fbcdn-sphotos-h-a.akamaihd.net
fbcdn-sphotos-i-a.akamaihd.net
fbcdn-sphotos-j-a.akamaihd.net
fbcdn-sphotos-k-a.akamaihd.net
fbcdn-sphotos-l-a.akamaihd.net
fbcdn-sphotos-m-a.akamaihd.net
fbcdn-sphotos-n-a.akamaihd.net
fbcdn-sphotos-o-a.akamaihd.net
fbcdn-sphotos-p-a.akamaihd.net
fbcdn-sphotos-q-a.akamaihd.net
fbcdn-sphotos-r-a.akamaihd.net
fbcdn-sphotos-s-a.akamaihd.net
fbcdn-sphotos-t-a.akamaihd.net
fbcdn-sphotos-u-a.akamaihd.net
fbcdn-sphotos-v-a.akamaihd.net
fbcdn-sphotos-w-a.akamaihd.net
fbcdn-sphotos-x-a.akamaihd.net
fbcdn-sphotos-y-a.akamaihd.net
fbcdn-sphotos-z-a.akamaihd.net
fbcdn-creative-a.akamaihd.net
fbcdn-creative-b.akamaihd.net
fbcdn-creative-c.akamaihd.net
fbcdn-creative-d.akamaihd.net
fbcdn-creative-e.akamaihd.net
fbcdn-creative-f.akamaihd.net
fbcdn-creative-g.akamaihd.net
fbcdn-creative-h.akamaihd.net
fbcdn-creative-i.akamaihd.net
fbcdn-creative-j.akamaihd.net
fbcdn-creative-k.akamaihd.net
fbcdn-creative-l.akamaihd.net
fbcdn-creative-m.akamaihd.net
fbcdn-creative-n.akamaihd.net
fbcdn-creative-o.akamaihd.net
fbcdn-creative-p.akamaihd.net
fbcdn-creative-q.akamaihd.net
fbcdn-creative-r.akamaihd.net
fbcdn-creative-s.akamaihd.net
fbcdn-creative-t.akamaihd.net
fbcdn-creative-u.akamaihd.net
fbcdn-creative-v.akamaihd.net
fbcdn-creative-w.akamaihd.net
fbcdn-creative-x.akamaihd.net
fbcdn-creative-y.akamaihd.net
fbcdn-creative-z.akamaihd.net
fbexternal-a.akamaihd.net
fbexternal-b.akamaihd.net
fbexternal-c.akamaihd.net
fbexternal-d.akamaihd.net
fbexternal-e.akamaihd.net
fbexternal-f.akamaihd.net
fbexternal-g.akamaihd.net
fbexternal-h.akamaihd.net
fbexternal-i.akamaihd.net
fbexternal-j.akamaihd.net
fbexternal-k.akamaihd.net
fbexternal-l.akamaihd.net
fbexternal-m.akamaihd.net
fbexternal-n.akamaihd.net
fbexternal-o.akamaihd.net
fbexternal-p.akamaihd.net
fbexternal-q.akamaihd.net
fbexternal-r.akamaihd.net
fbexternal-s.akamaihd.net
fbexternal-t.akamaihd.net
fbexternal-u.akamaihd.net
fbexternal-v.akamaihd.net
fbexternal-w.akamaihd.net
fbexternal-x.akamaihd.net
fbexternal-y.akamaihd.net
fbexternal-z.akamaihd.net
argotunnel.com
cfargotunnel.com
cfl.re
cloudflare-dns.com
cloudflare-ech.com
cloudflare-esni.com
cloudflare-gateway.com
cloudflare-quic.com
cloudflare.com
cloudflare.net
cloudflare.tv
cloudflareaccess.com
cloudflareapps.com
cloudflarebolt.com
cloudflareclient.com
cloudflareinsights.com
cloudflareok.com
cloudflarepartners.com
cloudflareportal.com
cloudflarepreview.com
cloudflareresolve.com
cloudflaressl.com
cloudflarestatus.com
cloudflarestorage.com
cloudflarestream.com
cloudflaretest.com
cloudflarewarp.com
every1dns.net
isbgpsafeyet.com
one.one.one
pacloudflare.com
pages.dev
trycloudflare.com
videodelivery.net
warp.plus
workers.dev
cf-ns.com 
cf-ns.net 
cf-ns.site 
cf-ns.tech 
cftest5.cn 
cftest6.cn 
cftest7.com 
cftest8.com 
cloudflare-cn.com 
cloudflareanycast.net 
cloudflarechina.cn 
cloudflarecn.net 
cloudflareglobal.net 
cloudflareinsights-cn.com 
cloudflareperf.com 
cloudflareprod.com 
cloudflarestaging.com 
cloudflarestoragegw.com
```
5. Переходим вкладку `service` и перезапускаем
6. Все готов. Если не помогло попробуйте перезагрузить роутер, телефон, смарт тв, компьютер :)
