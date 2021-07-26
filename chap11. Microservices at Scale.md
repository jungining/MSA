# 11. 대규모 마이크로서비스

분리된 많은 서비스의 장애를 처리하거나 수백개의 서비스를 관리해야 한다면, 대응 패턴은 무엇일까?

## 11.1 장애는 어디에서나 발생한다
- 어떤 것이든 고장날 수 있다는 가정을 명심하고 장애에 대한 계획을 세운다면 다양한 절충안을 준비할 수 있다.

## 11.2 얼마나 많아야 너무 많은건가?
- 오토스케일링 기능이 없다면, 교차 기능 요구사항의 이해가 필요하다.
- 교차기능 요구사항 : 응답시간/지연시간, 가용성, 데이터의 내구성
- 교차기능 요구사항은 서비스마다 다르므로, 요구사항을 지속적이며 체계적으로 측정할 방법이 필요하다.

## 11.3 기능 분해
- 회복력 있는 시스템 구축에서 가장 중요한 것은 `안전하게 기능을 분해할 수 있는 능력`이다.
- 모놀리식 애플리케이션에서는 시스템 상태가 ON/OFF 밖에 없지만, 마이크로서비스 아키텍처에서는 훨씬 미묘한 상황을 고려행야 한다.

이제 장애가 발생할 때 처리할 수 있도록 기술적인 관점에서 가능한 일들을 고려해보자.

## 11.4,5 아키텍처 안전 조치
> 아키텍처 안전 조치 : 무언가 잘못될 때 벌어지는 심각한 파급 효과를 막기 위해 이용하는 몇가지 패턴

1. 타임아웃 - 항상 기본 타임아웃 시간을 적절히 설정하라.
2. 회로 차단기 - 임계치를 설정하고, 임계치를 초과했을때 커넥션을 중단한다. 복구 여부를 확인해 정상 임계치 도달시 커넥션을 리셋한다.
3. 격벽(bulk head) - 특정 하위 서비스가 느려지게 되더라도 그 서비스의 커넥션 풀에서만 영향을 받고 다른 호출은 정상 처리됨을 보장한다.
4. 격리 : 서비스간의 격리도를 높이면, 상위 서비스는 하위 서비스로 인해 계획되지 않은 장애로부터 영향을 받을 가능성이 낮아진다. 서비스 소유자 간에 조율할 것도 줄어든다.

## 11.6 멱등성(idempotent)
- 멱등성 : 역효과 없이 호출을 반복할 수 있음
- 이벤트를 멱등 방식으로 처리함으로써 안전성을 보장한다.

## 11.7 확장
1. 더 크게 만들기
2. 작업부하 나누기
3. 위험 분산
4. 부하 분산
5. 작업자 기반 시스템
6. 다시 시작하기

## 11.8 데이터베이스 확장
## 11.9 캐싱
## 11.10 자동 확장
## 11.11 CAP 정리
## 11.12 서비스 발견
## 11.13 동적 서비스 레지스트리
## 11.14 문서화 서비스
## 11.15 자기 기술 시스템