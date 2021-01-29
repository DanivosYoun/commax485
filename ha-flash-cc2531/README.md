# HA flash addon for cc2531
cc디버거 없이 라즈베리파이를 이용한 cc2531 기기의 플래싱 애드온.

코디네이터 혹은 라우터 선택이 가능합니다. (설정화면 참고)

## 설치 방법
1. Supervisor -> ADD-ON STORE 이동
2. " https://github.com/kimtc99/HAaddon " 를 Repositories 에 추가하고 새로 고침을 합니다.
3. Saram's Repository 항목으로 이동하여 "CC2531 flash addon for HA with RaspberryPi"를 선택하고 INSTALL을 눌러 설치합니다.

## 설정 화면
<pre><code>
"coordinator": true,
"zigbee3": true,
"router_level": 0,
"flags": ""
</code></pre>

#### coordinator : true / false
코디네이터로 설치할 경우 true, 라우터로 설치할 경우 false 를 입력하세요.
#### zigbee3 : true / false
코디네이터를 zigbee3.0으로 설치할 경우 true, zigbee1.2 로 설치할 경우 false
#### router_level : 0, 1, 2
라우터 firmware 설치 옵션 (코디네이터로 설정시 작동 안함)
* 0: standard firmware
* 1: standard firmware + diagnostic messages
* 2: standard firmware + diagnostic messages + USB support
#### flags : 문자
명령어 뒤에 추가할 옵션을 적습니다. 추가한 옵션은 플래싱과 관련한 모든 명령(cc_chipid, cc_erase, cc_write) 뒤에 추가됩니다.
예로 ffff 에러의 경우 flags에 "-m 300"을 적어주면 됩니다.(참고: https://cafe.naver.com/koreassistant/2125 )

(자세한 설명은 https://github.com/Koenkk/Z-Stack-firmware 에서 확인하세요.)

## 연결 방법
|CC2531|라즈베리파이|
|:---:|:---:|
|1 (GND)|39 (GND)|
|3 (DC)|36 (GPIO27, BCM16)|
|4 (DD)|38 (GPIO28, BCM20)|
|7 (reset)|35 (GPIO24, BCM19)|

![cc2531 점프선 연결화면](https://github.com/kimtc99/HAaddon/blob/master/img/cc2531-1.jpg)
![cc2531과 RaspberryPi 연결화면](https://github.com/kimtc99/HAaddon/blob/master/img/cc2531-2.jpg)

## 결과 확인
wiring page 관련 문구가 나오고 애드온이 종료되면 플래싱이 완료됩니다.
