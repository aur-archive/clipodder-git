pkgname=clipodder-git
pkgver=20121224
pkgrel=1
pkgdesc="A small simple cron-friendly podcast downloader, with support for arbitrary user defined media types"
arch=('any')
url="https://github.com/Afterburn/clipodder"
license=('GPL v3')
depends=(gcc curl libxml2 confuse git)
replaces=('clipodder', 'clipodder-git')
_gitroot="https://Afterburn@github.com/Afterburn/clipodder.git"
_gitname="clipodder"


build()
{
cd ${srcdir}

    msg "Connecting to the GIT server...."
    if [[ -d ${srcdir}/${_gitname} ]] ; then
        cd ${_gitname}
        git pull origin
        msg "The local files are updated..."
    else
        git clone ${_gitroot} --depth=1
    fi
    
    msg "GIT checkout done."

    msg "Starting make for: ${pkgname}"
    
    if [[ -d ${srcdir}/${_gitname}-build ]]; then
       msg "Cleaning the previous build directory..." 
       rm -rf ${srcdir}/${_gitname}-build
    fi

    mv ${srcdir}/${_gitname} ${srcdir}/${_gitname}-build
    
    cd ${srcdir}/${_gitname}-build/

    make
        
    mkdir -p ${pkgdir}/usr/bin
    cp ${_gitname} $pkgdir/usr/bin/clipodder || return 1
    

}

