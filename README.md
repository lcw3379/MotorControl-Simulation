# MotorControl-Simulation

1. DC모터

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


실행 결과는 다음과 같다.

![image](https://github.com/lcw3379/MotorControl-Simulation/assets/127228208/79db1b32-7801-4b4c-9a59-b50c765f3e5e)

그 후, 위치제어기, 속도제어기, 전류제어기를 장착하여 모터 구동 시뮬레이션을 만들어 보았다.

![image](https://github.com/lcw3379/MotorControl-Simulation/assets/127228208/a4811c4a-29b9-4cb4-a93c-670033597c69)

위치제어기, 속도제어기, 전류제어기 내부는 다음과같다.
![image](https://github.com/lcw3379/MotorControl-Simulation/assets/127228208/02fee68c-bc52-487f-8977-d6ede4632717)

![image](https://github.com/lcw3379/MotorControl-Simulation/assets/127228208/35ca43ba-487a-41f3-8ca0-7b0fef3b51b6)
속도제어기에는 PI제어기와 IP제어기를 섞어서 사용한다.

![image](https://github.com/lcw3379/MotorControl-Simulation/assets/127228208/e76a5ad2-7273-4187-bf28-6ca93e1fd82c)




스텝에서의 반응은 다음과 같다.
![image](https://github.com/lcw3379/MotorControl-Simulation/assets/127228208/83ef8ec2-de15-4da8-91fd-396f48864ba4)


연속 펄스에서의 반응은 다음과 같다.

![image](https://github.com/lcw3379/MotorControl-Simulation/assets/127228208/efebb33b-8a50-4c7e-92eb-e65a88c754a7)

속도추정을 제대로 하지 못하는 것으로 보아 전압 인풋에 문제가 있다고 판단하였다. 전압을 측정하였더니 정격전압인 12볼트까지 제대로 올라가지 못하는 현상이 있었다.

![image](https://github.com/lcw3379/MotorControl-Simulation/assets/127228208/6d6d0b00-e086-41c4-9c3a-2537312ec9d8)

