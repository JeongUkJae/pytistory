Post API
========

게시글 목록 조회
----------------

최근 게시물 목록을 가져올 수 있는 API입니다. 해당 API에 관한 정보는
`게시물 목록 API <http://www.tistory.com/guide/api/post.php#post-list>`_ 를 통해
살펴보실 수 있습니다.

.. code-block:: python

  from pytistory import PyTistory

  pytistory = PyTistory()
  pytistory.configure()

  response = pytistory.post.list(blog_name='oauth')

결과값은 아래처럼 받을 수 있습니다.

.. code-block:: json

  {
    "status": "200",
    "item": {
      "url": "http://oauth.tistory.com",
      "secondaryUrl": "",
      "page": "1",
      "count": "10",
      "totalCount": "4",
      "posts": {
        "post": [
          {
            "id": "4",
            "title": "티스토리 OAuth Open API 일단 써보세요!",
            "postUrl": "http://oauth.tistory.com /4",
            "visibility": "0",
            "categoryId": "0",
            "comments": "6",
            "trackbacks": "0",
            "date": "1303796661"
          },
          {
            "id": "3",
            "title": "View에 보냅니다~",
            "postUrl": "http://oauth.tistory.com /3",
            "visibility": "3",
            "categoryId": "0",
            "comments": "0",
            "trackbacks": "0",
            "date": "1303372106"
          },
          {
            "id": "2",
            "title": "View에 보내봅니다.",
            "postUrl": "http://oauth.tistory.com /2",
            "visibility": "3",
            "categoryId": "0",
            "comments": "0",
            "trackbacks": "0",
            "date": "1303372007"
          },
          {
            "id": "1",
            "title": "티스토리 OAuth2.0 API 오픈!",
            "postUrl": "http://oauth.tistory.com /1",
            "visibility": "0",
            "categoryId": "0",
            "comments": "0",
            "trackbacks": "0",
            "date": "1303352668"
          }
        ]
      }
    }
  }

게시글 작성
----------------

게시글을 작성할 수 있는 API입니다. 해당 API에 관한 정보는
`게시글 작성 API <http://www.tistory.com/guide/api/post.php#post-write>`_ 를 통해
살펴보실 수 있습니다.

.. code-block:: python

  from pytistory import PyTistory

  pytistory = PyTistory()
  pytistory.configure()

  response = pytistory.post.write("Post Title",
                                  blog_name='sampleUrl',
                                  visibility=1,
                                  category=12,
                                  content="Post Content",
                                  tag=["Tag1", "Tag2"])

인자는 다음처럼 받습니다.

:title: 포스트 제목입니다. ``str``\ 타입입니다.

:blog_name: 블로그 명입니다. 기본값은 ``None``\. ``str``\ 타입입니다.

:target_url: 블로그의 url입니다. deprecated된 옵션입니다. 기본값은 ``None``\. ``str``\ 타입입니다.
:visibility:

    * 0: 비공개
    * 1: 보호
    * 2: 공개
    * 3: 발행

    기본값은 ``0``\입니다.

:published: 발행 시간. 만약 설정시 예약 발행이 됨., ``None``\. 타입은 ``datetime.datetime``\ 타입입니다.

:category: 카테고리를 뜻하고, ``0``\은 분류없음입니다. 값 설정시 카테고리가 설정됩니다. 기본값은 ``0``\입니다.
:content: 글 내용, 기본값은 ``None``\이고 ``str``\타입입니다.
:slogan: 문자 주소. 이는 아마 블로그 주소 형식을 문자로 설정했을 때의 값인 듯 합니다. 기본값은 ``None``\.
:tag: 게시글에 태그를 설정합니다, 기본값은 ``None``\. 값 설정할 때 타입은 ``list``\입니다.

결과값은 아래처럼 받을 수 있습니다.

.. code-block:: json

  {
    "status": "200",
    "postId": "74",
    "url": "http://sampleUrl.tistory.com/74"
  }

게시글 수정
--------------

작성된 게시글을 수정할 수 있는 API입니다. 해당 API에 관한 정보는
`게시글 수정 API <http://www.tistory.com/guide/api/post.php#post-modify>`_ 를 통해
살펴보실 수 있습니다.

.. code-block:: python

  from pytistory import PyTistory

  pytistory = PyTistory()
  pytistory.configure()

  response = pytistory.post.modify("Post Title",
                                  1,
                                  blog_name='sampleUrl',
                                  visibility=1,
                                  category=12,
                                  content="Post Content",
                                  tag=["Tag1", "Tag2"])

인자값은 위의 게시글 작성 API에서, 두가지 변경사항만 있습니다.

``published``\값을 설정할 수 없고, ``int``\타입의 ``post_id``\를 추가적으로 전달해주어야 합니다.

결과값은 아래처럼 받을 수 있습니다.

.. code-block:: json

  {
    "status": "200",
    "postId": "74",
    "url": "http://sampleUrl.tistory.com/74"
  }

글 읽기
--------------

단일 게시글을 읽을 수 있는 API입니다. 해당 API에 관한 정보는
`글 읽기 API <http://www.tistory.com/guide/api/post.php#post-read>`_ 를 통해
살펴보실 수 있습니다.

.. code-block:: python

  from pytistory import PyTistory

  pytistory = PyTistory()
  pytistory.configure()

  response = pytistory.post.read(1, blog_name='sampleUrl')

인자값은 ``blog_name``\과 ``post_id``\만을 받습니다.

결과값은 아래처럼 받을 수 있습니다.

.. code-block:: json

  {
    "status": "200",
    "item": {
      "url": "http://oauth.tistory.com",
      "secondaryUrl": "",
      "id": "1",
      "title": "티스토리 OAuth2.0 API 오픈!",
      "content":
        "안녕하세요 Tistory API 입니다.<br><br>이번에 Third-party Developer 용 <b>Tistory OAuth 2.0 API</b> 가 오픈됩니다.",
      "categoryId": "0",
      "postUrl": "http://oauth.tistory.com/1",
      "visibility": "0",
      "acceptComment": "1",
      "acceptTrackback": "1",
      "tags": {
        "tag": ["open", "api"]
      },
      "comments": "0",
      "trackbacks": "0",
      "date": "1303352668"
    }
  }

파일 첨부
--------------

파일을 첨부 할 수 있는 API입니다. 해당 API에 관한 정보는
`파일 첨부 API <http://www.tistory.com/guide/api/post.php#post-attach>`_ 를 통해
살펴보실 수 있습니다.

.. code-block:: python

  from pytistory import PyTistory

  pytistory = PyTistory()
  pytistory.configure()

  response = pytistory.post.attach('./path/to/uploading/file', blog_name='sampleUrl')

인자값은 파일의 경로와 블로그의 이름을 받습니다. 스트림을 통한 업로드는 추후 구현예정입니다.

결과값은 아래처럼 받을 수 있습니다.

.. code-block:: json

  {
    "status": "200",
    "url": "http://cfile6.uf.tistory.com/image/1328CE504DB79F5932B13F",
    "replacer":
      "%5b%23%23_1N%7ccfile6.uf%401328CE504DB79F5932B13F%7cwidth%3d\"500\"+height%3d\"300\"%7c_%23%23%5d"
  }


글 삭제
--------------

**이 API를 사용하기 위해서는 사전 협의가 필요하다고 합니다.**

단일 게시글을 삭제할 수 있는 API입니다. 해당 API에 관한 정보는
`글 삭제 <http://www.tistory.com/guide/api/post.php#post-delete>`_ 를 통해
살펴보실 수 있습니다.

.. code-block:: python

  from pytistory import PyTistory

  pytistory = PyTistory()
  pytistory.configure()

  response = pytistory.post.delete(1, blog_name='sampleUrl')

인자값은 글의 번호와 블로그의 이름을 받습니다.

결과값은 아래처럼 받을 수 있습니다.

.. code-block:: json

  {
    "status": "200"
  }
