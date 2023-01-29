# FCM-Practice

## 🧩 개요

FCM을 적용하기 위한 `AppDelegate` 세팅 코드

## 🤔 배운 내용

### ✔️ APNs (apple push notification service)

#### 역할

  - **알림관리**

    - APNs가 서버(Provider)로부터 받은 알림을 저장하고 online 상태의 디바이스에 알림을 전달 한다.

    - 최신 알림만을 전달하고 디바이스가 offline 상태가 오래 지속될경우 알림을 삭제 한다.

  - **보안관리**

    - connection trust: 토큰/인증서 기반의 인증을 필요로 하며, 애플 디바이스들간의 인증도 존재한다.

    - device token trust: 각각의 앱마다 APNs가 암호화된 토큰을 발급하며, 디바이스 또는 앱의 상태가 변경될 때(ios 업데이트, 복원, 초기화 등) 새로 토큰을 발급한다.
  
#### 관련용어

  - **Connection Trust** : `Provider to APNs`, `APNs to Device` 두개가 존재.
  
    - `Provider-to-APNs` Connection trust : 애플과 계약을 맺은, 승인된 공급자만 APNs와 연결을 시켜서 연결 신뢰를 얻는다. 연결 신뢰를 얻는 방법은 아래 2가지이다.

      - token-based: valid authentication key certificate

      - certificate-based: SSL certificate

    - `APNs-to-device` Connection trust : 승인된 애플 디바이스들만 APNs에 연결하여 알림을 받게한다.

  - **Device-token Trust** : 각 원격 알림에서 end to end로 동작한다. 알림이 올바른 provider와 device 사이에서만 라우팅 된다. 해당 토큰은 device의 할당된 고유 식별자를 포함하는 NSData 인스턴스이기 때문에, token의 보안이 좋다.
  
#### Remote Notification 흐름도

<img width="1438" alt="image" src="https://user-images.githubusercontent.com/42196410/215315344-7040fd9a-f53e-478c-b819-bec284f9bcee.png">


### ✔️ FCM (Firebase Cloud Messaging)

**APNs의 보안요건을 갖춘 서버를 직접 구축하기 힘들 때, 손쉽게 원격알림을 구축해주는 플랫폼.**

- 원격알림 메시지 전송

  사용자에게 표시되는 알림 메시지를 실시간 또는 예약 전송

- 다양한 메시지 타겟팅

  단일기기, 기기그룹, 주제를 구독한 기기

- 발송 메시지 저장, 관리

  알림 내용/상태, 플랫폼, 최종 전송 시간, 열람율 관리  
