# Dev Note

## IntelliJ
### 프로젝트 열기
1. 파일 - 새로 만들기 - 기존 소스에 있는 프로젝트
2. 해당 작업폴더 선택 - 확인
3. 외부 모델에서 프로젝트 가져오기 - 웬만하면 이클립스 선택 - 다음 - 다음 - 다음 - 확인

### 서버(톰캣) 연결
1. 우측 상단 셀렉트박스 ‘현재 파일’ - 구성 편집 - 새 항목 추가 - tomcat - local
2. 폴더 지정 / 하단 ‘수정’ - war exploded 선택 - 컨텍스트패스 슬래시 뒷부분 지우기 - 확인

### package lombok error
1. 환경설정 - 플러그인 - lombok 설치
2. pom.xml lombok 디펜던스 있는지 확인
3. 아래 내용으로 입력되어있는지 확인 (인텔리제이가 허용을 안해서 수정해야함)
   1. 
```
`⠀<repository>`
`<id>egovframe</id>`
`<url><https://maven.egovframe.go.kr/maven/></url>`
`<releases>`
`<enabled>true</enabled>`
`</releases>`
`<snapshots>`
`<enabled>false</enabled>`
`</snapshots>`
`</repository>`
```

4. 메이븐 업데이트 (ctrl + shift + o)

### 알림
1. 사전 빌드 공유 색인 다운로드 - 항상 다운로드
2. 종속성 java.batch.blahblah.Jakarta EE:Batch blahblah - 무시

### git 연동참고
[https://brunch.co.kr/@mystoryg/168](https://brunch.co.kr/@mystoryg/168)

