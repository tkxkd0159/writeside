# Rules
* 파일 이름은 대소문자 구분해서 파일 안에서 참조 시 이를 지켜야한다. 단, 컴파일된 `html`은 소문자 kebab case로 변하기 때문에 같은 이름의 대소문자 다른 파일은 생성 불가.
* 현재 Algoria index 업로드할 때 floating number 처리 못하는 버그있음. 무조건 소수점 떼고 정수로 올리기 때문에 버그 해결 전까지 `writeside.cfg`에서 버전 설정 정수. `CONFIG_JSON_VERSION`도 이에 맞춰서 설정.

# Versioning
1. 각 버전 관리할 브랜치 하나씩 생성.
2. 설정 업데이트
   1. root의 `writerside.cfg`에서 `<instance>`에 `version` 설정
   2. 정적으로 배포되어 있는 `help-version.json`에서 버전 관련 메타데이터 작성. 이 때 `version` 값은 위의 `<instance>`에 선언한 값과 동일해야 함.
   3. 처음인 경우 `cfg/buildprofiles.xml`에서 `<versions-switcher>{metadata-deployed-url}</version-switcher>` 설정

# SEO
배포하는 문서가 크롤링 되도록 허용하는 설정. `cfg/buildprofiles.xml`에서 아래 설정
```XML
<variables>
    <noindex-content>false</noindex-content>
</variables>
```

# Experimental features
## Feedback widget
설정하면 매 문서 페이지 맨 아래에 피드백 제출할 수 있는 위젯 삽입해줌
```XML
<variables>
    <feedback-widget>true</feedback-widget>
    <feedbackRequireEmail>true</feedbackRequireEmail>
    <feedback-url>https://example.com</feedback-url>
    <feedback-support>support_tickec_url</feedback-support>
</variables>
```