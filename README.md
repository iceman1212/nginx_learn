# nginx_learn #
>error_log   /dev/null;  丢弃日志  
client_max_body_size  上传文件大小限制 
client_max_body_size          50m; //文件大小限制，默认1m  
client_header_timeout         1m;  
client_body_timeout           1m;  
proxy_connect_timeout         60s;  
proxy_read_timeout            1m;  
proxy_send_timeout            1m;

## Nginx提供了很多内置的变量,如:  
>$arg_PARAMETER 这个变量包含在查询字符串时GET请求PARAMETER的值。  
$args 这个变量等于请求行中的参数。  
$binary_remote_addr 二进制码形式的客户端地址。  
$body_bytes_sent 传送页面的字节数  
$content_length 请求头中的Content-length字段。  
$content_type 请求头中的Content-Type字段。  
$cookie_COOKIE cookie COOKIE的值。  
$document_root 当前请求在root指令中指定的值。  
$document_uri 与$uri相同。  
$host 请求中的主机头字段，如果请求中的主机头不可用，则为服务器处理请求的服务器名称。  
$is_args 如果$args设置，值为"?"，否则为""。  
$limit_rate 这个变量可以限制连接速率。  
$nginx_version 当前运行的nginx版本号。  
$query_string 与$args相同。  
$remote_addr 客户端的IP地址。    
$remote_port 客户端的端口。  
$remote_user 已经经过Auth Basic Module验证的用户名。    
$request_filename 当前连接请求的文件路径，由root或alias指令与URI请求生成。  
$request_body 这个变量（0.7.58+）包含请求的主要信息。在使用proxy_pass或fastcgi_pass指令的location中比较有意义。  
$request_body_file 客户端请求主体信息的临时文件名。  
$request_completion 未知。  
$request_method 这个变量是客户端请求的动作，通常为GET或POST。包括0.8.20及之前的版本中，这个变量总为main   request中的动作，如果当前请求是一个子请求，并不使用这个当前请求的动作。  
$request_uri 这个变量等于包含一些客户端请求参数的原始URI，它无法修改，请查看$uri更改或重写URI。  
$scheme 所用的协议，比如http或者是https，比如rewrite ^(.+)$ $scheme://example.com$1 redirect;  
$server_addr 服务器地址，在完成一次系统调用后可以确定这个值，如果要绕开系统调用，则必须在listen中指定地址并且使用bind参数。  
$server_name 服务器名称。  
$server_port 请求到达服务器的端口号。  
$server_protocol 请求使用的协议，通常是HTTP/1.0或HTTP/1.1。  
$uri 请求中的当前URI(不带请求参数，参数位于$args)，可以不同于浏览器传递的$request_uri的值，它可以通过内部重定向，或者使用index指令进行修改。  
另外： HTTP_X_FORWARDED_FOR是透过代理服务器取得客户端的真实IP地址，有些用此方法读取到的仍然是代理服务器的IP。还有一点需要注意的是：如果客户端没有通过代理服务器来访问，那么用 HTTP_X_FORWARDED_FOR 取到的值将是空的。

## nginx_lua
>./configure   --with-ld-opt="-Wl,-E -lpthread -lcrypt -llua -lm -lpcre -lz -ldl" --add-module=../ngx_devel_kit-0.2.19 --add-module=../lua-nginx-module-0.9.19 && make && make install  
