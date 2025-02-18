# 객체 지향 프로그래밍

**2025/02/17 [포텐업] 게임 개발자 양성 과정**

---

## SOLID 원칙

### SOLID

객체지향 설계에서 지켜야 할(권장) 5가지 개발 원칙

* **S**RP (Single Responsibility Principle) : 단일 책임 원칙
* **O**CP (Open Closed Principle) : 개방 폐쇄 원칙
* **L**SP (Liskov Substitution Principle) : 리스코프 치환 원칙
* **I**SP (Interface Segregation Principle) : 인터페이스 분리 원칙
* **D**IP (Dependency Inversion Principle) : 의존성 역전 원칙



### 단일 책임 원칙 SRP

**클래스에는 변경하는 이유가 하나만 존재해야 한다.**

즉, 클래스는 한 가지 일만 담당해야 한다. 이로 인해 유지 보수가 용이해진다.



#### SRP 위반 (잘못된 경우)

- EmailService 클래스는 이메일 전송과 데이터베이스 저장이라는 두 가지 기능을 담당하고 있다.
- 한 클래스가 두 가지 책임을 가지므로 SRP를 위반한다.

```c++
#include <iostream>
#include <string>

// 이메일 클래스
class Email
{
public:
    std::string recipient;
    std::string subject;
    std::string body;

    Email(const std::string& recipient, const std::string& subject, const std::string& body)
        : recipient(recipient), subject(subject), body(body) {}
};

// SRP 위반: EmailService 클래스가 이메일 전송과 데이터베이스 저장이라는 두 가지 책임을 가짐.
class EmailService
{
public:
    void SendEmail(const Email& email)
    {
        // 이메일 전송 로직 (예제용 출력).
        std::cout << "이메일을 " << email.recipient << "에게 전송합니다: " << email.subject << "\n";
    }

    void SaveEmailToDatabase(const Email& email)
    {
        // 이메일을 데이터베이스에 저장하는 로직 (예제용 출력).
        std::cout << "이메일을 데이터베이스에 저장합니다: " << email.subject << "\n";
    }
};

int main()
{
    Email email("example@example.com", "안녕하세요", "이것은 테스트 이메일입니다.");
    EmailService emailService;

    emailService.SendEmail(email);
    emailService.SaveEmailToDatabase(email);

    return 0;
}
```



#### SRP 준수

- EmailSender 클래스
  - 이메일 전송이라는 하나의 책임만 담당한다.
  - SendEmail 함수는 이메일을 전송하는 역할을 한다.
- EmailRepository 클래스
  - 이메일을 데이터베이스에 저장하는 하나의 책임만 담당한다.
  - SaveEmailToDatabase 함수는 이메일을 저장하는 역할을 한다.
- SRP 적용
  - 각 클래스가 하나의 책임만 수행하므로 Single Responsibility Principle을 준수한다.
  - 유지보수가 쉽고 코드가 명확해진다.

```c++
#include <iostream>
#include <string>

// 이메일 클래스
class Email
{
public:
    std::string recipient;
    std::string subject;
    std::string body;

    Email(const std::string& recipient, const std::string& subject, const std::string& body)
        : recipient(recipient), subject(subject), body(body) {}
};

// 이메일 전송 책임을 담당하는 클래스
class EmailSender
{
public:
    void SendEmail(const Email& email)
    {
        // 이메일 전송 로직 (예제용 출력)
        std::cout << "이메일을 " << email.recipient << "에게 전송합니다: " << email.subject << "\n";
    }
};

// 이메일 저장 책임을 담당하는 클래스
class EmailRepository
{
public:
    void SaveEmailToDatabase(const Email& email)
    {
        // 이메일을 데이터베이스에 저장하는 로직 (예제용 출력)
        std::cout << "이메일을 데이터베이스에 저장합니다: " << email.subject << "\n";
    }
};

int main()
{
    Email email("example@example.com", "안녕하세요", "이것은 테스트 이메일입니다.");

    EmailSender emailSender;
    EmailRepository emailRepository;

    emailSender.SendEmail(email);
    emailRepository.SaveEmailToDatabase(email);

    return 0;
}
```

