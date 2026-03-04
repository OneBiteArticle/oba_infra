# oba_infra
한입 기사 인프라 레포지토리입니다.

---
### 인증서 발급(1회)
```sh
docker compose run --rm certbot certonly --webroot --webroot-path=/var/www/certbot -d your-domain.com
```
- 성공하면?: Congratulations! Your certificate and chain have been saved at... 메시지가 뜹니다.

### 공통 네트워크 생성 (필수)

컴포즈를 올리기 전에 터미널에서 네트워크를 먼저 수동으로 만들어야 합니다.
```sh
docker network create oba_shared_network
```

### 크론탭 설정 (필수)
컨테이너 띄운 후 Ec2 터미널에서 자동 새로고침을 등록해야 합니다.
```sh
# 크론탭 편집기 열기
sudo crontab -e
```
```sh
# 매주 일요일(0) 새벽 4시 0분에 Nginx 새로고침 (일주일에 한 번)
0 4 * * 0 docker exec oba-nginx nginx -s reload
```