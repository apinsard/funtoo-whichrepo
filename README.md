# funtoo-whichrepo

## Example usage

```
➜  ~ which whichrepo
whichrepo () {
        cat=${1%/*}
        pkg=${1#*/}
        res=$(curl -s http://ports.funtoo.org/packages.xml | xmllint --xpath "string(/packages/category[@name='$cat']/package[@name='$pkg']/@repository)" - 2>/dev/null)
        [ -n "$res" ] && echo $res || echo "gentoo?"
}
➜  ~ whichrepo app-admin/ego
funtoo-overlay
➜  ~ whichrepo x11-wm/qtile 
pinsard
➜  ~ whichrepo media-video/vlc  
gentoo-x11-shard
➜  ~ whichrepo mail-client/mutt
gentoo?
➜  ~ whichrepo unexisting/package
gentoo?
➜  ~
```
