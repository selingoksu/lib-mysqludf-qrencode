**Dependencies**:

  * [libpng](http://www.libpng.org/pub/png/libpng.html)
  * [libqrencode](http://fukuchi.org/works/qrencode/index.en.html)

**To compile:**
```
   gcc -shared -o lib_mysqludf_qrencode.so lib_mysqludf_qrencode.c $(mysql_config --cflags)\
	  -lpng -lqrencode -DMYSQL_DYNAMIC_PLUGIN
```

**To register these functions:**

_at mysql commandline prompt, type:__```
   CREATE FUNCTION qrencode RETURNS STRING SONAME 'lib_mysqludf_qrencode.so';
   CREATE FUNCTION qrencode_info RETURNS STRING SONAME 'lib_mysqludf_qrencode.so';
```_

**To get rid of the functions:**

_at mysql commandline prompt, type:__```
   DROP FUNCTION qrcode;
   DROP FUNCTION qrcode_info;
```_

**To list all installed functions:**

_at mysql commandline prompt, type:__```
   SELECT  FROM mysql.func;
```_

**Note:**

If you have permission problems installing function:

  1. `sudo vi /etc/apparmor.d/usr.sbin.mysqld`
  1. _add the path:  /usr/lib/mysql/plugin_
  1. `sudo /etc/init.d/apparmor restart`

