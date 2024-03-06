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


