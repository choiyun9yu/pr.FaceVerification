# Face Recognition with ArcFace

## 개요
딥러닝에서 얼굴과 관련된 기술은 크게 두 가지로 나눌 수 있다.  
사진이나 동영상에서 얼굴의 위치를 찾는 얼굴 검출(Face Detaction)과  
얼굴의 동일인 여부를 판단하는 얼굴 인식(Face Recognition)이 그것이다.  

여기서 얼굴 인식은 다시 2가지로 나뉘게 된다. 하나는 1:1 검증으로  
두 장의 얼굴 사진으로 서로 동일인인지를 판단하는 얼굴 검증(Face Verification)이고,    
다른 하나는 1:N 검증으로 새로 들어온 얼굴 사진이 기존에 존재하는 DB에 있는 사람인지를  
판단하는 얼굴 식별(Face Identification)이다.

본 프로젝트는 얼구 검증 프로젝트로서 신분증 사진과 얼굴 사진을 비교하여 동일이 여부를   
판단하는 딥러닝 모델을 만들고자 했다.  


## 얼굴 검증 모델의 구조 
얼굴 검증 모델은 두 장의 사진을 Input하면 그곳에서 각각 먼저 얼굴을 검출한다.  
얼굴을 검출한 뒤 특징을 뽑기 위해 사전 훈련된 backbone network에 넣어서  
특징을 추출하게 된다. 이때 특징을 더 잘 추출하기 위해서 얼굴을 정렬하는 등의  
전처리를 할 수 있다.

전처리와 backbone을 지나면 각 얼굴 사진들의 Embedding Vector가 추출된다.  
이 벡터간의 거리차이로 두 얼굴의 동일인 여부를 결정한다. 거리차이가 임계값(Threshold)를  
넘어가면 비동일인, 임계값을 넘지 않으면 동일인으로 판단하는 것이다.  


## 내용
본 프로젝트에서는 사전 학습된 얼굴 인식 모델들 중에서 가장 정확도가 높은 모델을 선정한 후  
임계값을 최적화하여 정확도를 높이는 방법을 사용하였다.  

오픈소스 : https://github.com/serengil/deepface
