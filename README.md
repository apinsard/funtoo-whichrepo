# funtoo-whichrepo

## Example usage

    ➜  ~ which whichrepo
    whichrepo () {
            cat=${1%/*}
            pkg=${1#*/}
            res=$(curl -s http://ports.funtoo.org/packages.xml | xmllint --xpath "/packages/category[@name='$cat']/package[@name='$pkg']/@repository" - 2>/dev/null)
            [ -n "$res" ] && echo $res || echo "gentoo?"
    }
    ➜  ~ whichrepo app-admin/ego
     repository="funtoo-overlay"
    ➜  ~ whichrepo x11-wm/qtile 
     repository="pinsard"
    ➜  ~ whichrepo media-video/vlc
     repository="gentoo-x11-shard" repository="funtoo-media"
    ➜  ~ whichrepo app-editors/vim
     repository="funtoo-overlay"
    ➜  ~ whichrepo mail-client/mutt
    gentoo?
    ➜  ~ whichrepo unexisting/package
    gentoo?
