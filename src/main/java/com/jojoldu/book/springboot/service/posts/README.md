### 영속성 컨텍스트
```java
@Transactional
    public Long update(Long id, PostsUpdateRequestDto requestDto) {
        Posts posts = postsRepository.findById(id).orElseThrow(() -> new IllegalArgumentException("해당 게시글이 없습니다. id=" + id));
        posts.update(requestDto.getTitle(), requestDto.getContent());
        return id;
    }
```

* update 기능에서 쿼리를 날리는 부분이 없음 => JPA 영속성 컨텍스트 때문
* 영속성 컨텍스트: 엔티티를 영구 저장하는 환경
* JPA의 핵심 내용은 엔티티가 영속성 컨텍스트에 포함되어 있냐 아니냐로 갈림
* JPA의 엔티티 매니저가 활성화된 상태로 트랜잭션 안에서 데이터베이스에서 데이터를 가져오면 이 데이터는 영속성 컨텍스트가 유지된 상태
* 이 상태에서 해당 데이터의 값을 변경하면 트랜잭션이 끝나는 시점에 해당 테이블에 변경분을 반영
* 즉, Entity 객체의 값만 변경하면 별도로 Update 쿼리를 날릴 필요가 없음
* 이 개념을 더티 체킹(Dirty checking)이라고 함

-------------------

```java
  @Transactional(readOnly = true)
    public List<PostsListResponseDto> findAllDesc(){
        return postsRepository.findAllDesc().stream().map(PostsListResponseDto::new).collect(Collectors.toList());
    }
```
### @Transactional(readOnly = true)
* 트랜잭션 범위는 유지하되, 조회 기능만 남겨두어 조회 속도가 개선되기 때문에 
  * 등록, 수정, 삭제 기능이 전혀 없는 메서드에 사용을 권장