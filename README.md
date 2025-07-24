# QAInfo


# 파일 체크섬 확인
```sh
certutil -hashfile [파일명] SHA256|MD5
```

예제
```
certutil -hashfile readme.txt SHA256
```

# PICT 페어와이즈 조합 사용
## 다운로드
https://github.com/microsoft/pict/releases/download/v3.7.4/pict.exe

## 기본 명령
1. 엑셀 출력하는 경우
```
pict data.txt > r.xls
```

2. 전수 테스트 조합 만드는 경우
```
pict data.txt /o:max > r2.xls
```

# 다운로드 위치
- Jenkins: https://www.jenkins.io/download/  에서 LTS Windows 버전
- OepnJDK: https://github.com/ojdkbuild/ojdkbuild  에서 17버전

# CPPCheck
## 설치위치

## 실행 명령
```sh
cppcheck  --enable=all --inconclusive --xml --xml-version=2 src 2> cppcheck.xml
```
```sh
"c:\Program Files\Cppcheck\cppcheck.exe"  --enable=all --inconclusive --xml --xml-version=2 src 2> cppcheck.xml
```


## MISRA 분석을 위한 실행
### Misra_2012.txt 파일 복사
- 위치: C:\TestTools

### 설정 파일 생성: misra.json
- 위치: C:\TestTools
- 파일 구성
```json
{
    "script": "misra.py",
    "args": [
        "--rule-texts=C:\\TestTools\\Misra_2012.txt"
    ]
}
```

### 실행명령
```sh
cppcheck.exe --addon="C:\TestTools\misra.json"  --xml --xml-version=2 . 2> cppcheck.xml
```


# CPD
## 다운로드
https://github.com/pmd/pmd/releases/tag/pmd_releases%2F6.55.0
에서, https://github.com/pmd/pmd/releases/download/pmd_releases%2F6.55.0/pmd-bin-6.55.0.zip 다운로드

## 실행
- Jenkins 용
```sh
C:\tools\pmd\bin\cpd --minimum-tokens 100 --files ./src --language cpp --format xml > cpd.xml || exit 0
```

- CSV 출력 (엑셀 확인용)
```sh
"C:\TestTools\pmd-bin-6.55.0\bin\cpd.bat" --minimum-tokens 100 --files . --language cpp --format csv > result.csv
```
# Lizard 순환 복잡도 분석
## 설치 주의 사항
CMD(명령 프롬프트)를 관리자 권한으로 실행한 후, pip install lizard 실행

## 실행 방법
- CSV 출력
```sh
"C:\Program Files\Python312\Scripts\lizard.exe" . --csv > lizard.csv
```

- Jenkins용 xml 출력
```sh
"C:\Program Files\Python312\Scripts\lizard.exe" . --xml > lizard.xml
```

## CSV 출력했을 때 각 열 정보
<img width="1091" height="412" alt="image" src="https://github.com/user-attachments/assets/ad550a0d-3ba7-4057-b4ed-02a9bf1e9419" />





# CLOC (라인수, 주석라인수 확인)
## 다운로드
https://github.com/AlDanial/cloc

## 사용법
```
cloc.exe .
```
