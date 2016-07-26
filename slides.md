class: center, middle

## The FreeBSD ports & pkg System
### Developer's Perspective

Li-Wen Hsu &lt;lwhsu@FreeBSD.org&gt;

---
![https://lwhsu.github.io/talk-20160730-bsddaytw_ports_dev/](url-qrcode.png)

.footnote[https://lwhsu.github.io/talk-20160730-bsddaytw_ports_dev/]

---
# Package management

- Install 3rd party softwares

---
# About FreeBSD Ports

https://en.wikipedia.org/wiki/FreeBSD_Ports

- Jordan Hubbard committed his port make macros to the FreeBSD CVS repository on August 21, 1994.
  * https://svnweb.freebsd.org/changeset/ports/5
  * https://svnweb.freebsd.org/ports/head/Mk/bsd.port.mk?revision=5&view=markup&pathrev=5#l28

- Src people make FreeBSD, ports pople make FreeBSD useful

---
# About FreeBSD Package

- Package
- Pkgng
- Pkg

https://man.FreeBSD.org/pkg

---
# Porter's Handbook

https://www.freebsd.org/doc/en_US.ISO8859-1/books/porters-handbook/

---
# Ports Tree

```
$ ls /usr/ports
.arcconfig       Templates/       devel/           mail/            shells/
.gitattributes   Tools/           dns/             math/            sysutils/
.gitignore       UIDs             editors/         misc/            textproc/
.portsnap.INDEX  UPDATING         emulators/       multimedia/      ukrainian/
CHANGES          accessibility/   finance/         net/             vietnamese/
CONTRIBUTING.md  arabic/          french/          net-im/          www/
COPYRIGHT        archivers/       ftp/             net-mgmt/        x11/
GIDs             astro/           games/           net-p2p/         x11-clocks/
INDEX-10         audio/           german/          news/            x11-drivers/
INDEX-8          benchmarks/      graphics/        palm/            x11-fm/
INDEX-9          biology/         hebrew/          polish/          x11-fonts/
Keywords/        cad/             hungarian/       ports-mgmt/      x11-servers/
LEGAL            chinese/         irc/             portuguese/      x11-themes/
MOVED            comms/           japanese/        print/           x11-toolkits/
Makefile         converters/      java/            russian/         x11-wm/
Mk/              databases/       korean/          science/
README           deskutils/       lang/            security/
```

---
# A Port

- Makefile
- distinfo
- files/
- pkg-descr
- pkg-plist

---
# Become a Ports Developer!

````sh
echo DEVELOPER=yes >> /etc/make.conf
````

---
# Quick Porting

- Writing the Makefile
- Writing the Description Files
- Creating the Checksum File
- Testing the Port
- Checking the Port with portlint
- Submitting the New Port

---
# Makefile

```Makefile
# $FreeBSD$

PORTNAME=       oneko
PORTVERSION=    1.1b
CATEGORIES=     games
MASTER_SITES=   ftp://ftp.cs.columbia.edu/archives/X11R5/contrib/

MAINTAINER=     youremail@example.com
COMMENT=        Cat chasing a mouse all over the screen

.include <bsd.port.mk>
```

(Using space for formatting, but port Makefile should use tab with 8 as width)

.right[![onko](oneko.png)]

---
# pkg-descr

```
This is a port of oneko, in which a cat chases a poor mouse all over
the screen.
 :
(etc.)

WWW: http://www.oneko.org/
```

---
# pkg-plist

```
bin/oneko
man/man1/oneko.1.gz
lib/X11/app-defaults/Oneko
lib/X11/oneko/cat1.xpm
lib/X11/oneko/cat2.xpm
lib/X11/oneko/mouse.xpm
```

- `PLIST_FILES=` in `Makefile`
- Sorting
   * file `sort`
   * directory `sort -r`
- `make makeplist`

---
# Checksum File

- `make makesum`

---
# Ports Makfile targets

---
# UID/GID

---
# Testing

---
# Staging

---
# USE

--
# SUB

---
# Master Sites

- MASTER_SITES
- MASTER_SITE_SUBDIR

- bsd.sites.mk

---
# *DIR

- MASTERDIR
- PORTSDIR
- DISTDIR
- WRKDIRPREFIX
- WRKDIR
- WRKSRC
- PATCHDIR
- SCRIPTDIR
- FILESDIR
- PKGDIR
- SRC_BASE

---
# *_DEPENDS

- EXTRACT_DEPENDS
- PATCH_DEPENDS
- FETCH_DEPENDS
- BUILD_DEPENDS
- RUN_DEPENDS
- LIB_DEPENDS
- TEST_DEPENDS

---
# CONFLICTS

---
# USE_GITHUB

---
# License

---
# OPTIONS

---
# BROKEN

---
# Other files under ports/

- CHANGES
- LEGAL
- MOVED
- UPDATING

---
# Paths

- LOCALBASE
  * Where ports install things
  * Default: /usr/local
- LINUXBASE
  * Where Linux ports install things
  * Default: `/compat/linux`
- PREFIX
  * Where *this* port installs its files.
  * Default: ${LINUXBASE} if USE_LINUX_PREFIX is set, otherwise ${LOCALBASE}

---
# INSTALL_* & COPYTREE_*

- INSTALL_PROGRAM
- INSTALL_KLD
- INSTALL_LIB
- INSTALL_SCRIPT
- INSTALL_DATA
- INSTALL_MAN

- COPYTREE_BIN
- COPYTREE_SHARE

---
# Doc & Examples & Data

- PORTDOCS
  * DOCSDIR
- PORTEXAMPLES
  * EXAMPLESDIR
- PORTDATA
  * DATADIR

---
# handy pkg commands
- make -V
- pkg version -t

---
# Utilities

- ports-mgmt/porttools
- ports-mgmt/portlint

- bz

---
# Submit your work

- New porrt
- Patch

---
# Special port type

- slave port
- meta port

---
# Language specific ports

- Perl
- Python
- Ruby
- Haskell

---
# FreeBSD.org web services

- https://bugs.FreeBSD.org
- https://reviews.FreeBSD.org
- http://portscout.FreeBSD.org/

- Redports

---
# Best Practices

---
# References

- Mk/bsd.pot.Mk
  * https://svnweb.freebsd.org/ports/head/Mk/bsd.port.mk?view=markup

---
# Possible target as 2016/07/30
