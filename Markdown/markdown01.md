# MARKDOWN - 23/08/29
### Markdown 이란 ?
- 마크다운은 웹상에서 글을 쓰는 모든 사람들을 위한 **글쓰기 도구(서식, 포맷, 양식)** 이다.
- 마크다운은 쉽게 글을 쓸 수 있도록 해주고 읽는 사람에게도 쉽게 읽힐 수 있도록 해주는 서식이다.
- ***.md 확장자**를 사용하며 오픈소스, 프로젝트 소개 등 다양한 곳에 활용됨
  
## Markdown 문법
### 1. Heading(제목)
글머리 1 ~ 6개까지 작성 가능

```
# H1
## H2
### H3
#### H4
##### H5
###### H6
```

# H1
## H2
### H3
#### H4
##### H5
###### H6

### 2. Paragrapgh (내용)
  줄바꿈 / 문단 나누기

- `Enter` 두 번 입력
- 문장 마지막에서 **3칸 이상 띄어쓰기**하기

### 3. List (목록)
#### 3.1 순서가 있는 리스트 (Ordered List)
**숫자 입력 후 한번 띄어쓰기하기**   
소분류도 사용하고 싶다면 다음줄에 `Tab`을 사용해 다시 지정할수있다. (순서가 없는 리스트도 동일)   
1. 파이썬
    1. Pandas
    2. Tenserflow
2. 자바 
    1. JavaScript
3. C
4. SQL

#### 3.2 순서가 없는 리스트 (Unordered List)
**"-" 입력 후 한번 띄어쓰기하기**   
- 파이썬
- 자바
- C
  - C++
- SQL
  - Oracle
  - Mysql

### 4. Emphasis (내용 강조)
- 굵게 : * 두개로 감싸기(\*\*bold**) = (**bold**)
- 이탤릭체 : * 한개로 감싸기(\*italic\*) = (*italic*)
- 코드 강조 \`(백틱) 한개로 감싸기(\`code\`) = (`code`)

### 5. Table (표)
- **" | "** 를 활용해 칸을 나눌 수 있다. - **|text|**
- **" - "** 를 활용해 줄을 나눌 수 있다. - **|-|**

```
|이름|나이|전공|
|---|---|---|
|김김김|25|`컴공`|
|이이이|27|경영|
|박박박|30|기계|
```

|이름|나이|전공|
|---|---|---|
|김김김|25|`컴공`|
|이이이|27|경영|
|박박박|30|기계|

### 6. Code Block (코드 블록)
코드 블록은 프로그래밍 코드를 삽입할 경우 사용되며, 보기 좋게 코드를 삽입할 수 있다.

Back tick(`) 문자 세 개(```)를 코드의 위아래에 삽입한다.

```
(```)   
mkdir aaa   
cd aaa   
touch b.txt   
(```)
```

```   
mkdir aaa   
cd aaa   
touch b.txt   
```

### 6.1 언어 지정 코드 블록 
Back tick(`) 문자 세 개 뒤에 코드의 언어를 입력하면 자신이 사용하는 코드의 환경에 맞게 코드를 삽입할 수 있다.

```
(```python)
a = 1
b = 2
c = a + b
print(c)

def func():
    return 1
(```)
```

```python
a = 1
b = 2
c = a + b
print(c)

def func():
   return 1
```

### 7. Quote (인용문)
**">"** 을 사용해 사용하고 싶은 인용문구를 작성할 수 있다.

**\>** 일하는 시간과 노는 시간을 뚜렷이 구분하라. 시간의 중요성을 이해하고 매 순간을 즐겁게 보내고 유용하게 활용하라. 그러면 젊은 날의 유쾌함으로 가득찰것이고 늙어서도 후회할 일이 적어질것이며 비록 가난할 때라도 인생을 아름답게 살아갈수있다.   
**\>**   
**\>** 루이사 메이올콧

> 일하는 시간과 노는 시간을 뚜렷이 구분하라. 시간의 중요성을 이해하고 매 순간을 즐겁게 보내고 유용하게 활용하라. 그러면 젊은 날의 유쾌함으로 가득찰것이고 늙어서도 후회할 일이 적어질것이며 비록 가난할 때라도 인생을 아름답게 살아갈수있다.
>
> 루이사 메이올콧

### 8. Mathematical Expression (수식)

#### 8.1 줄 수식
글 도중에 수식을 넣으려면 수식 양쪽에 **"$"** 특수문자를 사용한다.


- 글 도중에 수식을 넣으려면 **\$x + y\$** 이렇게 합니다.

- 글 도중에 수식을 넣으려면 **$x + y$** 이렇게 합니다.

#### 8.2 블록 수식
**"$$"** 특수문자를 처음과 끝부분에 사용해 블록 수식을 지정할 수 있다.


\$$ 5x + 2y = 3 $$


$$ 5x + 2y = 3 $$

### 9. Link / Image (링크 / 이미지)
1. Link - [표시텍스트]\(링크)
  ```   
   - [마크다운 링크 알아보기!](https://lynmp.com/ko/article/title/markdown-link-ua811c9dc59o)
  ```
  
  - [마크다운 링크 알아보기!](https://lynmp.com/ko/article/title/markdown-link-ua811c9dc59o)

2. Image - ![대체텍스트]\(링크)   
   ```
   - ![마크다운 이미지](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAT4AAACfCAMAAABX0UX9AAAAbFBMVEX///8AAADT09NISEg4ODjQ0NAeHh7W1tYRERH5 ...)
   ```

   - ![마크다운 이미지](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAT4AAACfCAMAAABX0UX9AAAAbFBMVEX///8AAADT09NISEg4ODjQ0NAeHh7W1tYRERH5+flnZ2dZWVkYGBiwsLDy8vKYmJjo6OjIyMj19fXCwsIvLy+QkJC3t7eqqqpFRUXj4+MNDQ2fn59NTU2Dg4NdXV0qKiojIyN9fX1ubm48PDw6tcSpAAADi0lEQVR4nO3da3eaMACA4cSqoGuZtWrFWm/9//9xp1wDhOAaDKfkfT5tJS2Hd1YwXCYEAAAAAAAAAAAAAAAAAAAAAAAARiwKJk4Fq6G3uEfr7ZN0bL+Nht7qvry5bpfaDb3d/dgNU0/K96G3vA+ToepJ+Tr0tttbH4fLt//973/5G1/4NXVnnq3097/9ndINeXO71tcwffm5XesDPCfb8eF6te/pv5rr1fYu/c2duF5tMB9Tvpnr1ZLPCvmskM8K+ayQzwr5rJDPynjzxUGp7TN9pIzRThwvlAGBZvlo8y3+HJ5zh5O+33oalmOWuhErWQwIz5ofMuJ86pzSp/abluqQlnylub/5tJMJ28oI8hnyyeZepXZuhHymfJf6riGoLiefMZ98qn5DVJ/dJ58xX233caovJp85X+WM4raxlHwd+WR54Ks5KUy+rnyXOFsYN5eRrzOfPGXL9uSrui+fvCbLGrsN8t2XL9l9/NUuId8d+Q4z8apdQL578snD5Ey+hrvztSIf+X7KnG8u9Z7JlzLne9MeqsirOmdFvtZ8O93HDDmNPv4r37q53I98L9qjlVnlCLDIt1iUP0XNd1G+npf0JZ/mWHkn9Pmi06a4fnSjfkP55fMtG+tNvup5IZlO/2nzaScUqoqrmf3JJyqvJLn8/lXU5xPxxVxvU4z0KF9QiZK8flryiZmx3jkuBnqUT919hGmBtnzGO5TmyuUGPuUTH/UvtObLr/nWUa/e9yqfuGV/v2Z/b8/XMqul/KyEX/mifbWUIZ+43lHPs3zpYfCmOGNuytc40klsq2M8y5fsPsq3fmM+oZmzqdXzLp/Yqqd7zfnWjburb/Uh3uUT6p/N+cR6Wqu3qI/wL5+qI5+IK59Ujs0ZK/KZ8omZMqG60Vy+Sz5jPuWTyibWLCafOZ94yZfr6pGvK19+NZH+ngfydeVLr2VruU2dfJ35vvu1PWxkzPnCzKF167fFmDC/+kpjsdTf1yBGnE/Es1LbXUUrZYx215BqHC0XxpvPCfJZIZ8V8lkhnxXyWSGfFfJZGVc+nmH1Q+mT4Jw/BzObznK92t6lEwQHx7+92Yvvy+1aHyC/KOV8fHLmmJ8JaZvQ+T0adzc79DWCh1+bryl7KMdP/HwMwzVRj+X8iZ+PMdBzr0fx1Otv0ee0e2v7Nf0cwfteYcX/mAAAAAAAAAAAAAAAAAAAAAAAAIAe/QPfUjco97t4cwAAAABJRU5ErkJggg==)

