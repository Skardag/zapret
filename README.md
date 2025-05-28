FWTYPE= nftables
WS_USER= nobody

NFQWS_PORTS_TCP= 80,443
NFQWS_PORTS_UDP= 443,50000-50099

--filter-tcp=80
--hostlist=/opt/zapret/ipset/zapret-hosts-google.txt
--dpi-desync=fakeddisorder
--dpi-desync-autottl=4
--dpi-desync-repeats=16
--dpi-desync-fooling=md5sig
--new

--filter-tcp=443
--hostlist=/opt/zapret/ipset/zapret-hosts-google.txt
--dpi-desync=fakeddisorder
--dpi-desync-repeats=16
--dpi-desync-fooling=md5sig
--dpi-desync-cutoff=d3
--new

--filter-udp=443
--hostlist=/opt/zapret/ipset/zapret-hosts-google.txt
--dpi-desync=fake
--dpi-desync-repeats=16
--dpi-desync-any-protocol
--dpi-desync-fake-quic=/opt/zapret/files/fake/quic_initial_www_google_com.bin
--new

--filter-tcp=80
--hostlist=/opt/zapret/ipset/zapret-hosts-user.txt
--dpi-desync=fakedsplit
--dpi-desync-split-pos=1,midsld
--dpi-desync-autottl=4
--dpi-desync-repeats=16
--new

--filter-tcp=443
--hostlist=/opt/zapret/ipset/zapret-hosts-user.txt
--dpi-desync=fakedsplit
--dpi-desync-split-pos=1,midsld
--dpi-desync-autottl=4
--dpi-desync-repeats=16
--dpi-desync-fake-tls-mod=padencap
--dpi-desync-fake-tls=/opt/zapret/files/fake/tls_clienthello_www_google_com.bin
--new

--filter-udp=443
--hostlist=/opt/zapret/ipset/zapret-hosts-user.txt
--dpi-desync=fake
--dpi-desync-repeats=16
--dpi-desync-any-protocol
--dpi-desync-fake-quic=/opt/zapret/files/fake/quic_initial_www_google_com.bin
--new

--filter-tcp=80
--hostlist=/opt/zapret/ipset/cust1.txt
--dpi-desync=fakedsplit
--dpi-desync-split-pos=1,midsld
--dpi-desync-autottl=4
--dpi-desync-repeats=16
--new

--filter-tcp=443
--hostlist=/opt/zapret/ipset/cust1.txt
--dpi-desync=fakedsplit
--dpi-desync-split-pos=1,midsld
--dpi-desync-autottl=4
--dpi-desync-fake-tls-mod=padencap
--dpi-desync-fake-tls=/opt/zapret/files/fake/tls_clienthello_www_google_com.bin
--dpi-desync-repeats=16
--new

--filter-udp=443
--hostlist=/opt/zapret/ipset/cust1.txt
--dpi-desync=fake
--dpi-desync-repeats=16
--dpi-desync-any-protocol
--dpi-desync-fake-quic=/opt/zapret/files/fake/quic_initial_www_google_com.bin
--new

--filter-tcp=80
--hostlist=/opt/zapret/ipset/cust2.txt
--dpi-desync=fakedsplit
--dpi-desync-split-pos=1,midsld
--dpi-desync-autottl=4
--dpi-desync-repeats=16
--new

--filter-tcp=443
--hostlist=/opt/zapret/ipset/cust2.txt
--dpi-desync=fakedsplit
--dpi-desync-split-pos=1,midsld
--dpi-desync-autottl=4
--dpi-desync-fake-tls-mod=padencap
--dpi-desync-fake-tls=/opt/zapret/files/fake/tls_clienthello_www_google_com.bin
--dpi-desync-repeats=16
--new

--filter-udp=443
--hostlist=/opt/zapret/ipset/cust2.txt
--dpi-desync=fake
--dpi-desync-repeats=16
--dpi-desync-any-protocol
--dpi-desync-fake-quic=/opt/zapret/files/fake/quic_initial_www_google_com.bin
--new

--filter-udp=50000-50099
--filter-l7=discord,stun
--dpi-desync=fake
--dpi-desync-repeats=16
--new
