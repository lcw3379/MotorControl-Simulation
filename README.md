
# 1. DC모터

 DC모터 모델링은 해당 블로그를 참고하였다.

 https://ropiens.tistory.com/8

전동기의 에너지 변환 과정은 전기 시스템, 자계 시스템, 기계 시스템을 거친다.

먼저 전기시스템의 식은 다음과 같다.

Va=Raia+Ladiadt+ea

다음으로 자계시스템의 식은 다음과 같다.

F=Bli[N]
여기서 자계 B를 자속 ϕ로 변환하면 다음과 같다.
Tm=kTϕia
 
마지막으로 기계시스템의 식은 다음과 같다.

Tm=Jω˙+bω+TL

자계시스템과 합치면 아래의 식이 된다.

Kia=Jω˙+bω+TL(ω=dθ/dt)

해당 식을 라플라스 변환을 거친 후 블록 선도를 만들면 다음과 같다.

![image](https://github.com/lcw3379/MotorControl-Simulation/assets/127228208/41687f1c-8ec7-4348-aa10-cb1f38bb3a0e)

Maxon사의 dcx35l의 사양을 참고하여 다음과 같이 작성하였다.

![image](https://github.com/lcw3379/MotorControl-Simulation/assets/127228208/95b3203b-934c-412b-b8fd-950f344aabb6)


실행 결과는 다음과 같다. 정격속도인 Wm_rated와 값이 거의 같은 것을 확인하였다.

![image](https://github.com/lcw3379/MotorControl-Simulation/assets/127228208/79db1b32-7801-4b4c-9a59-b50c765f3e5e)

그 후, 위치제어기, 속도제어기, 전류제어기를 장착하여 모터 구동 시뮬레이션을 만들어 보았다.

![image](https://github.com/lcw3379/MotorControl-Simulation/assets/127228208/a4811c4a-29b9-4cb4-a93c-670033597c69)

위치제어기, 속도제어기, 전류제어기 내부는 다음과같다.

![image](https://github.com/lcw3379/MotorControl-Simulation/assets/127228208/02fee68c-bc52-487f-8977-d6ede4632717)

위치제어기.

![image](https://github.com/lcw3379/MotorControl-Simulation/assets/127228208/35ca43ba-487a-41f3-8ca0-7b0fef3b51b6)

속도제어기. 속도제어기에는 PI제어기와 IP제어기를 섞어서 사용한다.

![image](https://github.com/lcw3379/MotorControl-Simulation/assets/127228208/e76a5ad2-7273-4187-bf28-6ca93e1fd82c)

전류제어기.



스텝에서의 반응은 다음과 같다.
![image](https://github.com/lcw3379/MotorControl-Simulation/assets/127228208/83ef8ec2-de15-4da8-91fd-396f48864ba4)


연속 펄스에서의 반응은 다음과 같다.

![image](https://github.com/lcw3379/MotorControl-Simulation/assets/127228208/b2ccdf98-1bcb-47f2-9e09-3dfb5bd9b008)



# 2. BLDC 모터
BLDC모터는 mosfet소자로 구성된 인버터, 인버터에 신호를 주는 디코더, BLDC모터로 구성되어 있다.

![image](https://github.com/lcw3379/MotorControl-Simulation/assets/127228208/e5cfaef2-7233-4d60-8c4e-944768c17a33)

BLDC모터는 참조한 블로그처럼 PMSM모터의 역기전력 파형을 사다리꼴 모양으로 설정하여 구현하였다.

모터의 부하는 0.05초에서 토크의 형태로 가하였다.

그러나 아래 사진처럼 참고자료와는 달리 부하가 없는 상태에서도 모터가 특정 속도로 움직이는 현상이 있었다.

![image](https://github.com/lcw3379/MotorControl-Simulation/assets/127228208/3cf3a8ec-fd27-4aed-958a-b3bc80b01dff)


참고한 BLDC모터의 파라미터를 조금씩 변형하여 결과를 보았다. 상전류에서는 초기에 큰 전류가 흐른 다음, BLDC모터에서 보이는 전류 모양과 부하 시 역기전력이 줄어드는 현상 등을 볼 수 있었다. 하지만 초기부터 가속이 발생하는 현상은 막을 수 없었다. 그리고 RPM이 +방향이 아닌 -방향으로 추출되었다. 

![image](https://github.com/lcw3379/MotorControl-Simulation/assets/127228208/88fb8e72-1de1-4343-b584-507b08c0cc99)
![image](https://github.com/lcw3379/MotorControl-Simulation/assets/127228208/c6628d30-b1cf-4466-83be-4194e023cc30)
![image](https://github.com/lcw3379/MotorControl-Simulation/assets/127228208/c6d03947-bcec-4d3a-806b-8ce8813ea834)



여러 파라미터를 조정해가며 역기전력 파형과 속도를 관찰하였다. 모터의 파라미터 값에 의하여 변화가 컸다. 
![image](https://github.com/user-attachments/assets/6dc3a44e-0b61-48de-b54a-cfd4d82cbba1)
![image](https://github.com/user-attachments/assets/de5fc550-8fed-44cd-9882-474d3746184b)





참고 

DC모터

 https://ropiens.tistory.com/8
 
BLDC모터

김상훈 저, 모터제어

https://m.blog.naver.com/lagrange0115/220616270553

https://blog.naver.com/PostView.naver?blogId=lagrange0115&logNo=220672963499
