# How to setup Ubuntu 20.04 Focal on the WSL
이 문서에는 우분투 20.04 Focal 버전의 이미지 구축 방법을 기술 한다.

## 호스트 이미지 구축
### WSL 이미지 설치
```shell
wsl --install Ubuntu-20.04 --web-download
```
### 추가 패키지 설치
```shell
[ELDEBS_ROOT]/scripts/install-pkgs-ubuntu-20.04.sh
```
### multistrap 

#### Install rootfs for ARM64 Ubuntu 20.04
```bash
mkdir -p /opt/multistrap/arm64-ubuntu-focal
cd /opt/multistrap/arm64-ubuntu-focal
tar xvf [ELDEBS_ROOT]/gpg/ubuntu-trust-gpg.tar.bz2
multistrap -f [ELDEBS_ROOT]/multistrap/ubuntu-20.04-forcal.conf
[ELDEBS_ROOT]/sysroot-relativelinks.py /opt/multistrap/arm64-ubuntu-focal
```

#### Install rootfs for ARM64 Debian 10
```bash
mkdir -p /opt/multistrap/arm64-debian-buster
cd /opt/multistrap/arm64-debian-buster
tar xvf [ELDEBS_ROOT]/gpg/debian-trust-gpg.tar.bz2
multistrap -f [ELDEBS_ROOT]/multistrap/debian-10-buster-dev.conf
[ELDEBS_ROOT]/sysroot-relativelinks.py /opt/multistrap/arm64-debian-buster
```

#### Install rootfs for ARM64 Debian 9
```bash
mkdir -p /opt/multistrap/arm64-debian-stretch
cd /opt/multistrap/arm64-debian-stretch
tar xvf [ELDEBS_ROOT]/gpg/debian-trust-gpg.tar.bz2
multistrap -f [ELDEBS_ROOT]/multistrap/debian-9-stretch.conf
[ELDEBS_ROOT]/sysroot-relativelinks.py /opt/multistrap/arm64-debian-stretch
```
