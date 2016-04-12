**A Simple python script showing how to use MySQL UDF qrencode function**

```
#!/usr/bin/python
# -*- coding: utf-8 -*-

import MySQLdb as mdb 
import sys

try:
    conn = mdb.connect(host='localhost',user='root', passwd='secret', db='MYPUB')

    cursor = conn.cursor()

    cursor.execute("SELECT qrcode(name) FROM BEER WHERE id=1")

    fout = open('image.png','wb')
    fout.write(cursor.fetchone()[0])
    fout.close()

    cursor.close()
    conn.close()

except IOError, e:

    print "Error %d: %s" % (e.args[0],e.args[1])
    sys.exit(1)
```

that's all! image.png is your QRCode.