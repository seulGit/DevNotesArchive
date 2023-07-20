AOP (Aspect-Oriented Programming)
=================================

공통관심사항을 핵심비즈니스로직에서 처리하려면 일일히 다 적어넣어야해서 유지보수도 힘들고, 보기에도 지저분하다.

그래서 따로 모듈화를 해서 interceptor 처럼 처리되게끔 하는 AOP 기법을 쓴다.

```
@Aspect //AOP라고 인식하게 해주는 어노테이션
@Component //AOP는 정형화된 패턴이 아니다보니 보통은 Config에 따로 Bean으로 등록해주는 게 좋다. 여기서는 Component스캔방식을 씀.
public class TimeTraceAop {
	@Around("execution(* hello.hellospring..*(..))") //공통관심사항이다보니 적용될 범위를 정해준다. 여기서는 hello.hellospring 패키지 안의 모든 것으로 설정.
	public Object execute(ProceedingJoinPoint joinPoint) throws Throwable { //Throwable.. 예외처리도 다시한번 공부하자
		long start = System.currentTimeMillis();
		System.out.println("START: " + joinPoint.toString());
		try {
			return joinPoint.proceed(); //비즈니스로직을 마저 실행한다.
		} finally {
			long finish = System.currentTimeMillis();
			long timeMs = finish - start;
			System.out.println("END: " + joinPoint.toString() + " " + timeMs + "ms"; //실행되는 비즈니스로직의 메서드명들을 소요시간과 함께 출력한다.
		}
	}

}
```

참고: 인프런 - 스프링입문(김영한 님)
