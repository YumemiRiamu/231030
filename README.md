# 231030

20191276 컴퓨터공학과 양용석

간단한 멀티태스킹 예제 (출력 창에서 스레드 두개가 일정 주기마다 카운트하는 예제)

코드 

```
//CMainFrm.cpp 파일에서 전역함수 ThreadFunctionA, B 선언

UINT ThreadFunctionA(LPVOID pParam);
UINT ThreadFunctionB(LPVOID pParam);

//A : 1부터 10까지 1초 간격으로 카운트 
UINT ThreadFunctionA(LPVOID pParam)
{
	for (int i = 0; i < 10; ++i)
	{
		TRACE("Thread A: %d\n", i);
		Sleep(1000); // 1초 동안 잠깁니다.
	}

	return 0;
}
//B 정의 : 1부터 10까지 0.5초 간격으로 카운트
UINT ThreadFunctionB(LPVOID pParam)
{
	for (int i = 0; i < 10; ++i)
	{
		TRACE("Thread B: %d\n", i);
		Sleep(500); // 0.5초 동안 잠깁니다.
	}

	return 0;
}
//OnCreate() 내부에 두 함수가 병렬로 실행되도록 스레드를 생성
  AfxBeginThread(ThreadFunctionA, NULL);
	AfxBeginThread(ThreadFunctionB, NULL);

```
실행 결과 </br>
![Image description](./스크린샷 2023-10-30 111557.png) </br>
