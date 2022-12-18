# <WEEK 11. Manipulate 3D Images>

## CornerPin

![maxresdefault (2)](https://user-images.githubusercontent.com/112792903/208293650-68a3e64e-5e53-47f5-b457-4387828c0c37.jpg)

CornerPin2D 노드는 추적 데이터에서 추출한 위치에 영상 시퀀스의 네 모서리를 매핑하도록 설계되어있음.
실제로 이 노드를 사용하면 4개의 핀을 활용하여 다른 영상 시퀀스로 바꿀 수 있습니다. 예를 들어, 사각형 형태를 지닌 컴퓨터, TV, 광고판 등을 바꿀 수 있음.
이 노드를 사용하기 전에 Tracker 노드를 사용하여 교체가 필요한 위치에 대해 코너당 하나씩 4개의 트랙을 생성해 T, R, S 수치값을 얻어야 함.

- 예시로 휴대폰을 터치하는 코너핀을 제작할 경우. 손가락이 위에 올라와야 함으로 로토로 따로 잡아주어야 함.
- 정확한 수치값을 붙이기 위해 Set to input과 Copy to 버튼을 누르자.
- 코너핀 이미지, 교수님 핸드폰에 푸티지 합성한 것으로 연습.
- 코너핀 원본의 영역을 넘어간다. 그러나 이는 프로젝트의 해상도가 넘어가서. from=set to input-이미지가 있던 원래의 해상도 위치로.
- 이미지를 강제로 맞추려면 to=copy 'from'을 원본의 플레이트와 맞추어 주기
- 코너핀 투디를 핸드폰 화면에 맞추어 준다. from은 건드릴 필요 없음. 원본을 화면에 맞추어 준다. 레퍼런스 프레임을 잘 맞추는 것이 중요함.
- 한 번에 끝나는 경우는 없음. 한 두 픽셀 밀리는 경우 있음. 프레임을 잡아주어야 한다,
- 프롬에서 점들 물결표시 (창 띄우고 맨 위의 것) 옆 엑스 눌러주기. 프레임을 넘어가며 로토처럼 일일이 맞추어 주기.
- 플레이트를 stablize를 해서 하는 방법도 있음.
- 움직임을 주지 않아도 멈춰있는 것을 하는 방법, transform stablize. invert 버튼을 눌러주면 다시 원본으로 만드는 매치 노드 사이에 넣어주기
- 컬러의 대비도 맞춰주면 더욱 좋음. 


## 3D Camera Tracking

![maxresdefault (3)](https://user-images.githubusercontent.com/112792903/208293873-0b9ee955-fab7-4fa0-839c-759f9f7fbb63.jpg)

Nuke의 CameraTracker 노드는 내장 카메라 추적 또는 매치 이동 도구로 구성되어 있음. 원래의 카메라와 같은 움직임을 가지는 가상 카메라를 만들어 내는 것.
2D 영상으로 카메라의 움직임을 추적하면 2D 영상에 가상 3D 객체를 추가할 수도 있음.
CameraTracker 노드를 사용하여 카메라 동작을 2D 시퀀스 또는 스틸로 추적하여 애니메이션 3D 카메라, 예를 들어 구름이 떠다닌 등 장면을 만들 수 있음.

준비해야 할 노드

![ct2_create_scene2](https://user-images.githubusercontent.com/112792903/208294284-944f2931-ffcb-4f90-b03b-6a05e379809d.png)


각 3D 장면에는 Scene, Camera, Card, ScanlineRender이 필요함. Scene노드는 Card 노드로부터 출력하여 이러한 객체의 합성을
ScanlineRender 노드로 전송하면 Viewer에 연결시키면 완성

- Camera : Scene 노드 와 ScanlineRender(스캔라인 렌더) 노드에 연결할 수 있습니다. ScanlineRender 노드에 연결된 카메라는 렌더링에 사용되는 카메라임.
 
 (과정)
 
   1.3D > Camera를 선택.
   2. Camera 노드에서 Scene 노드로 드래그 연결 혹은 Camera 노드를 ScanlineRender 노드에 연결.
      
- Scene : 스크립트에서 위치에 관계없이 3D 작업영역의 모든 요소에 필요한 것. 
- Card : 사용하고자 하는 객체. Sphere Cube 다양하게 있음
- ScanlineRender : 스크립트의 모든 scene 노드는 스캔라인렌더 노드에 연결해야 함. 
                   스캔라인렌더 노드는 누크에 씬scene 결과를 렌더링하도록 지시해줌.
                   ScanlineRender 노드를 사용하여 씬에서 2D와 3D를 전환하며 볼수 있음 (Tab 키) 
