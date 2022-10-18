## mock을 사용하는 이유

- 테스트 대상 기능 중 일부 기능이 준비가 되지 않았을때 / 다른 시스템과 통신등이 필요한 경우 미리 리턴 값을 선언하여 테스트 할수 있다. / Stub

- 기본 : when - return

  - (when)어떤 메서드를 호출했을때 -> (return)return값을 지정해줄 수 있음

  - when(spyWhenService.callServerAPI("1")).thenReturn(**true**); when(spyWhenService.callServerAPI("2")).thenReturn(**false**); doReturn(**true**).when(spyWhenService).callServerAPI("1"); doReturn(**false**).when(spyWhenService).callServerAPI("2");

    