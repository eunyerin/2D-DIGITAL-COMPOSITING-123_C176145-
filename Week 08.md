# <WEEk 08. IBK Gizmo & Color grade etc>


## Keying 크리틱

1. 키 작업 후 확인을 해야 한다. 감마키-체크보드
2. 초록색 뭍은 것은 despill을 통해 빼주거나 hue correction으로 조정을 해준다.
3. 원본 플레이트는 그대로 내려와야 한다. 키 작업의 목적은 알파를 추출해 원본에 넣어주는 것.
4. 원본이 손상되는 것을 막아야 하고 이에 집착해야 한다..
5. 하드 매트와 소프트 매트를 통해. erode: 소프트 키와 하드 키를 합칠 때 생기는 것들을 줄여주기 위해


## Grade

![gradeNode](https://user-images.githubusercontent.com/112792903/208253386-b255a343-b99b-4119-a0fd-34c8b41ae569.png)

1. merge 노드 A, B input
2. 파일 외장하드: preference-localization (외장하드의 무거운 파일들을 local에 복사하는 기능. storage용량을 늘려주기 60GB) Localization policy on하면 푸티지 초록색으로 바뀜.
3. Grade 노드: 화이트 밸런스를 맞추는 역할을 할 수 있음. 
4. lift: 어두운 부분을 올리는 것. 밝은 부분은 영향이 별로 없음. 제일 먼저 어두운 정도를 맞춰줌
5. Gain: 밝은 영역에 영향을 많이 줌. 밝은 부분이 훨씬 더 밝아짐.
6. Multiply: Gain과 유사하지만 RGB각각의 수치들의 값을 수정해줌.
7. offset: 그래프가 그대로 옆으로 이동, 전부 밝아지거나 어두워짐. 
8. Gamma: shadow와 highlight의 중간 톤을 관리하는 부분. 가능하면 감마는 잘 건들지 않는 편.
9. 최종 렌더 할 때 모든 값이 1 이상으로 가지 않도록 주의.


<기능 추가 소개>
1. blackpoint / whitepoint : 이미지의 들어오는 흑백을 실제 흑백, 0 및 1로 다시 매핑하는 데 사용된다. 
2. Clamp : Grade를 사용하여 값을 다시 매핑하면 이미지에서 가장 어두운 픽셀을 제외한 다른 픽셀을 샘플링하는 것처럼 검정 값이 음의 영역으로 빠르게 내려간다. 
   그러면 어두운 값이 0보다 작게 설정됩니다. 이러한 이유로 이미지 조정을 적용한 후 Nuke는 기본적으로 검정색 클램핑으로 설정됩니다.
   노이즈 또는 음의 방향으로의 변위에 사용되는 다른 지도를 다시 매핑하는 경우 이 상자를 열어야 합니다. 
   (출처. https://www.chrisbturner.com/blog/nukes-grade-node-demystified)
 

## 색이 매치되지 않은 상황일 경우

![gradeNode](https://user-images.githubusercontent.com/112792903/208253753-84181747-3c9a-466e-95e5-d9dfe46c2fc2.png)

1. 프로젝트 세팅에 포맷
Constant에 작업을 시작 -> 머지 노드로 합치기 -> 머지에서 set box to B(B가 가지고 있던 크기로 맞춰줌) -> 이미지가 720에 전부 들어오게 하고 싶다 transform: 원하는 위치에 이미지를 놓을 수 있음+filter를 cubic 걍 건들지 말아라, reformat: resize type에서 (nuke node concatenation) -> 푸티지 2개의 사이즈가 안 맞으면 crop을 하거나 reformat을 해야. black outside는 밖의 영역은 그냥 블랙으로. 리사이즈 none+black outside -> 이렇게 한 후 로토 작업 아님 로토 작업 후 transform

-> w키 merge a, b에 놓고. -> rgb 개별 채널로 놀고 보라-> 항상 어두운 부분부터 작업-> 0.0a -> gain 수치 밝은 부분 -> 노드 그룹 backdrop node -> 로토 알파-> premult -> 저 두 플레이트 사이에 연기 소스 -> 머지 -> 노드 그래프 정리 중요

-> 포토샵 png로 한 후 누크 합칠 때는 pre multi     

## Color correct node
saturation 정도만 사용하는 것이 좋음. 심지어 saturation node가 따로 있음.

