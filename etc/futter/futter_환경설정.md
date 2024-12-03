# Flutter Windows 환경설정

## 1. Flutter 다운로드 및 개발 도구 설치

Flutter 사용에 필요한 개발 도구를 Flutter 공식 웹사이트에서 다운로드합니다.
![image](https://github.com/user-attachments/assets/a941884d-c1ef-469e-a2a2-f9ed7b576366)


### 1-1. 필수 도구 다운로드
- [git](https://git-scm.com/) 설치
- [Android Studio 2023](https://developer.android.com/studio) 설치
  ![image](https://github.com/user-attachments/assets/14fc8c90-efde-4929-917d-1ddcaf54f073)


### 1-2. Flutter 다운로드 및 압축 해제
1. Flutter SDK를 [Flutter 공식 사이트](https://flutter.dev/docs/get-started/install)에서 다운로드합니다.
2. 압축을 해제합니다.

![image](https://github.com/user-attachments/assets/7250eb40-9b83-4bb2-b4e8-4e136ec4ee0c)

#### **[유의사항]**
- 압축을 푼 Flutter 파일은 **관리자 권한 승인이 필요한 경로**(예: `C:\Program Files`)에 넣지 말아야 합니다.
- Flutter 파일의 상위 폴더 경로에 **특수문자**나 **공백**이 포함되지 않도록 주의합니다.

---

## 2. Flutter 환경 변수 설정

### 2-1. 시스템 속성에서 환경 변수 설정
1. **시스템 속성 > 고급 > 환경 변수**로 이동합니다.
2. `Path` 항목에 Flutter SDK가 위치한 경로를 추가합니다.
   
   예) `C:\flutter\bin`

![image](https://github.com/user-attachments/assets/1d97ebd0-1f2e-47b6-a6df-e93f2c6e5e9e)

### 2-2. 설치 확인
1. 명령 프롬프트(cmd)를 열고 다음 명령어를 실행합니다:
   ```bash
   flutter doctor
   ```
2. 설치 상태를 확인하고 누락된 항목이 있는 경우 보완합니다.

---

## 3. Android 설정

### 3-1. Android SDK Command-line Tools 설치
1. Android Studio 실행
2. **Tools > SDK Manager**로 이동
3. **Android SDK Command-line Tools**를 설치

![image](https://github.com/user-attachments/assets/0a9afe69-aaaa-4f14-bbf5-1199deb4f926)

### 3-2. Android Licenses 허용
1. 명령 프롬프트(cmd)에서 다음 명령어를 실행합니다:
   ```bash
   flutter doctor --android-licenses
   ```
2. 라이센스 약관을 확인하고 허용합니다.

### 3-3. Flutter와 Dart 플러그인 설치
1. Android Studio 실행
2. **File > Settings > Plugins**로 이동
3. **Flutter**와 **Dart** 플러그인을 설치
![image](https://github.com/user-attachments/assets/9e7c3607-3a62-4d50-9063-1e8ab8524bc6)

---

## 4. 프로젝트 생성

### 4-1. 새로운 Flutter 프로젝트 생성
1. Android Studio에서 **File > New > New Flutter Project** 선택
2. Flutter SDK 경로를 입력
3. 프로젝트를 생성하여 완료
![image](https://github.com/user-attachments/assets/e4cdd812-c8f2-4c9b-9f5a-fd3a8d705a7b)

