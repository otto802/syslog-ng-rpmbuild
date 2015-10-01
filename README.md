# syslog-ng-rpmbuild
RPMs of newer syslog-ng releases for Centos5/6

main reason for me was to get the redis support working (other special outputs not tested)


# Scratchpad notes on rpmbuild

definetely incomplete! I did a lot of edits at the .spec file to get a clean build!

## CENTOS 6

#### prepare

yum install rpm-build make bison flex gcc-c++ openssl-devel libnet-devel pcre-devel hiredis-devel

useradd -m syslog-ng-build
su -s /bin/bash syslog-ng-build
mkdir -p ~/rpmbuild/{BUILD,RPMS,SOURCES,SPECS,SRPMS}

* get release from github
* cp syslog-ng_3.6.4.tar.gz rpmbuild/SOURCES/

#### run rpmbuild

rpmbuild -bb syslog-ng-3.6.4/syslog-ng.spec

* build will fail: edit .spec file
* add files
* remove install.sh root references (-o root)
 

## CENTOS 5

centos5 seems not to support rpmbuilding with non-root (or I didnt figured it out how it works)

#### prepare

yum install rpm-build make bison flex gcc-c++ openssl-devel libnet-devel pcre-devel hiredis-devel libeventlog-devel

mkdir -p ~/rpmbuild
* get release from github
* cp syslog-ng-3.6.4.tar.gz /usr/src/redhat/SOURCES/syslog-ng_3.6.4.tar.gz

#### run rpmbuild

rpmbuild -bb syslog-ng-3.6.4/syslog-ng.spec

* build will fail: edit .spec file
* add files
* add hiredis dependency
* remove install.sh root references (-o root)
