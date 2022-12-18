# <WEEK 13. Weekely Research>

## Copycat Node

![maxresdefault](https://user-images.githubusercontent.com/112792903/208295923-94906692-c955-4c80-913e-3fafd7206c92.jpg)

CopyCat (NukeX 및 Nuke Studio에만 해당)은 Garbage matte, deblurring과 같은 시퀀스별 효과를 시퀀스에 따라 복사한 다음 
네트워크를 훈련시켜 전체 시퀀스에 이 효과를 복제함.


## Nuke Ai Node

- CopyCat : 시퀀스 내의 소수의 프레임에 효과를 생성하여, CopyCat 노드를 사용하여 효과를 복제하도록 네트워크를 훈련할 수 있음. 
            클라우드로 데이터를 전송하지 않고도 Nuke 내에서 고품질의 맞춤형 모델을 비교적 빠르게 생성할 수 있음.
            
- Inference : Copy Cat에 의해 생성된 신경 네트워크를 실행하는 노드이며, 모델을 이미지 시퀀스 또는 다른 시퀀스에 적용.

- Upscale & Deblur :  공통 컴포지트 태스크를 위한 두 가지 새로운 툴이 CopyCat과 오픈 소스 ML-Server의 ML 방법론을 사용하여 개발되었음. 
                      이러한 노드의 ML 네트워크는 CopyCat을 사용하여 보다 고품질의 샷 또는 스튜디오 고유의 버전을 만들 수 있으며, 
                      비디오 크기 조정 및 모션 블러 제거에 주로 사용됨.
                      
  (출처. https://www.fxguide.com/fxfeatured/copycat-inference-machine-learning-in-nuke/)
