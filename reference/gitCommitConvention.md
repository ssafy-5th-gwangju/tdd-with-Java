# 🤝 CommitConvention   
**Type**
|말머리|내용|
|------|----|
|feat:|새로운 기능 추가|     
|fix:|버그 수정|   
|docs:|문서 수정|    
|style:|코드 포맷 변경, 세미콜론 누락, 코드 변경 없음|    
|refactor:|프로덕션 코드 리팩터링|   
|test:|테스트 추가, 테스트 코드 리팩터링, 프로덕션 코드 변경 없음|   
|chore:|빌드 테스크 업데이트, 패키지 매니저 환경설정, 프로덕션 코드 변경 없음|   

**예시**
```git
git commit -m "feat:OOO 클래스 계산 기능 구현"   
```     

**팀 단위로 작업할 경우**
```git
git commit -m "feat(아이디):OOO 클래스 계산 기능 구현"   
```     

**커밋은 기능 단위당 하나씩 만들자**     
* `test:OOO 기능 테스트` 
* `feat:OOO 기능 구현`  
* `refactor:OOO 리팩토링`         
