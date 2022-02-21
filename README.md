# PowerManagerApiServer

## history

### v1.0.1

* HTTP2Switch(HTTP/2 지원 여부), IncludeCipherSuites(TLS 시 키 교환 알고리즘 제한) 설정 추가
* HTTP/2 통신 지원 추가 - HTTP2Switch true 시 HTTP/2 가 지원되면 HTTP/2 통신, false 이거나 지원되지 않으면 HTTP/1.1 통신
* IncludeCipherSuites TLS 통신 시 특정 키 교환 알고리즘만 사용하도록 제하는 기능 추가 https://docs.microsoft.com/ko-kr/dotnet/api/system.net.security.tlsciphersuite?view=net-6.0
* IncludeCipherSuites 설정 시 주의 사항 지원 되지 않는 알고리즘 선택하거나, HTTP2Switch를 true 했는데 HTTP/2에서 지원하지 않는 알고리즘 선택 시 웹서버 비정상 가동
* PM-B540-W 1.01.30 이하 모든 디바이스는 IncludeCipherSuites 를 제한하지 말것 API 인증이 되지 않음

## Config.yml

* HttpPort: Http 접속 포트 (기본값 18080)
* HttpsPort: Https 접속 포트 (기본값 18443)
* ServerCertificate: 서버인증서 경로 (p12, pfx, pem 등 - 필수값)
* ServerCertificatePassword: 서버인증서 패스워드 (필수값)
* DbPath: Database Sqlite 파일 경로 (필수값)

## IncludeCipherSuites 설정 방법
```
IncludeCipherSuites:
  - "TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384"
  - "TLS_ECDHE_RSA_WITH_CHACHA20_POLY1305_SHA256"
```