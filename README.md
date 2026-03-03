# oba_infra
한입 기사 인프라 레포지토리입니다.

---
### 공통 네트워크 생성 (필수)

컴포즈를 올리기 전에 터미널에서 네트워크를 먼저 수동으로 만들어야 합니다.
```sh
docker network create oba_shared_network
```