# How to setup Debian 10 buster on the wsl
이 문서에는 데비안 10 (buster) 버전의 이미지 구축 방법을 기술 한다.

## 호스트 이미지 구축
### WSL 이미지 생성
```shell
wsl --import Debian-10 C:\wsl-rootfs\debian-10 [ELDEBS_ROOT]\rootfs\x86_64-buster.tar.gz
```
### 저장소 설정 및 추가 패키지 설치
```bash
# 구버전 배포판에 대한 저장소 설정
echo "deb http://deb.debian.org/debian/ buster main contrib non-free" > /etc/apt/sources.list
echo "deb http://deb.debian.org/debian/ buster-backports-sloppy main contrib non-free" >> /etc/apt/sources.list
echo "deb http://deb.debian.org/debian/ buster-backports main contrib non-free" >> /etc/apt/sources.list
echo "deb http://deb.debian.org/debian/ buster-proposed-updates main contrib non-free" >> /etc/apt/sources.list

# 추가 패키지 설치
[ELDEBS_ROOT]/scripts/install-pkgs-debian-buster.sh
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
