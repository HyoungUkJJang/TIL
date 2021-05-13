회원관리 시스템 API - POST기반구조(컬렉션)

회원목록 /members -> GET
회원등록 /members -> POST
회원조회 /members/{id} -> GET
회원수정 /members/{id} -> PATCH, PUT, POST
회원삭제 /members/{id} -> DELETE

파일관리 시스템 API - PUT 구조(스토어)

파일목록 /files -> GET
파일조회 /files/{filename} -> GET
파일등록 /files/{filename} -> PUT
파일삭제 /files/{filename} -> DELETE
파일 대량 등록 /files -> POST

HTML FORM 사용할때는 - Get Post만 지원하기때문에 Control uri

-------참고하면 좋은 URI 설계 개념-------------

1. 문서
- 단일 개념(파일 하나, 객체 인스턴스, DB row) ex > /members/100, /files/start.png

2. 컬레션 (주로사용)
- 서버가 관리하는 리소스 디렉터리
- 서버가 리소스의 URI를 생성하고 관리 ex > /members

3. 스토어 (주로사용x)
- 클라이언트가 관리하는 지원 저장소
- 클라이언트가 리소스의 URI를 알고 관리 ex > /files

4. 컨트롤러, 컨트롤 URI
- 문서, 컬렉션, 스토어로 해결하기 어려운 추가 프로세스 실행
- 동사를 직접사용 ex > /members/{id}/delete
