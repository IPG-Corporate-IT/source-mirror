# How this archive was created (shell commands)

```
name='ipg-php-composer'
version='2.3.7'
gittag="ipg/$version"
mkdir -p "${name}-${version}" && cd "${name}-${version}"
git ls-remote --quiet --exit-code hub-composer "refs/tags/${gittag}"
mkdir '.git'; git init .
git --git-dir=".git" fetch --depth=1 --quiet 'hub-composer' "refs/tags/${gittag}:refs/tags/${gittag}"
git --git-dir=".git" --work-tree="." checkout  -b master "${gittag}"
cd ..
tar -cJf "${name}-${version}.tar.xz" "${name}-${version}"
``` 
