# 발생 오류

'System.Web.Http, Version=5.2.4.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35' 또는 여기에 종속되어 있는 파일이나 어셈블리 중 하나를 로드할 수 없습니다. 찾은 어셈블리의 매니페스트 정의와 어셈블리 참조가 일치하지 않습니다. (예외가 발생한 HRESULT: 0x80131040)


## 오류 설명

.NET 응용 프로그램에서 특정 어셈블리(System.Web.Http)를 로드할 수 없다는 내용의 오류가 발생했다. 이 오류 메시지는 보통 애플리케이션이 참조하려는 어셈블리의 버전과 실제 로드된 어셈블리의 버전이 일치하지 않을 때 발생하는데 기존의 참조들을 모두 지우고 다시 재참조 했으나 문제가 해결 되지 않았다.
오류 메시지에서 System.Web.Http, Version=5.2.4.0이라는 버전의 어셈블리를 찾으려고 시도했으나, 로컬 어딘가에 5.2.4.0 버전이 잠들어 있는지 매니페스트 정의(실제 어셈블리 파일에 기록된 버전 정보)가 일치하지 않아 오류가 발생한 것으로 보였다.


## 해결 방법

오류를 해결하기 위해 web.config 파일에 다음과 같은 <bindingRedirect> 구문을 추가했다.

```
      <dependentAssembly>
        <assemblyIdentity name="System.Web.Http" publicKeyToken="31bf3856ad364e35" culture="neutral" />
        <bindingRedirect oldVersion="0.0.0.0-5.2.7.0" newVersion="5.2.7.0" />
      </dependentAssembly>
      <dependentAssembly>
        <assemblyIdentity name="System.Net.Http.Formatting" publicKeyToken="31bf3856ad364e35" culture="neutral" />
        <bindingRedirect oldVersion="0.0.0.0-5.2.7.0" newVersion="5.2.7.0" />
      </dependentAssembly>

```

## 결론

이 문제는 어셈블리 버전이 일치하지 않아서 발생한 것입니다. 구체적으로, System.Web.Http 어셈블리를 찾을 때, 애플리케이션은 특정 버전(예: 5.2.4.0)을 참조하려고 했지만, 로컬 시스템에 있는 실제 어셈블리의 버전이 다를 때 이 문제가 발생한다.

`Binding Redirect란?`

bindingRedirect는 .NET에서 사용되는 기능으로, 애플리케이션이 참조하는 특정 어셈블리의 버전이 설치된 실제 어셈블리와 일치하지 않을 때 이를 해결한다.

위의 예시에서, `oldVersion="0.0.0.0-5.2.7.0"` 은 5.2.7.0 버전 이하의 모든 버전을 의미하며, `newVersion="5.2.7.0"` 은 시스템에 설치된 실제 어셈블리의 버전을 나타낸다. 즉, 애플리케이션이 예전 버전(예: 5.2.4.0)을 참조하려고 해도, 자동으로 새로운 버전(5.2.7.0)으로 리다이렉트 되어 문제를 해결한다. (= 구버전 참조를 무시하고, 최신 버전으로 매핑하여 로드할 수 있게 문제 해결)
