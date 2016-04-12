## Create QRCode images from your MySQL queries ##

Here you can read about [how to compile this library](HowToCompile.md)

Once installed, to create a QRCode (PNG image) on the fly:
```
   SELECT qrencode( NAME ) FROM BEERS WHERE id=1;
```
The `SELECT` will return a blob containing your PNG image

**Be Careful**

> If you execute a query like this:
```
     SELECT qrencode( NAME ) FROM BEERS;
```
> and you have many many records, your SQL will be very slow and you will eat a lot of    memory and CPU!
> You are creating a PNG in memory for each record!


If you want to try this function from a python script [here the code](DemoUsage.md).

**N.B.**
**I've moved this project to [GitHub](https://github.com/Lus71/lib_mysqludf_qrencode)**

