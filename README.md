
# Для версии Zapret 71.***

## Для установки

- AX3000T плагин 2 файла! [Первый файл](https://www.dropbox.com/scl/fi/htckknbdgclxmai0j03zi/luci-app-zapret_72.20251022-r1_all.ipk?rlkey=h1mmf4uuub97knk747dsn16ix&st=gplhdakw&dl=1) ||| [Второй файл](https://www.dropbox.com/scl/fi/kw99bcigcnirulzke6p92/zapret_72.20251022_aarch64_cortex-a53.ipk?rlkey=rs3a799vla1k5d0yk0of29jls&st=xt6vhiaw&dl=1)
- -----
- 4C плагин 2 файла! [Первый файл](https://www.dropbox.com/scl/fi/28cfg7rcni05bd6joqy3l/luci-app-zapret_72.20251022-r1_all.ipk?rlkey=zum6rfvsi7xb4aka32xk5lggu&st=zhpchk85&dl=1) ||| [Второй файл](https://www.dropbox.com/scl/fi/qut6y8k9j93teis3pbsgl/zapret_72.20251022_mipsel_24kc.ipk?rlkey=fklxvydh8xxcrfvtro23vsxpx&st=e14ot5jb&dl=1)

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
--filter-tcp=443
--hostlist=/opt/zapret/ipset/zapret-hosts-google.txt
--dpi-desync=fake,multidisorder
--dpi-desync-split-seqovl=681
--dpi-desync-split-pos=1
--dpi-desync-fooling=badseq
--dpi-desync-badseq-increment=10000000
--dpi-desync-repeats=2
--dpi-desync-split-seqovl-pattern=/opt/zapret/files/fake/tls_clienthello_www_google_com.bin
--dpi-desync-fake-tls-mod=rnd,dupsid,sni=fonts.google.com
--new
--filter-udp=443
--hostlist=/opt/zapret/ipset/zapret-hosts-google.txt
--dpi-desync=fake
--dpi-desync-repeats=4
--dpi-desync-fake-quic=/opt/zapret/files/fake/quic_initial_www_google_com.bin
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
1187013846746005515.discordsays.com
api.discord.com
api.discordapp.com
attachments.discord.com
attachments.discordapp.net
billing.discord.com
billing.discordapp.com
canary.dl2.discordapp.net
canary.discord.com
canary.discordapp.com
cdn.discord.co
cdn.discord.gg
cdn.discord.media
cdn.discordapp.com
development.dl2.discordapp.net
dis.gd
disboard.org
discord.center
discord.co
discord.com
discord.design
discord.dev
discord.gg
discord.gift
discord.gifts
discord.me
discord.media
discord.new
discord.st
discord.store
discord.tools
discord-activities.com
discordactivities.com
discord-attachments-uploads-prd.storage.googleapis.com
discordapp.com
discordapp.io
discordapp.net
discordbee.com
discordbotlist.com
discordcdn.com
discordexpert.com
discordhome.com
discordhub.com
discordInvites.net
discordlist.me
discordlist.space
discordmerch.com
discordpartygames.com
discords.com
discordsays.com
discordservers.com
discordstatus.com
discordtop.com
disforge.com
dl.discordapp.net
dl2.discordapp.net
dyno.gg
findAdiscord.com
gateway.discord.gg
gateway.discord.media
images.discordapp.net
images-ext-1.discordapp.net
images-ext-2.discordapp.net
images-ext-3.discordapp.net
images-ext-4.discordapp.net
images-ext-5.discordapp.net
media.discord.co
media.discord.gg
media.discordapp.net
mee6.xyz
ptb.dl2.discordapp.net
ptb.discord.com
ptb.discordapp.com
region1.discord.gg
region2.discord.gg
region3.discord.gg
stable.dl2.discordapp.net
status.discord.com
status.discordapp.com
top.gg
updates.discord.com
updates.discordapp.net
upload.discordapp.com
voice.discord.gg
www.discord.com
www.discordapp.com

cdn.telegram.com
chat.telegram.com
comments.app
contest.com
fragment.com
graph.org
mcp.telegram.com
quiz.directory
secure.telegram.com
t.me
tdesktop.com
telega.one
telegra.ph
telegram-cdn.org
telegram.dog
telegram.me
telegram.org
telegram.space
telesco.pe
tg.dev
tx.me
api.telegram.org
core.telegram.org
web.telegram.org
webk.telegram.org
webz.telegram.org
desktop.telegram.org

account.whatsapp.com
api.whatsapp.com
autodiscover.whatsapp.com
b.whatsapp.com
blog.whatsapp.com
business.whatsapp.com
call.whatsapp.com
cdn.whatsapp.net
chat.whatsapp.com
faq.whatsapp.com
graph.whatsapp.com
snr.whatsapp.net
v.whatsapp.com
wa.me
web.whatsapp.com
whatsapp.cc
whatsapp.com
whatsapp.info
whatsapp.net
whatsapp.org
whatsapp.tv
whatsappbrand.com
whatsapp-plus.info
whatsapp-plus.me
whatsapp-plus.net
wl.co
mmg.whatsapp.net
g.whatsapp.net
g-fallback.whatsapp.net
mmx-ds.cdn.whatsapp.net
pps.whatsapp.net
scontent.whatsapp.net
static.whatsapp.net

cdn.youtube.com
fonts.googleapis.com
fonts.gstatic.com
ggpht.com
googleapis.com
googleusercontent.com
i.ytimg.com
i9.ytimg.com
kids.youtube.com
m.youtube.com
manifest.googlevideo.com
music.youtube.com
nhacmp3youtube.com
returnyoutubedislikeapi.com
s.ytimg.com
signaler-pa.youtube.com
storage.googleapis.com
studio.youtube.com
tv.youtube.com
yt3.googleusercontent.com
yting.com
usercontent.dev

```

7. Изменить `zapret-hosts-user.txt`

```
Тут пока нет изменей на всякий случий него от сюда над копировать дальше 8 и 9 пункт выполнить
```
8. Переходим вкладку `service` и перезапускаем
9. Все готов. Если не помогло попробуйте перезагрузить роутер, телефон, смарт тв, компьютер :)
