# MPA vs SPA, SSR vs CSR

## 목차
- MPA vs SPA 
- SSR 개념과 동작과정, 장단점
- CSR 개념과 동작과정, 장단점
- 구동방식 선택기준 


![SSR vs CSR 002](https://user-images.githubusercontent.com/80729831/139271230-cda9493c-aef3-4e8f-8f40-d30a1c15f36e.jpeg)

## MPA
- multi page application의 약자로 여러 페이지로 구성된 웹 어플리케이션입니다.
- 사용자의 클릭과 같이 인터렉션이 발생할 때마다 서버로부터 새로운 html을
- 받아와서 해당 링크로 이동하여 페이지 전체를 새로 렌더링하는 전통적인 웹 페이지 구성 방식입니다.

## SPA

- Single Page Application의 약자로 하나의 페이지로 구성된 웹 어플리케이션 입니다. 
- 브라우저에 최초에 한번 페이지 전체를 로드하고, 이후부터는 특정 부분만 Ajax를 통해 데이터를 바인딩하는 방식입니다.
- 단일 페이지 어플리케이션(SPA)는 현재 웹개발의 트랜드로 볼 수 있고, 우리가 배운 react와 vue, 앵귤러와 같은 자바스크립트 프레임워크등이 spa의 방식을 가지고 있습니다.
- 메뉴를 선택하면 메인 화면 부분 혹은 클릭한 부분만 바뀌는 그러게 사이트들은 SPA 입니다. 

그림에서 보는 것과 같이. Ssr은 새로운 파일을 불러오지만, csr은 json파일의 데이터만 받아오게 됩니다.

![SSR vs CSR 003](https://user-images.githubusercontent.com/80729831/139271652-1555c76f-ef2d-4a09-b00a-121bbfe88d61.jpeg)
![SSR vs CSR 004](https://user-images.githubusercontent.com/80729831/139271664-6e6258b4-530a-489f-b295-f2f665aae930.jpeg)
![SSR vs CSR 005](https://user-images.githubusercontent.com/80729831/139271671-26cb1b6f-5660-42a2-b032-75970cea631c.jpeg)
![SSR vs CSR 006](https://user-images.githubusercontent.com/80729831/139271675-896e3e7c-3e2a-4238-ab30-1489b7e261d9.jpeg)
![SSR vs CSR 007](https://user-images.githubusercontent.com/80729831/139271682-dc55b83d-4eb0-41fb-bbc1-ad9beae56595.jpeg)
![SSR vs CSR 008](https://user-images.githubusercontent.com/80729831/139271686-be506dad-20ed-424b-bab2-57a0fffb81c8.jpeg)
![SSR vs CSR 009](https://user-images.githubusercontent.com/80729831/139271691-5959b148-2da3-4483-9ef4-4ee4da8f6318.jpeg)
 

## 참고 자료
- https://www.sarah-note.com/%ED%81%B4%EB%A1%A0%EC%BD%94%EB%94%A9/posting2/
- https://velog.io/@kdo0129/SSR-CSR
- https://velog.io/@pkbird/Single-Page-Application
- https://www.excellentwebworld.com/what-is-a-single-page-application/
- https://www.youtube.com/watch?v=vM_zQLnlyKw
- https://www.excellentwebworld.com/what-is-a-single-page-application/
