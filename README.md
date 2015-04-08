Nginx Xml Distributing Upstream Module
=========================

This Nginx upstream module based on post content. Designed for wechat.  

This module is open sourced under the same license as Nginx.  

You could read doc/doc.txt and following installation guide.

You should also be familiar with wechat development.
If not, you could learn it at [mp.weixin.qq.com](https://mp.weixin.qq.com).

Installation
---------------------------
Installation Instruction: (Tested in ubuntu 14.04)
* First, you must have `libxml`, `pcre` and `zlib` installed. If not, you need:  
  `sudo apt-get install libxml2-dev libpcre3-dev zlib1g-dev`
* Add a soft link: `sudo ln -s libxml2/libxml /usr/include/libxml`

And you need to use 1.6.x nginx with the module. Other nginx may not work.
You can get nginx by:  
`wget http://nginx.org/download/nginx-1.6.3.tar.gz &&tar xzf nginx-1.6.3.tar.gz`

Says the nginx source folder is `./nginx-1.6.3`, then you should modify nginx:
* First go to `nginx-1.6.3` folder.
* `cp -af ../src/ngx_http_upstream.h src/http/`
* `sed -i 's/.*-Werror.*//g' gcc`. If not, after `./configure`,
  you can also go to `nginx-1.6.3/objs/Makefile`, delete `-Werror` in line 2.

Compile:
* First go to `nginx-1.6.3` folder.
* Execute `./configure --add-module=../src --prefix=/usr/local/nginxXml`
* Then, Return to `nginx-1.6.3` folder, `make && sudo make install`.
* You could find `nginx` in `/usr/local/nginxXml`

We give `doc/nginx.conf` as an example.
The `ticketups` in `upstream test` block is what you need to write.
You could use regular expression in xml body to match each server.  
You could use re in `Content, MsgType, CreateTime, FromUserName` and so on.
If the message couldn't be matched by any server, it's sent to the last server.


Thanks
-----------------------------------------------
Thanks for Evan Miller's tutorial and upstream hash module.
Many of my source code comes from that module.


Thanks for developer of libxml and pcre.

Thanks for Liuqiang teacher, Chen Huarong, Jiang Linnan, Gong Dahan,
Yu Zeming and all of my other classmates.

Thanks for open source!
