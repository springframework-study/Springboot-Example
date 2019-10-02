## 자동 설정 개요

+ EnableAutoConfiguration (@SpringBootApplication 안에 숨어 있음)
+ @SpringBootApplication
    + @SpringBootConfiguration -> @Configuration과 비슷한 애노테이션
    + @ComponentScan
    + @EnableAutoConfiguration
+ 빈을 사실 두 단계로 나눠서 읽힘(등록함)
    + 1단계 @ComponentScan -> 이것만으로도 실행가능 (물론 웹서버로는 동작X)
    + 2단계 @EnableAutoConfiguration
+ 1단계로만 실행하는법
```{.java}
//@SpringBootApplication
@Configuration
@ComponentScan
//@EnableAutoConfigration
public class Application{

    public static void public static void main(String[] args){
        SpringApplication application = new SpringAplication(Application.class);
        application.setWebApplicationType(WebApplicationType.None);
        application.run(args);
    }
}
```

+ @ComponentScan -> 하위패키지에 있는것들도 스캔하지만 다른패키지는 X
    + @Component
    + @Configuration @Repository @Service @Controller @RestController
    
+ @EnableAutoConfiguration
    + spring.factories -> META-INF파일에 있음
        + org.springframework.boot.autoconfigure.EnableAutoConfiguration키값이 있음
    + @Configuration
    + @ConditionalOnXxxYyyZzz -> 이 조건에 따라 어떠한 빈을 등록하거나 등록하지 않는다.