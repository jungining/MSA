# 10. 콘웨이의 법칙과 시스템 설계

- 콘웨이의 법칙 : 조직은 시스템을 설계할 때 필연적으로 그 조직의 의사소통 구조와 일치하도록 만든다.

## 10.1. 증거

- 강력히 결합된 조직 (ex.비전과 목적이 결속된 상용제품 회사)
    - 모듈화가 덜 됨
- 느슨히 결합된 조직 (ex.분산된 오픈 소스 커뮤니티)
    - 모듈화가 잘 됨, 결합도가 낮은 시스템을 만듬
- [마이크로소프트 내 사례연구](https://www.microsoft.com/en-us/research/publication/the-influence-of-organizational-structure-on-software-quality-an-empirical-case-study/?from=http%3A%2F%2Fresearch.microsoft.com%2Fpubs%2F70535%2Ftr-2008-11.pdf) : 윈도우비스타
    - 조직 구조와 연관된 지표가 통계적으로 오류 유발 수준과 가장 밀접하다.

## 10.2. 넷플릭스와 아마존
- 각 시스템의 생명주기를 그시스템을 관리하는 팀이 소유하고 운영
- 작은 팀이 일도 빠르게 처리
- two-pizza team 법칙 : 팀의 규모가 피자 두 판으로 식사를 마칠 수 없는 규모가 돼서는 안 된다.

## 10.4. 의사소통 경로 적응
- 지리적으로 분산된 팀의 의사소통 비용이 높을수록 -> 변경을 조율하는 비용이 높아짐 -> 거대하고 유지보수 하기 어려운 코드베이스가 된다.
- 소유한 서비스의 설계를 진화시키려면
    - 서비스의 소유권을 변경 비용을 적게 유지할 수 있는 동일 위치의 한 팀에 부여할 것을 검토
- 시스템을 구축하는 조직이 느슨히 결합할수록 시스템은 모듈화되고 덜 결합된다.
- 한 팀이 많은 서비스를 소유하려 한다면 분산된 조직에서의 유지보수를 어렵게 만든다.

## 10.5 서비스 소유권
- 서비스 소유권 (SERVICE OWNERSHIP) : 서비스를 소유한 팀이 해당 서비스의 변경을 책임진다.
    - 요구사항 발굴, 애플리케이션 빌드, 배포, 유지보수
    - 배포하기 쉬운 서비스가 만들어진다. ([벽 너머로 던지기](https://specialties.bayt.com/en/specialties/q/167538/in-management-what-they-mean-by-quot-throwing-it-over-the-wall-quot/) 불가)

## 10.6 공유 서비스의 추진 (이유)

공유 서비스를 선택하게 되는 요인

1. 분리의 어려움
    - 서비스 분리 비용이 아주 높거나, 조직이 그것의 문제를 알지 못한 경우 둘 이상의 팀이 하나의 서비스를 소유한다.
    - 거대한 모놀리식 서비스에서 흔하게 발생
2. 제품 feature team (feature based team)
    - 작은 팀이 하나의 제품 feature의 모든 기능을 구현하면서 그 제품 feature set의 개발을 주도하는것
    - 제품 feature team을 광범위하게 적용하면 모든 서비스가 공유된다. 
    - 하지만, 마이크로서비스는 기술 도메인이 아닌 비즈니스 도메인에 따라 모델링된다.
3. 전달 병목점(delivery bottleneck)을 피하기 위해서
    - 변경해야 할 큰 backlog가 있는 경우


## 10.7 내부 오픈소스 (추천)

공유된 서비스들을 제거할 수 없다면, 내부 오픈소스를 써라.
- committer라는 코드 관리인(책임자)을 두고, 변경을 요청하거나 pull request를 보낸다.

1. 관리인의 역할
- 신뢰할 수 있는 committer(core team)과 신뢰할 수 없는 커미터(팀 밖)을 구분해야 한다.
- core team은 변경사항을 조사하고 승인하는 rule이 필요하다.
    - 변경 코드는 기존 코드와 문법적으로 일관돼야 함(coding guideline)
- 좋은 gatekeeper는 제출자와 명확한 의사소통을 하고 좋은 행동 양식을 장려한다.
2. 성숙도
- 서비스의 안정성과 성숙도가 낮을수록 core team이 아닌 외부인의 패치 적용은 더 어렵다. 
3. 도구
- 분산 관리 버전 도구
- 코드 리뷰 시스템
- 빌드, 배포

## 10.8 경계가 있는 콘텍스트와 팀 구조
경계가 있는 콘텍스트에 따라 팀을 짤때 장점
1. 도메인 개념을 더 쉽게 파악 가능
2. 서비스들이 더 긴밀히 소통하여 시스템 설계와 릴리즈 조율을 쉽게 만든다.
3. delivery team이 그 분야의 전문가들과 좋은 관계를 형성하기 쉽다.

## 10.9 방치된 서비스(orphaned service)
-  다양한 기술 스택을 사용하는 polyglot 방식을 적용한 경우, 팀이 더이상 그 기술스택을 모른다면 방치된 서비스(orphaned service)를 변경하는것은 심각한 문제가 될 수 있다.

## 10.11 콘웨이의 역법칙
- 시스템 설계가 조직을 변경할 수 있다.
## 10.12 사람
- 처음에 어떻게 보이든 항상 사람의 문제다.
- 마이크로 서비스 세계에서 사람들의 책임을 명확히 구분해야 한다.
