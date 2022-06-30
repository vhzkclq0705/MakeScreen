# MakeScreen
## 케이스 스터디 1주차 과제
- 기본적인 UI Components만으로 autolayout을 활용하여 앱의 정적인 화면 구현
- 깃허브 앱의 화면을 구현하기로 결정
- Constraint와 Color를 정확하게 할 필요는 없다고 느껴서 비슷하게만 구현

## 결과

|Github|MakeScreen|Storyboard|
|---|---|---|
|![깃허브](https://user-images.githubusercontent.com/75382687/176746589-b5df5fa5-d9eb-4d85-9950-c03495867657.PNG)|![내꺼](https://user-images.githubusercontent.com/75382687/176750863-c3a0dae4-3327-4d2a-b69a-a7b41dd5ab87.PNG)|![스토리보드](https://user-images.githubusercontent.com/75382687/176746820-211a8183-c93e-4175-8637-d70ebc22556c.png)|

<br>

## 느낀 점
최근 대부분의 구현을 코드로만 하다보니 오토레이아웃을 설정하는 것이 너무 힘들었다.   
스토리보드로 구현을 했을 때, StackView의 오토레이아웃 설정이 제일 어려울 것이라 생각하여 StackView를 최대한 많이 사용하였다.   
TableView나 CollectionView 없이 View와 StackView로만 구현해야 했기에, 생각보다 많은 UI Componentent가 필요했다.      
이번 과제 덕분에 Content Hugging Priority, Content Compression Resistance Priority를 설정하는 방법과 이유를 알게 되었다.      
완전하게 똑같진 않지만, cornerRadius나 border를 스토리보드에서 설정해 줄 수 없기 때문에 Filled 속성의 버튼과 높이 0.5인 View들을 사용했다.   

## 개발 이슈
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
    → label의 text는 변하지 않는 값들이기 때문에 우선순위를 더 높게 설정하였다.
- PinnedView1, 2
    - StackView의 높이가 고정이라고 가정.
    - StackView 내부 가장 아래 레이블의 Content Compression Resistance Priority를 500으로 설정.  
    → PinnedView1, 2의 하단부를 맞춰주기 위해서는 가장 아래에 있는 label의 높이가 줄어들어도 상관이 없다고 생각했기 때문에 우선순위를 가장 낮게 설정하였다.
- PinnedView1
    - 가장 아래 StackView의 text가 Swift인 label의 Content Hugging Priority를 200으로 설정.  
    → 해당 StackView 내부의 UI Componente들을 왼쪽으로 정렬해주기 위해서 가장 우측 label의 우선순위를 낮게 설정하였다.
- PinnedView2
    - 위와 동일하나 Content Hugging Priority가 아닌 Content Compressio Resistance Priority를 500으로, 우선 순위를 가장 낮게 설정하였다.
