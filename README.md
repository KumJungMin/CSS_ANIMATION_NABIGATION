# hover시 글자색이 변하는 메뉴 애니메이션

## 1. preview

<img src="https://j.gifs.com/5Qkq6K.gif" />


## 2. 코드 분석

### 1) html

#### (1) gnb안에 4개의 a태그를 자식으로 한다.
```html
<body>
    <div class="gnb"> 
        <a href="">MENU</a>
        <a href="">SIGNUP</a>
        <a href="">INTRODUCE</a>
        <a href="">CALL</a>
    </div>
</body>

```

<br/><br/>

### 2) css

#### (1) gnb와 gnb a의 설정
- gnb를 세로 중앙(세로 중앙)에 위치시키기

  : `position:absolute`을 하여 top, left값 사용이 가능하게 한다.
  
  : `top : 50%` `transform: translateY(-50%)`을 해서 브라우저 크기에 맞춰 항상 세로 중앙 되게 한다.

<br/>

- gnb a태그에 이벤트 발생 시간 설정

  : `transition: 0.5s`을 해서 a에 이벤트가 발생시 0.5초 뒤에 일어난다는 사전설정을 한다.

```css

      body{
            background-color: royalblue;     /*배경색*/
            margin: 0;
            
        }

        a{
            color: #222;                    /*a 태그 디자인*/
            text-decoration: none;
        }
        
        .gnb{
            position:absolute;             /*수직중앙주기(1)*/
            top : 50%;                     /*수직중앙주기(2) -> 브라우저 크기에 맞춰 항상 중앙*/
            transform: translateY(-50%);   /*수직중앙주기(3)*/
            left : 50px;
        }
        
        .gnb a{
            display: block;                /*새로로 일렬*/
            font-size: 40px;
            margin: 15px 0px;              /*상하 좌우*/
            color : #fff;
            transition: 0.5s;              /*이벤트 발생시간 설정*/
        }

```

<br/>

#### (2) 메인 효과 설정하기
- 메인효과들은 코드들이 순서대로 작동해야한다.
- 그러므로 먼저 전체 투명도가 낮아져야하는 경우 -> 메인효과1 코드를 메인효과2보다 위에 써줘야한다.

- 메인효과1 (gnb에 hover시 a에 이벤트 발생)
  
  : gnb에 마우스가 올라갔을 때 전체 메뉴의 글자(a태그)의 투명도가 낮아지게 한다.

<br/>

- 메인효과2 (특정 a태그에 hover시 그 a태그만 밝게)

  : `.gnb a:hover`을 사용하여 gnb의 자식인 a태그에 hover시 투명도를 높인다.
  
<br/>

- 장식용 가상 클래스(before)

  :  마우스가 특정a에 올라갔을 때 나타나는 화살표이다.
  
  : gnb의 자식인 a태그에 hover가 되면 `before`의 투명도가 1이 된다.
  
```css
        .gnb:hover a{        /*메인효과1*/
            opacity: 0.3;   
        }
        
        .gnb a:hover{        /*메인효과2 : 특정 a만 밝게*/
            opacity: 1;
        }
        
        .gnb a:before{       /*장식 클래스*/
            content: '>';
            margin-right: 10px;
            opacity: 0;
        }
       
        .gnb a:hover:before{ /*장식 클래스에 hover이벤트 적용*/
            opacity: 1;
        }

```















