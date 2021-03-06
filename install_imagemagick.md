### installing Image Magick

If you find that you need to install ImageMagick (e.g., in order to render svg to png):

Follow this link to install from source: `https://imagemagick.org/script/install-source.php`

You might run into an issue where the compiler can't find parser.h. To fix this, follow the instructions in this blogpost: https://medium.com/@maohua.ethan.wang/install-imagemagick-on-mac-with-options-d5a2174df62

We ended up needing to add the libxml location to CFLAGS, but then actually just added a with-xml=no option so we don't compile/install imagemagick the libxml delegate library... hopefully that is okay for our purposes. but if it is not, we'll have to revisit this later. @jefan 11/6/2019
Also consulted this forum: `https://www.imagemagick.org/discourse-server/viewtopic.php?t=29261`

Download imagemagick tar file.

Go to where it was downloaded and run: tar xzvf ImageMagick.tar.gz
Perhaps, when running the ./configure command, add these options to make sure that the delegate libraries (namely jpeg, png) are also installed:
```
./configure --enable-delegate-build --with-png=yes --with-jpeg=yes CFLAGS="-I//anaconda3/include/libxml2 -I//anaconda3/include" --with-xml=yes
make clean; make
make install
make check (optional to check installation)
```
