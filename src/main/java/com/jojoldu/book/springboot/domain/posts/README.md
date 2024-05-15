
### @Entity
* 테이블과 링크될 클래스임을 나타냅니다.
* 기본값으로 클래스의 카멜케이스 이름을 언더스코어 네이밍으로 테이블 이름을 매칭합니다.
* ex) SalesManager.java -> sales_manager table

### @Id
* 해당 테이블의 PK 필드를 나타냅니다.

### @GeneratedValue
* PK의 생성 규칙을 나타냅니다.
* 스프링 부트 2.0에서는 GenerationType.IDENTITY 옵션을 추가해야만 auto_increment가 됩니다.

### @Column
* 테이블의 칼럼을 나타냅니다. 굳이 선언하지 않아도 해당 클래스의 필드는 모두 칼럼이 됩니다.
* 사용하는 이유는, 기본값 외에 추가로 변경이 필요한 옵션이 있을 때 사용합니다.
* 문자열의 경우 VARCHAR(255)가 기본값인데, 사이즈를 500으로 늘리고 싶거나, 타입을 TEXT로 변경하고 싶거나 등의 경우에 사용됩니다.
  */

### PostsRepository
* DB Layer 접근자로, JPA에서는 Repository라고 부르며 인터페이스로 생성합니다.
* 단순히 인터페이스를 생성 후, JpaRepository<Entity 클래스, PK 타입>를 상속하면 기본적인 CRUD 메소드가 자동으로 생성됩니다.
* @Repository를 추가할 필요도 없습니다.
* 주의할 점은 Entity 클래스와 기본 Entity Repository는 함께 위치해야 하는 점입니다.
* 둘은 아주 밀접한 관계이고, Entity 클래스는 기본 Repository 없이 제대로 역할을 할 수가 없습니다.
* 규모가 있는 프로젝트에서는 도메인별로 프로젝트를 분리해야 합니다.
* 그런데 이 프로젝트는 그렇게 복잡하지 않으니 도메인 패키지에서 함께 관리합니다.
