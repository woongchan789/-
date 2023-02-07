소장님(Sojangnim)
---
Last modified: 2023.02.07

<p align="center"><img src="https://user-images.githubusercontent.com/75806377/216811389-71c9f2a4-501c-4842-9ea0-dc6b21ea1ff7.png"></p>  

'소장님'은 집에서도 간편하게 캡슐내시경 검사가 가능할 수 있도록 시작된 프로젝트입니다.  
캡슐내시경이 전송한 소장의 사진을 토대로 병변 검출을 object detection model을 진행하며  
어플리케이션 내에서 진단 결과를 확인할 수 있으며 내원하여 검사에 소요되는 전체적인 시간비용을 절감하고자  
캡슐내시경 검사 시작부터 내원 및 퇴원까지에 이르는 전체적인 프로세스를 고려하여 어플리케이션을 설계하였습니다.  

Background
---
소장의 경우 위와 대장 사이에 위치하여 소장 검사에 많은 어려움이 존재합니다.    
하지만 캡슐내시경이 개발이 되면서 소장의 병변을 사전에 검출하여 사전치료 및 검사가 가능해졌는데요.  
캡슐내시경이 전송한 소장의 사진을 통해 소장 내 궤양, 림프종 같은 병변을 사전에 검출하여
이제는 대장내시경과 같이 캡슐내시경 검사가 흔한 검사 방법으로 많이 사용되고 있습니다.  

하지만 여전히 캡슐내시경의 단점은 존재합니다.  
캡슐내시경이 전송한 소장의 사진을 통해 병변을 판독하고 검사하는데 있어 전문 의료진의 개입 및 판단이  
필요하기에 입원에서 진단까지의 최종 프로세스 과정에 대략 2주 정도 긴 시간이 소요된다는 단점이 존재합니다.

이 점에서 착안하여 본 연구는 시작되었습니다.  
COVID-19로 인하여 재택 안에서 모든 것들을 수행할 수 있는 서비스들에 대한 수요가 증가하였기에  
'캡슐내시경 검사도 집에서 하면 좋지 않을까?'라는 아이디어를 가지고 develop 해보았습니다.

Service Flow
--- 

<p align="center"><img src="https://user-images.githubusercontent.com/75806377/217163965-776d5a0a-4827-4117-969c-d9a7252bb58e.png" height="500px" width="1000px"></p>

Object detection
---
캡슐내시경이 이미지 저장 장치로 발신한 사진을 통해 검사가 시작됩니다.  
소장 내 어떤 병변이 있는지 detection을 하는 단계인데요.  
본 프로젝트에서는 object detection model 중 yolov5와 mmdetection 그리고 cbnet을 활용하였으며  
다양한 실험을 통해 정확도가 높았던 model들을 ensemble하여 최종 모델로 채택하였습니다.  
ensemble을 진행할 때는 WBF(Weighted Box Fusion)방식으로 ensemble을 진행하였습니다.  
</br>
<p align="center"><img src="https://user-images.githubusercontent.com/75806377/217166025-dd8779c9-6f77-437c-85e7-8406367c4240.png" height="800px" width="1000px"></p>

#### Accuracy(box_loss, obj_loss, cls_loss)
---
![image](https://user-images.githubusercontent.com/75806377/217166864-3f7ff8f1-bdb4-4417-a236-d5a2f3de895f.png)
![image](https://user-images.githubusercontent.com/75806377/217166928-c68e8471-64f7-48e3-92a7-32c278dea5cd.png)
![image](https://user-images.githubusercontent.com/75806377/217166980-8dba67f8-44d2-464c-ad3c-ebaf99ee2b90.png)

#### Applicatoin prototyping
---
<p align="center"><img src="https://user-images.githubusercontent.com/75806377/216810773-fa0e1932-9fcb-4e7d-88a0-4da225a6aefe.gif" height="400px" width="250px"></p>  

![image](https://user-images.githubusercontent.com/75806377/217167648-2a8a0ef4-c867-42dc-99ed-f3609350c190.png)
![image](https://user-images.githubusercontent.com/75806377/217167784-6296120b-f661-4b73-ad53-54fa431a5e46.png)
![image](https://user-images.githubusercontent.com/75806377/217167825-14c41f56-0b47-4314-8b0d-7ec3189e2185.png)



