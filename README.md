# SKUad ERP Procurement

공급사 관리, 본사 구매 주문(PO), 본사 창고 입고를 담당하는 독립 백엔드 서비스입니다. 프로젝트 이름은 `procurement-service`, 기본 패키지는 `com.skuad.procurement`입니다.

## 기술 구성

Java 17, Spring Boot 4.2.0, Gradle(Groovy), YAML, 실행 가능한 JAR를 사용합니다. 공통 의존성은 Spring Web·Security, OAuth2 Resource Server·Client, Spring Data JPA, Validation, PostgreSQL, Flyway, Actuator, Lombok입니다.

## 로컬 실행

Java 17을 설치한 뒤 프로젝트 폴더에서 실행합니다. IntelliJ에서는 Gradle JVM도 17로 선택합니다.

```bash
./gradlew bootRun
```

기본 설정은 PostgreSQL 없이 시작합니다. [상태 점검](http://localhost:8084/actuator/health)에서 `UP`을 확인합니다. 실행 포트는 `SERVER_PORT`로 변경할 수 있습니다.

## PostgreSQL 연결

PostgreSQL에 서비스용 데이터베이스를 만든 뒤 `postgres` 프로필을 사용합니다.

```bash
SPRING_PROFILES_ACTIVE=postgres \
DB_URL=jdbc:postgresql://localhost:5432/procurement_db \
DB_USERNAME=postgres \
DB_PASSWORD='<로컬 DB 비밀번호>' \
./gradlew bootRun
```

현재 상태 점검을 제공하며 구매 업무 API와 Flyway 테이블 마이그레이션은 후속 개발에서 추가합니다.
