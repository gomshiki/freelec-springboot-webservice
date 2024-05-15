### {{#posts}}
* posts라는 List를 순회합니다.
* Java의 for문과 동일하게 생각하면 됩니다.

### {{id}} 등의 {{변수명}}
* List에서 뽑아낸 객체의 필드를 사용합니다.

### {{posts.id}}
* mustache는 객체의 필드 접근 시 점(Dot)으로 구분합니다.
* 즉, Post 클래스의 id에 대한 접근은 posts.id로 사용할 수 있습니다.

### readonly
* input 태그에 읽기 기능만 허용하는 속성
* id와 author는 수정할 수 없도록 일기만 허용하도록 추가합니다.