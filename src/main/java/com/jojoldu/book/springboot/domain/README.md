### @MappedSuperclass
* JPA Entity 클래스들이 BaseTimeEntity를 상속할 경우 
* 필드들(createdDate, modifiedDate)도 컬럼으로 인식하도록 함

### @EntityListeners(AuditingEntityListener.class)
* BaseTimeEntity 클래스에 Auditing 기능을 포함시킴
  * Spring Data JPA에서 시간데 대해 자동으로 값을 넣어주는 기능

### @CreatedDate
* Entity가 생성되어 저장될 때 시간이 자동 저장됨

### @LastModifiedDate
* 조회한 Entity의 값을 변경할 때 시간이 자동 저장됨