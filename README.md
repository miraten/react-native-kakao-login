# 카카오로그인 for React Native

![platforms](https://img.shields.io/badge/platforms-Android%20%7C%20iOS-brightgreen.svg?style=flat-square&colorB=191A17)
[![npm](https://img.shields.io/npm/v/@beblue/react-native-kakao-login.svg?style=flat-square)](https://www.npmjs.com/package/@beblue/react-native-kakao-login)
[![npm](https://img.shields.io/npm/dm/@beblue/react-native-kakao-login.svg?style=flat-square&colorB=007ec6)](https://www.npmjs.com/package/@beblue/react-native-kakao-login)

[![github issues](https://img.shields.io/github/issues/trabricks/react-native-kakao-login.svg?style=flat-square)](https://github.com/trabricks/react-native-kakao-login/issues)
[![github closed issues](https://img.shields.io/github/issues-closed/trabricks/react-native-kakao-login.svg?style=flat-square&colorB=44cc11)](https://github.com/trabricks/react-native-kakao-login/issues?q=is%3Aissue+is%3Aclosed)
[![Issue Stats](https://img.shields.io/issuestats/i/github/trabricks/react-native-kakao-login.svg?style=flat-square&colorB=44cc11)](http://github.com/trabricks/react-native-kakao-login/issues)

## 알림

이 소스는 `@actbase/react-native-kakao-login` 의 소스에서 일부 버그를
수정한 버전입니다.

Typescript 에서 import 할 때의 오류를 수정한 것으로 그 이상의 작업은 현재
예정되어 있지 않습니다.

원 소스 `@actbase/react-native-kakao-login`에서 이 오류를 반영하면 이 프로젝트는 바로 내릴 예정입니다. 참고하세요.

현재 iOS에 한정하여 소스를 수정하였으며, Android는 전혀 손대지 않은 상태입니다.

## 기본설정

현재 버전은 Kakao SDK v2반영 버전입니다.

@actbase/react-native-KakaoSDK랑 상관없이 독립적으로 사용가능합니다.

스위프트 기반 sdk라서.. 가이드는 좀 정리해서 다시 올리겠습니다.

궁금한 사항이 있는경우 카카오톡 오픈채팅 React & React-Native에서 물어보면 많은 분들이 답변해주십니다.

작업하시다가 외주 혹은 작업할 업체가 필요하면 [leader@trabricks.io](mailto:leader@trabricks.io)로 메일 주시면 친절하게 안내해드립니다.

RN 0.60 이상 사용가능하며, Pod 필수입니다.

## Getting started

### Mostly automatic installation (RN >= 0.60)

```bash
$ npm install @beblue/react-native-kakao-login --save
$ cd ios && pod install && cd ..
```

## 설정

iOS 버전을 `11.0` 이상으로 설정한다.

XCode에서 프로젝트를 열고 `PROJECT_NAME.xcodeproj` 파일에서

`Info` 섹션의 `Deployment Target / iOS Deployment Target`을 `11.0` 이상으로 변경

`Pods/Podfile`파일의 상단에 있는 다음 부분에서 버전을 `11.0` 이상으로 수정

```
    ...

    platform :ios, '11.0'

    ...
```

## 사용방법

```js
import KakaoLogin from "@beblue/react-native-kakao-login";

// 카카오 로그인 시 처리부문
const loginOutput = await KakaoLogin.login();
```

| 변수명                | 설명                        |
| --------------------- | --------------------------- |
| accessToken           | 카카오의 accessToken        |
| refreshToken          | 카카오의 refreshToken       |
| accessTokenExpiresAt  | 카카오의 accessToken만료일  |
| refreshTokenExpiresAt | 카카오의 refreshToken만료일 |
| scopes                | 사용권한                    |

```js
import KakaoLogin from "@beblue/react-native-kakao-login";

// 카카오 로그아웃시 처리
await KakaoLogin.logout();

// 카카오 액세스 토큰 가져오는 명령, 로그인 시 자동으로 로그아웃 후 처리됨에 따라
// 별도로 값만 가져올 경우 사용.
// 로직 변경으로 인해 해당 현재 토큰의 대한 정보(아이디, 만료일)만 가져옵니다.
const accessToken = await KakaoLogins.getAccessToken();

// 카카오 회원정보 가져오기
const profile = await KakaoLogins.getProfile();
```

| 변수명        | 설명                                                                                            |
| ------------- | ----------------------------------------------------------------------------------------------- |
| id            | 카카오계정 고유키                                                                               |
| connected_at  | 연결한 일자                                                                                     |
| kakao_account | [회원정보](https://developers.kakao.com/sdk/reference/ios-legacy/release/Classes/KOUserMe.html) |
| properties    | 기타자료                                                                                        |
