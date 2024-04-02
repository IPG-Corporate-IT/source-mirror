# source-mirror
Files used for building binaries. Typically tar files, author signatures and checksums.

Files may be directly downloaded using a modified link:
```
# illustrative example
LINK='https://github.com/IPG-Corporate-IT/source-mirror/blob/main/apcu-5.1.21.tgz'
curl -sLO  "https://raw.githubusercontent.com/IPG-Corporate-IT/source-mirror/main/${LINK##*/}"
# other example, employing login
curl -sL -u ${{ github.repository_owner }}:${{ secrets.GITHUB_TOKEN }} -o "${LINK##*/}"
```
- Redis server source is suffixed with tar.gz:
  - The redis*.tgz files are PHP Pecl
  - typically redis-5.3.7.tgz redis-6.2.6.tar.gz

- PECL source files may be downloaded
  - pecl download pdo_sqlsrv
  - pecl download sqlsrv

See this section of ipg-php.spec and ipg-http.spec
```
Source0: https://archive.apache.org/dist/httpd/httpd-%{version}.tar.bz2
Source1: https://archive.apache.org/dist/httpd/httpd-%{version}.tar.bz2.asc
%global  pubkeyurl https://keys.openpgp.org/vks/v1/by-fingerprint/26F51EF9A82F4ACB43F1903ED377C9E7D1944C66
%global  sha256sum fa16d72a078210a54c47dd5bef2f8b9b8a01d94909a51453956b3ec6442ea4c5
```

- The above entries are interpreted as follows:
  - The `%prep` uses the sha256 checksum to confirm file integrity
  - The `%prep` confirms the authenticity of the source file tarball using the publisher's well know public key and detached ASCII armored signature. The public key is fetched from the keyserver using the key server URL.
  - Source0 is extracted per the `Source0` and within the `%setup` macro.
