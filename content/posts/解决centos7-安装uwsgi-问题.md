---
title: 解决centos7 安装uwsgi 问题.md
date: 2019-12-24 20:05:28
tags:
- Python
- CentOS
---
部署环境真的是特别麻烦，写完了一个 Django 项目之后想部署一下，跟着教程来结果总是出错，
后面在群里问了一下，终于把这个问腿解决了，现在总结一下经验。
## 环境
Centos7
Python3.6.8

### 报错详情
执行
```
pip3 install uwsgi
```
爆出错误
```
[root@study sanyue]# pip3 install uwsgi
WARNING: Running pip install with root privileges is generally not a good idea. Try `pip3 install --user` instead.
Collecting uwsgi
  Using cached https://files.pythonhosted.org/packages/e7/1e/3dcca007f974fe4eb369bf1b8629d5e342bb3055e2001b2e5340aaefae7a/uwsgi-2.0.18.tar.gz
Installing collected packages: uwsgi
  Running setup.py install for uwsgi ... error
    Complete output from command /usr/bin/python3 -u -c "import setuptools, tokenize;__file__='/tmp/pip-build-1l3owc8n/uwsgi/setup.py';f=getattr(tokenize, 'open', open)(__file__);code=f.read().replace('\r\n', '\n');f.close();exec(compile(code, __file__, 'exec'))" install --record /tmp/pip-cbse3bta-record/install-record.txt --single-version-externally-managed --compile:
    /usr/lib64/python3.6/distutils/dist.py:261: UserWarning: Unknown distribution option: 'descriptions'
      warnings.warn(msg)
    running install
    using profile: buildconf/default.ini
    detected include path: ['/usr/include', '/usr/local/include']
    Patching "bin_name" to properly install_scripts dir
    detected CPU cores: 1
    configured CFLAGS: -O2 -I. -Wall -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -Wextra -Wno-unused-parameter -Wno-missing-field-initializers -Wno-format -Wno-format-security -DUWSGI_HAS_IFADDRS -DUWSGI_LOCK_USE_MUTEX -DUWSGI_EVENT_USE_EPOLL -DUWSGI_EVENT_TIMER_USE_TIMERFD -DUWSGI_EVENT_FILEMONITOR_USE_INOTIFY -DUWSGI_VERSION="\"2.0.18\"" -DUWSGI_VERSION_BASE="2" -DUWSGI_VERSION_MAJOR="0" -DUWSGI_VERSION_MINOR="18" -DUWSGI_VERSION_REVISION="0" -DUWSGI_VERSION_CUSTOM="\"\"" -DUWSGI_YAML -DUWSGI_PLUGIN_DIR="\".\"" -DUWSGI_DECLARE_EMBEDDED_PLUGINS="UDEP(python);UDEP(gevent);UDEP(ping);UDEP(cache);UDEP(nagios);UDEP(rrdtool);UDEP(carbon);UDEP(rpc);UDEP(corerouter);UDEP(fastrouter);UDEP(http);UDEP(ugreen);UDEP(signal);UDEP(syslog);UDEP(rsyslog);UDEP(logsocket);UDEP(router_uwsgi);UDEP(router_redirect);UDEP(router_basicauth);UDEP(zergpool);UDEP(redislog);UDEP(mongodblog);UDEP(router_rewrite);UDEP(router_http);UDEP(logfile);UDEP(router_cache);UDEP(rawrouter);UDEP(router_static);UDEP(sslrouter);UDEP(spooler);UDEP(cheaper_busyness);UDEP(symcall);UDEP(transformation_tofile);UDEP(transformation_gzip);UDEP(transformation_chunked);UDEP(transformation_offload);UDEP(router_memcached);UDEP(router_redis);UDEP(router_hash);UDEP(router_expires);UDEP(router_metrics);UDEP(transformation_template);UDEP(stats_pusher_socket);" -DUWSGI_LOAD_EMBEDDED_PLUGINS="ULEP(python);ULEP(gevent);ULEP(ping);ULEP(cache);ULEP(nagios);ULEP(rrdtool);ULEP(carbon);ULEP(rpc);ULEP(corerouter);ULEP(fastrouter);ULEP(http);ULEP(ugreen);ULEP(signal);ULEP(syslog);ULEP(rsyslog);ULEP(logsocket);ULEP(router_uwsgi);ULEP(router_redirect);ULEP(router_basicauth);ULEP(zergpool);ULEP(redislog);ULEP(mongodblog);ULEP(router_rewrite);ULEP(router_http);ULEP(logfile);ULEP(router_cache);ULEP(rawrouter);ULEP(router_static);ULEP(sslrouter);ULEP(spooler);ULEP(cheaper_busyness);ULEP(symcall);ULEP(transformation_tofile);ULEP(transformation_gzip);ULEP(transformation_chunked);ULEP(transformation_offload);ULEP(router_memcached);ULEP(router_redis);ULEP(router_hash);ULEP(router_expires);ULEP(router_metrics);ULEP(transformation_template);ULEP(stats_pusher_socket);"
    *** uWSGI compiling server core ***
    [gcc -pthread] core/utils.o
    [gcc -pthread] core/protocol.o
    [gcc -pthread] core/socket.o
    [gcc -pthread] core/logging.o
    [gcc -pthread] core/master.o
    [gcc -pthread] core/master_utils.o
    [gcc -pthread] core/emperor.o
    [gcc -pthread] core/notify.o
    [gcc -pthread] core/mule.o
    [gcc -pthread] core/subscription.o
    [gcc -pthread] core/stats.o
    [gcc -pthread] core/sendfile.o
    [gcc -pthread] core/async.o
    [gcc -pthread] core/master_checks.o
    [gcc -pthread] core/fifo.o
    [gcc -pthread] core/offload.o
    [gcc -pthread] core/io.o
    [gcc -pthread] core/static.o
    [gcc -pthread] core/websockets.o
    [gcc -pthread] core/spooler.o
    [gcc -pthread] core/snmp.o
    [gcc -pthread] core/exceptions.o
    [gcc -pthread] core/config.o
    [gcc -pthread] core/setup_utils.o
    [gcc -pthread] core/clock.o
    [gcc -pthread] core/init.o
    [gcc -pthread] core/buffer.o
    [gcc -pthread] core/reader.o
    [gcc -pthread] core/writer.o
    [gcc -pthread] core/alarm.o
    [gcc -pthread] core/cron.o
    [gcc -pthread] core/hooks.o
    [gcc -pthread] core/plugins.o
    [gcc -pthread] core/lock.o
    [gcc -pthread] core/cache.o
    [gcc -pthread] core/daemons.o
    [gcc -pthread] core/errors.o
    [gcc -pthread] core/hash.o
    [gcc -pthread] core/master_events.o
    [gcc -pthread] core/chunked.o
    [gcc -pthread] core/queue.o
    [gcc -pthread] core/event.o
    [gcc -pthread] core/signal.o
    [gcc -pthread] core/strings.o
    [gcc -pthread] core/progress.o
    [gcc -pthread] core/timebomb.o
    [gcc -pthread] core/ini.o
    [gcc -pthread] core/fsmon.o
    [gcc -pthread] core/mount.o
    [gcc -pthread] core/metrics.o
    [gcc -pthread] core/plugins_builder.o
    [gcc -pthread] core/sharedarea.o
    [gcc -pthread] core/rpc.o
    [gcc -pthread] core/gateway.o
    [gcc -pthread] core/loop.o
    [gcc -pthread] core/cookie.o
    [gcc -pthread] core/querystring.o
    [gcc -pthread] core/rb_timers.o
    [gcc -pthread] core/transformations.o
    [gcc -pthread] core/uwsgi.o
    [gcc -pthread] proto/base.o
    [gcc -pthread] proto/uwsgi.o
    [gcc -pthread] proto/http.o
    [gcc -pthread] proto/fastcgi.o
    [gcc -pthread] proto/scgi.o
    [gcc -pthread] proto/puwsgi.o
    [gcc -pthread] lib/linux_ns.o
    [gcc -pthread] core/yaml.o
    [gcc -pthread] core/dot_h.o
    [gcc -pthread] core/config_py.o
    *** uWSGI compiling embedded plugins ***
    [gcc -pthread] plugins/python/python_plugin.o
    In file included from plugins/python/python_plugin.c:1:0:
    plugins/python/uwsgi_python.h:2:20: 致命错误：Python.h：没有那个文件或目录
     #include <Python.h>
                        ^
    编译中断。

    ----------------------------------------
Command "/usr/bin/python3 -u -c "import setuptools, tokenize;__file__='/tmp/pip-build-1l3owc8n/uwsgi/setup.py';f=getattr(tokenize, 'open', open)(__file__);code=f.read().replace('\r\n', '\n');f.close();exec(compile(code, __file__, 'exec'))" install --record /tmp/pip-cbse3bta-record/install-record.txt --single-version-externally-managed --compile" failed with error code 1 in /tmp/pip-build-1l3owc8n/uwsgi/
```
### 解决方法
原因是没有安装python dev的标头文件和静态库

执行安装
```
yum install python3-devel
```
后面安装完全无任何问题，感谢
### 参考链接
[https://stackoverflow.com/questions/21530577/fatal-error-python-h-no-such-file-or-directory](https://stackoverflow.com/questions/21530577/fatal-error-python-h-no-such-file-or-directory)
