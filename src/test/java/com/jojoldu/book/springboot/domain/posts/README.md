### @After
* Junit에서 단위 테스트가 끝날 때마다 수행되는 메소드를 지정
* 보통 배포전 전체 테스트를 수행할 때 테스트간 데이터 침범을 막기위해 사용
* 여러 테스트가 동시에 수행되면 테스트용 데이터베이스인 H2에 데이터가 그대로 남아있어 다음 테스트 실행시 테스트가 실패할 수 있다.


### postsRepository.save
* 테이블 posts에 insert/update 쿼리를 실행
* id값이 있다면 update, 없다면 insert 쿼리가 실행

### postsRepository.findAll
* 테이블 posts에 있는 모든 데이터를 조회해오는 메소드