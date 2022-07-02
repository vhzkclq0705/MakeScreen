# MakeScreen
## 케이스 스터디 1주차 과제(UI Component와 오토레이아웃 공부하기)
- TableView와 CollectionView를 제외하고 코드 한 줄 없이 기본 UI 컴포넌트와 오토레이아웃으로 임의의 앱 화면 구현
- 깃허브 앱의 화면을 구현하기로 결정
- Constraint와 색을 정확하게 구현하기 힘들다고 판단하여 최대한 비슷하게 구현
- ScrollView와 ContainerView를 활용하였다.
- 코드로 구현해야 하는 부분을 제외하고 모두 구현하였다. ex) 스크롤 내리면 Navigation Bar에서 border와 Title 보이게 하기 등

## 결과

<details>
  <summary> 스토리보드 </summary>
  <div markdown="0">

![스토리보드](https://user-images.githubusercontent.com/75382687/176928197-35f79d23-571f-4d7c-b5cf-b021901effda.png)

- 우측 하단은 수정하기 전에 작업해논 결과물이 아까워서 내비뒀다.

  </div>
</details>

<br>

## 실행 화면 비교

|Github|MakeScreen|
|---|---|
|![github](https://user-images.githubusercontent.com/75382687/176928173-4c4e8b65-906e-4885-91c6-a88bae390c8d.gif)|![MyScreen](https://user-images.githubusercontent.com/75382687/176928190-c70431b0-5428-44e8-971d-0571f4f415be.gif)|

## iPhone 8 / iPhone 13 Pro Max

|iPhone 8|iPhone 13 Pro Max|
|---|---|
|![iPhone8](https://user-images.githubusercontent.com/75382687/176930804-bf774fa7-ccab-45ec-aa92-9d08dd99874f.gif)|![iPhone13ProMax](https://user-images.githubusercontent.com/75382687/176930815-69bc2ff8-d19f-48f2-b4fc-3037c52af9b3.gif)|

<br> 

## Priority 수정 작업
- 이미지 크기가 고정이라고 가정.
- ProfileInfoStackView
    - 각 StackView 내부 이미지의 Content Hugging Priority를 500으로 설정.   
    → 이미지의 크기가 바뀌지 않도록 우선순위를 높게 설정하였다.
    - 가장 밑의 StackView
        - text가 following인 label의 Content Hugging Priority를 200으로 설정.  
        → SuperView에서 20만큼의 trailing Constraints를 지정해 주면, 가장 마지막 label로 남은 간격을 채워 나머지 label의 크기가 바뀌지 않도록 설정하였다.
- MiddleView 내부의 StackView
    - 가장 우측 버튼의 Content Hugging Priority를 200
    가운데 label의 Content Hugging Priority를 250으로 설정.   
    → 해당 label의 text는 바뀌지 않기 때문에 우선순위를 더 높게 설정하였다.
- PinnedView
    - 내부 StackView의 높이가 고정이라고 가정.
    - StackView 내부 가장 아래 레이블의 Content Compression Resistance Priority를 500으로 설정.  
    → 폰트가 가장 작은 부분이어서 높이가 줄어들어도 문제가 없다고 생각했기 때문에 우선순위를 가장 낮게 설정하였다.
    - 가장 아래 StackView의 text가 Swift인 label의 Content Hugging Priority를 200으로 설정.  
    → 해당 StackView 내부의 UI Componente들을 왼쪽으로 정렬해주기 위해서 가장 우측 label의 우선순위를 낮게 설정하였다.

## 새로 알게된 점
- Navigation Bar와 Tab Bar의 뚜렷한 색상을 설정해주기 위해서는 Translucent 속성을 false로 해주어야 한다.
    > Translucent: Navigation Bar의 반투명 여부를 설정하는 인스턴스 속성


## 느낀 점

- 최근 대부분의 구현을 코드로만 하다보니 스토리보드에서 직접 오토레이아웃을 설정하는 것이 너무 힘들었다.   
- 스토리보드로 구현을 했을 때, StackView의 오토레이아웃 설정이 제일 어려울 것이라 생각하여 StackView를 최대한 많이 사용하였다.   
- TableView나 CollectionView 없이 구현해야 했기에, 생각보다 많은 UI Component가 필요했다.      
- 이번 과제 덕분에 Content Hugging Priority, Content Compression Resistance Priority를 설정하는 방법과 이유를 알게 되었다.     
- 완전하게 똑같진 않지만, cornerRadius나 border를 스토리보드에서 설정해 줄 수 없기 때문에 Filled 속성의 버튼과 높이 0.3인 View들을 사용했다.  
