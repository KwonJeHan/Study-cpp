# 블루프린트 학습 정리

**2025/03/18 [포텐업] 게임 개발자 양성 과정**

---

## 블루프린트 실습

대미지 처리 컴포넌트 (액터 컴포넌트)

몬스터와 플레이어에서 모두 사용하도록 구성

죽음 이벤트 발행 (OnDead)   

체력 변경 이벤트 발행 (OnHealthPowerChanged) 



플레이어 -> 몬스터 대미지 처리

몬스터의 죽음 상태 처리 

죽을 때 머티리얼 효과 적용 (디졸브 효과 적용/이 때 노이즈 텍스처 사용)

오파시티 마스크(Opacity Mask) 핀 활용

IF 블록을 활용해서 투명도 제어



플레이어/몬스터 공격 콜리전 채널/프로필 추가 / 기존 프로필과의 설정 업데이트 (오버랩, 트리거 등)



몬스터 -> 플레이어 대미지 처리

콜리전 배치

근접 공격(Melee) - 애니메이션 노티파이 스테이트 (블루프린트)

플레이어 피격 효과 (머티리얼 활용)



UI (Unreal Motion Graphic, UMG)

HPHUD UI

빌보드 (Billboard)

항상 카메라를 바라보는 기능

카메라 회전 그대로 설정 / 자손 컴포넌트에서 180도 뒤집기.

대미지 텍스트(애니메이션) 

오버레이 UI (시간 남으면)



몬스터 공격 스테이트 관련 예외 처리

플레이어가 죽으면 그만 공격 하도록 처리



체력 아이템

이벤트 디스패처를 통한 체력 회복 구현
