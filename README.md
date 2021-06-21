# 2zoProject
# 소설실 2조 프로젝트
# 구성
* LoginActivity : 로그인 페이지를 작동시키는 액티비티
* MainActivity : 로그인하면 들어갈 수 있는 첫 페이지
* meminfo : firebase 에 전달하는 회원 정보 클래스
* MeminfoActivity : 회원정보를 설정할 수 있는 액티비티
* MemInfoConfirmActivity : 회원정보를 확인하는 액티비티
* Post : firebase 에 전달되는 게시글 클래스
* ReadPostActivity : 게시글을 나열시키는 액티비티
* SignUpActivity : 회원가입 페이지를 작동시키는 액티비티
* SubPost : firebase 기반 게시글의 document 에 저장되는 댓글 클래스
* WritePostActivity : 게시글을 작성할 수 있는 액티비티
## 나인수
* login page -> clear
* logout page -> clear
* member Information part -> clear
* MainActivity layout 설계 -> clear
* 게시판 작성, 보기 -> clear
* 게시판 형태의 sns 텍스트 뷰를 클릭 가능하게 바꾸고  클릭시 내용까지 보여주기.-> 다른 액티비티 구상 필요 -> clear
* 댓글 시스템 (중요) -> clear
* 대략 90퍼 센트 완료
## 앞으로 구현해야 할것
* 회원가입시점에서 회원정보 입력하기 기능.
* 회원정보 추가하기(사진, 친한친구 ..등)
* 게시판 상태설정(모집중, 모집완료) -> update 구현
* 게시판 글 내에서 제한된 모집인원 구현(중요)
* 삭제 기능 구현

---
## 05/09
* 회원가입시 바로 MainActivity 로 이동
* 비밀번호 재설정 이메일 보내는 기능 추가
    * 비로그인 상태에서 가능
* 회원정보 입력 엑티비티인 memInfoActivity 작성
* 회원정보를 입력하는 기능구현
* 회원정보를 불러오는 기능구현
* firebase database 앱 gradle 에 등록
* firebase database 생성
* MainActivity 기본 레이아웃 배치
---
## 05/16
* MainActivity 에 글쓰기 버튼 동작 설정
* WritePostActivity 작성
    * 게시글 작성 기능을 포함하는 액티비티
* mainActivity 가 활성화 되면 setPostList 함수를 호출
    * setPostList 함수는 모든 게시글의 제목을 추가해 준다.
* 전혀 정렬되지 않았다. 최신순으로 정렬 기능을 구현해야한다.
    * timestamp 속성을 추가하여 해당 속성을 기준으로 내림차순 정렬 최대 20개 설정
    * 즉 최신순으로 게시글 제목을 메인 화면에 나열시켰다.
---
## 05/30
* 게시글 내용 확인기능 작성
* ReadPostActivity 추가작성
    * 데이터베이스로부터 꺼내온 데이터를 MainActivity 에서 Intent 를 통해 해당 ReadPostActivity 로 전달
    * 동적 Widget 여러개를 서로 다른 tag 로 구분하여 하나의 리스너를 통해 관리.
    * 해당 tag 와 일치하는 Post 배열을 구현해서 원하는 데이터만 Intent 로 전달.
* MainActivity 에서 나열했던 게시글 리스트들에게 클릭 동작을 구현
* ReadPostActivity 에서 해당 하는 Post 객체에 title 과 context 를 출력
---
## 05/31
* 댓글 서비스 구현 완료
    * document 안에 중첩 collection 을 만들고 그곳을 댓글문서 저장소로 활용
    * ReadPostActivity 안에 EditText 와 Button 구현
* 해당 문서 ID를 Intent 를 통해 String 형태로 전달받음
    * 전달받은 문서 ID 안에 중첩 collection 을 만들기 때문에 현재 보고있는 게시글의 댓글을 저장할 수 있음
* 댓글 작성후 실시간으로 화면에 적용(임시방편 -> 효율적인 방법 필요)
---
## 06/205
* 삭제 서비스 구현 완료
    * 본인 이 쓴 글인 경우에만 삭제
    * 본인이 쓴 글이 아닌 경우 toast 메시지만 보내고 끝냄
    * 삭제후 mainActivity 에 있는 list_post 초기화
    * 삭제후 이동은 finish 를 이용하고 초기화는 onResume 을 이용함
* 문서에 publisher 시각화
---