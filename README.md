# source-mirror
Files used for building binaries. Typically tar files, author signatures and checksums.

Files may be directly downloaded using a modified link:
```
# illustrative example
LINK='https://github.com/IPG-Corporate-IT/source-mirror/blob/main/apcu-5.1.21.tgz'
curl -sLO  "https://raw.githubusercontent.com/IPG-Corporate-IT/source-mirror/main/${LINK##*/}"
```
# Redis server source is suffixed with tar.gz
# The redis*.tgz files are PHP Pecl
redis-5.3.7.tgz redis-6.2.6.tar.gz

# PECL source files may be downloaded
pecl download pdo_sqlsrv
pecl download sqlsrv
