## 특화 프로젝트 (20.03.23~05.01)

### :books: Book_U_Love

<br>

<img src="https://user-images.githubusercontent.com/52685250/81321616-c79ef400-90cd-11ea-82f3-ef974586108e.png" width="550">

<br>

## :one: Overview

> <i>읽고는 싶지만 무엇을 읽어야 할 지 모르겠다면!</i>
>
> <i>"이제 저희가 추천해드릴게요."</i>
>
> <i>빅데이터로 추천받는 맞춤 도서로 코로나 피해 집콕하며 함께 교양 쌓아요</i>
>
> <i>도서 추천 서비스, <Book_U_Love> 개봉 박두!</i>

- BOOK_U_LOVE 서비스는 유저 데이터를 기반으로 하여 협업필터링(Collaborative Filtering)을 이용해 유저별 맞춤 도서를 추천해주는 서비스입니다.
- 선호 성향이 비슷한 사용자들을 같은 그룹화, 동일 그룹 선호 상품 추천하는 방식입니다.

<br>

## :two: Tech Stack

:round_pushpin: <b>Frontend</b> : `Vue.js`

:round_pushpin: <b>Backend</b> : `Django`

:round_pushpin: <b>Database</b> : `MySQL` 

:round_pushpin: <b>Development Enviornment</b> : Python 3.7.4,  Django 2.2.7, Node.js higher than 10.16x, Vue CLI higher than 4.2.x

:round_pushpin: <b>Using Editor</b> : Visual Studio Code

<br>





## :star: 맡은 역할

- 백엔드 모델링
  - User, Book, Author, Category, Review 모델링
  - Category는 대분류, 중분류, 소분류로 구분하여 모델링
    - 각 카테고리별로 책 목록을 불러올 수 있도록 함
    - 선호하는 책 목록에 추가할 수 있도록 함
    - 소분류가 없는 책의 경우 중분류로 추가할 수 있도록 함
- 유저 관련 기능 구현
  - 회원가입, 로그인, 비밀번호 찾기 기능
- 댓글 CRUD 구현
  - 댓글 읽기, 작성, 수정, 삭제가 가능하도록 함
    - 스포일러 기능 추가하여 편의성을 높임
- 데이터 수집
  - 인터파크 도서 API + 인터파크 도서 페이지 크롤링
  - 13000여권의 책 데이터
  - JSON 파일로 저장해두어 데이터를 불러오기 용이하도록 함
- 데이터 분석
  - 최근 리뷰(1주일 이내) 필터링 및 리뷰 개수 순서로 정렬
  - 카테고리 구분하여 책 데이터 전송
  - 리뷰 개수순으로 데이터를 정렬하여 전송

<br>



## :three: Quick Start

### :pushpin: Local에서 실행

:heavy_check_mark: <b>Backend Installation & Run</b>

```
cd backend
python manage.py makemigrations
python manage.py migrate
python manage.py loaddata api/dummy.json
python manage.py runserver
```

:heavy_check_mark: <b>Frontend Installation & Run</b>

```
cd frontend
npm instlal
npm run serve
```

<br>

### :pushpin: 배포 환경에서 실행

- http://i02b205.p.ssafy.io/ 주소를 접속해서 볼 수 있습니다.

<br>

## :four: ERD Diagram

![Image Pasted at 2020-5-1 07-37](https://user-images.githubusercontent.com/52685250/80773944-6f7c6500-8b96-11ea-9deb-a76182b692fc.png)

<br>



## :five: Homepage Configuration

#### (1) 메인 화면

- 비로그인 상태

<img src="https://user-images.githubusercontent.com/52685247/81492091-1916d100-92d0-11ea-890f-718ff3dc5260.png" style="max-height:40%; max-width:40%">



- Youtube 썸네일 클릭 시 카드를 띄워 바로 이용할 수 있도록 하였습니다.

![image](https://user-images.githubusercontent.com/52685247/81493434-4fa61900-92db-11ea-9d16-d756c6cfe26f.png)

##### 기능설명

>- 평점기준 TOP10 도서 목록 표시
>   - 평점이 높은 도서 목록을 보여주어 사용자의 도서 선택을 도움
>- 도서추천관련 Youtube 썸네일
>   - 도서관련 동영상 컨텐츠의 접근성을 높임
>- 검색기능
>   - 책 제목을 기준으로 제목에 포함된 단어를 검색할 시 해당되는 책 목록 표시
>- 카테고리 분류
>   - 사용자가 카테고리별로 책을 찾아볼 수 있도록 대분류, 중분류, 소분류로 카테고리를 나누어 책 검색이 용이하도록 함

<p style="page-break-before: always;"></p>

- 로그인 상태
  - 관심 카테고리를 설정하고 작성한 리뷰 데이터를 기반으로 도서를 추천받은 경우입니다.

![image](https://user-images.githubusercontent.com/52685247/81492207-0c46ad00-92d1-11ea-85a6-a8c442cdb077.png)

##### 기능 설명

>- 사용자 리뷰 기반 추천
>   - 사용자가 남긴 리뷰를 기반으로 사용자가 선호할만한 카테고리의 책을 추천
>   - 사용자가 남긴 리뷰가 10개 이상일 경우 기능이 보여지도록 함

<br>

<p style="page-break-before: always;"></p>

#### (2) 리뷰 수집기

<img src="https://user-images.githubusercontent.com/52685247/81492264-88d98b80-92d1-11ea-9822-777b4992d16c.png" style="max-height:50%; max-width:50%">



##### 기능설명

>- 사용자의 리뷰를 기반으로 추천하는 서비스
>   - 서비스 용도에 맞게 리뷰 데이터를 많이 수집하여 추천 정확도를 높이기 위함
>   - 사용자가 남긴 리뷰를 기반으로 개인 맞춤형 책 추천이 가능하도록 함
>- 리뷰 작성 유도
>   - 기준개수(10개)를 남기지 않았을 때 알림을 띄워 사용자가 리뷰를 남기도록 유도
> - 평점 기준, 리뷰개수 기준 TOP20의 도서 목록 제공
>   - 사용자가 읽어봤을 도서를 제공하여 리뷰 작성을 유도
> - 읽은 것 같지만 잘 기억이 나지 않는 유저를 위해 줄거리 정보 제공
> - 아직 읽지않은 책은 넘어갈 수 있도록 함

<p style="page-break-before: always;"></p>

#### (3) 도서 상세 페이지

<img src="https://user-images.githubusercontent.com/52685247/81492443-a0654400-92d2-11ea-9c88-2570c206232f.png" style="max-height:50%; max-width:50%">

<img src="https://user-images.githubusercontent.com/52685247/81492468-e15d5880-92d2-11ea-9f47-fc5f1a0c7e78.png" style="max-height:50%; max-width:50%">

##### 기능 설명

>- 기본적인 댓글 CRUD 구현
>   - 댓글 작성, 수정, 삭제 기능 + 평점 남기기
> - 내가 남긴 리뷰가 최상단에 위치하도록 함
>   - 댓글 확인 및 수정이 용이하도록 함
>- 찜 목록 추가 기능
>   - 찜 목록 추가 시, 마이페이지에서 찜해둔 책 목록 모아보는 기능
>- 스포일러 체크 기능
>   - 스포일러가 포함된 댓글이라 생각되면 다른 사용자가 읽을지 여부를 판단할 수 있도록 함
>- 댓글 좋아요 기능
>   - 좋은 댓글이라고 생각되는 댓글을 많이 남기면 점수를 부여하여 사용자 랭킹에 사용
>- 평점 분포도 그래프
>   - 사용자가 책에 대한 판단을 잘 할 수 있도록 도움(시각적 효과)
>- 유사한 도서 추천
>   - 같은 장르의 리뷰 개수와 평점이 높은 도서 목록을 추천하여 사용자가 좋아할만한 도서 목록을 한번 더 보여줌

<p style="page-break-before: always;"></p>

#### (4) 작가 소개 페이지

- 작가 기본 정보 제공
- 작가의 출간작 제공

![image](https://user-images.githubusercontent.com/52685247/81492540-a1e33c00-92d3-11ea-9e30-4661cfcc4728.png)

<br>

<p style="page-break-before: always;"></p>

#### (5) MY PAGE > Dashboard

<img src="https://user-images.githubusercontent.com/52685247/81492514-52047500-92d3-11ea-90cd-77777ff66c8f.png" style="max-height:40%; max-width:40%">

##### 기능설명

> - 유저의 선호 카테고리 분석
>   - 유저가 도서에 남긴 리뷰를 기반으로  선호 카테고리를 분석하여 그래프로 보여줌
>   - 선호 카테고리에 맞춰 사용자가 선호할만한 도서 추천

<br>

#### (6) MY PAGE > MY BOOKS

- 도서 상세 페이지에서 읽고 싶은 책에 `찜하기` 버튼을 클릭해서 `내가 읽고 싶은 책` 리스트를 볼 수 있습니다.
- 그리고 각 도서에 리뷰를 작성하면 리뷰를 작성한 도서들을 볼 수 있습니다.

<img src="https://user-images.githubusercontent.com/52685247/81493037-e4a71300-92d7-11ea-96b5-327284543a09.png" style="max-height:40%; max-width:40%">

<img src="https://user-images.githubusercontent.com/52685247/81493049-f7b9e300-92d7-11ea-926a-33e5da6daede.png" style="max-height:40%; max-width:40%">

<br>

<p style="page-break-before: always;"></p>

#### (7) MY PAGE > Account

- 계정 정보를 수정할 수 있는 페이지

<img src="https://user-images.githubusercontent.com/52685247/81493093-6008c480-92d8-11ea-80da-f7a1e66f7f23.png" style="max-height:50%; max-width:50%">

##### 기능설명

> - 유저 개인정보 수정, 탈퇴 기능
> - 관심 카테고리 추가, 수정
>   - 메인페이지에서 관심 카테고리에 따른 추천이 가능하도록 함

<br>



#### (8) MY PAGE > Admin Page

- 관리자 권한이 있는 계정만 접근할 수 있는 페이지



##### (8-1) 유저 관리

- 가입 유저 관리 페이지

<img src="https://user-images.githubusercontent.com/52685247/81493124-c42b8880-92d8-11ea-8954-b5419d8355d3.png" style="max-height:50%; max-width:50%">



##### (8-2) 책 관리 페이지

- 도서별 평균 평점, 리뷰 개수를 기반으로 분석이 가능하도록 함

<img src="https://user-images.githubusercontent.com/52685247/81493133-d9081c00-92d8-11ea-9978-2f7c9c8cfb63.png" style="max-height:50%; max-width:50%">

<br>



#### (9) TMI Center

- 빅데이터를 기반으로 분석된 결과를 볼 수 있는 페이지



##### (9-1) 최근 1주일 간 상위 리뷰 데이터

- 리뷰 작성일 기준 1주일 이내에 작성된 리뷰가 많은 순서로 도서를 제공
- 최근 인기있는 도서를 파악할 수 있도록 함

<img src="https://user-images.githubusercontent.com/52685247/81493236-c6daad80-92d9-11ea-99f5-0a93e09aecfd.png" style="max-height:50%; max-width:50%">

<p style="page-break-before: always;"></p>

##### (9-2) 동년배 책 분석

- 연령대, 성별을 기준으로 최근에 많은 리뷰를 남긴 책 목록을 제공

<img src="https://user-images.githubusercontent.com/52685247/81493304-3f416e80-92da-11ea-86fa-95cbb8b8250d.png" style="max-height:50%; max-width:50%">



##### (9-3) 동년배 취향 분석

- 연령대, 성별을 기준으로 리뷰 개수 분포를 확인하기 용이하도록 그래프로 보여줌

<img src="https://user-images.githubusercontent.com/52685247/81493350-a6f7b980-92da-11ea-8e99-b1644625f627.png" style="max-height:50%; max-width:50%">

<p style="page-break-before: always;"></p>

##### (9-4) 카테고리별 전체 리뷰

- 각 카테고리별 리뷰 분포를 그래프로 보여줌
- 어떤 카테고리에 유저들의 관심이 높은지 한눈에 파악하기 쉽도록 함

<img src="https://user-images.githubusercontent.com/52685247/81493370-ce4e8680-92da-11ea-9128-ee706b69b6fc.png" style="max-height:50%; max-width:50%">



---
