## Partial

특정 타입의 부분 집합을 만족하는 타입을 정의할 수 있다<br>
Partial는 상품의 정보를 업데이트할때 많이 쓰인다<br>
옵셔널 ? 를 사용하지 않고 인터페이스를 재활용할 수 있어 중복을 줄일 수 있고, 더 간결하게 표현이 가능하다.

```ts
// 기본 프로덕트
interface Product {
  id: number;
  name: string;
  price: number;
  brand: string;
  stock: number;
}

// optional을 사용한 코드(같은 내용을 두번 사용해야함)
interface UpdateProduct {
   id?: number;
   name?: string;
   price?: number;
   brand?: string;
   stock?: number;
 }
 
// 27줄 단 한줄로 18-24줄을 대신할 수 있다. 또는 productItem의 타입을 한번 보기
type UpdateProduct = Partial<Product>
// or
function updateProductItem(productItem: Partial<Product>) {
 // ...내용
}
```

## 변환과정을 통해 Partial의 타입 구현 내용
다음 밑의 코드를 파티셜 사용하기 전까지 변환해보자
```ts
interface UserProfile {
  username: string;
  email: string;
  profilePhotoUrl: string;
}

//옵셔널 체이닝 사용
interface UserProfileUpdate {
   username?: string;
   email?: string;
   profilePhotoUrl?: string;
 }
```

### 첫번째 구현

```ts
//옵셔널 체이닝 사용
type UserProfileUpdate = {
  username?: UserProfile['username'];
  email?: UserProfile['email'];
  profilePhotoUrl?: UserProfile['profilePhotoUrl'];
};
```

### 두번째 구현

반복문을 돌린다,
뒤에 optional 추가
```ts
type UserProfileUpdate = {
  [p in 'username' | 'email' | 'profilePhotoUrl']?: UserProfile[p]
};
```

### 세번째 구현

키값을 가져온다

```ts
// let updateProfile: keyof UserProfile 은  username | email | profilePhotoUrl 완벽하게 호환된다.

type UserProfileUpdate = {
  [p in keyof UserProfile]?: UserProfile[p];
};
```

### 네번째 구현
파티셜 형태와 마지막 구현모습이 같은걸 볼수 있다

```ts
type Subset<T> = {
  [P in keyof T]?: T[P]
};
```
![partial 형태](https://user-images.githubusercontent.com/80729831/137950080-2abd21c1-3865-4e06-8d33-513a95d48ac5.png)


