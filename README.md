# learn_nginx
Tips about how to use nginx

## nginx 中，超时时间的默认单位
A value without a suffix means seconds.
http://nginx.org/en/docs/syntax.html

## nginx 中，websocket对应的设置
/etc/nginx/default.d/websocket.conf

proxy_read_timeout		259200000;
proxy_send_timeout		259200000;
proxy_connect_timeout		86400000;

location /ws {
	proxy_pass		http://localhost:8010/;
	proxy_http_version	1.1;
	proxy_set_header	Upgrade $http_upgrade;
	proxy_set_header	Connection "Upgrade";
	proxy_set_header	Host $host;
}
