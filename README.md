# Embedded Linux Development Environment Build System Using WSL (ELDEBS)
 WSL를 사용한 임베디드 리눅스 개발환경 빌드 시스템

# 소개
임베디드 리눅스 소프트웨어 개발을 위한 개발 환경을 WSL를 사용하여 구축하는 것을 목표로 한다.
기반이 되는 배포판은 우분투/데비안 를 사용하여 구축을 진행 한다.
타겟 장치와 호스트 환경은 동일한 배포판 버전을 을 사용한다. (호스트:데비안-9-x86_64, 장치:데비안-9-ARM64)

# WSL 이미지 생성 방법
wsl 이미지 생성에 사용하는 루트 파일 시스템은 docker에서 사용하는 루트 파일 시스템과 동일 하다.
떄문에 구축하고자 하는 배포판 버전의 rootfs 압축 이미지 (tar.gz, tar.bz2, tar.xz)를 사용하여 구성하게 된다.
자세한 사용법은 다음의 경로를 참고 하도록 하자. https://learn.microsoft.com/ko-kr/windows/wsl/

## Debian의 경우
데비안 배포판의 경우 루트 파일 시스템을 다음의 경로를 통해서 획득이 가능 하다.
구버전 경로 : https://github.com/debuerreotype/docker-debian-eol-artifacts
최근 버전 경로 : https://github.com/debuerreotype/docker-debian-artifacts

각각의 저장소에서 원하는 대상의 블랜치를 사용하여 루트 파일 시스템을 확보 할 수 있다.

## Ubuntu의 경우
https://ubuntu.com/wsl 에서 자세한 정보를 확인 할수 있다.
그리고 기본적으로 우분투 LTS 버전을 다음과 같은 명령어를 통해서 설치 할수 있다. 
- [wsl --install --web-donwload Ubuntu-18.04]
- [wsl --install --web-donwload Ubuntu-20.04]
- [wsl --install --web-donwload Ubuntu-22.04]
