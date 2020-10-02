---
title: "(OpenSource - obs) dll-injection example"
permalink: opens/obs/game-capture/dll-injection-example/                # link 직접 지정
#toc: true                       # for Sub-title (On this page)
comments: true                  # for disqus Comments
categories:                     # for categories
date: 2020-10-02 00:00:00 -0000
last_modified_at: 2020-10-02 00:00:00 -0000
sidebar:
  title: "OpenSource 목차"
  nav: OpenS
tag:
  - OpenSource
  - obs
category:
  - dll-injection
classes: wide
excerpt: ""
header:
  teaser: /file/image/OpenS-page-teaser.gif
---

* [참고사이트](https://reversecore.com/38?category=216978)

---

## Dll Injection 이란?

**다른 프로세스에 특정 DLL 파일을 강제로 삽입시키는 것입니다.**

더 정확히 표현하면 다른 프로세스에게 LoadLibrary() API 를 호출하도록 명령하여 내가 원하는 DLL 을 loading 시키는 것입니다.<br>
따라서 DLL Injection 이 일반적인 DLL loading 과 다른점은 loading 대상이 되는 프로세스가 내 자신이냐 아니면 다른 프로세스냐 하는 것입니다.<br>

![](/file/image/dll-injection-1.png)

notepad 프로세스에 myhack.dll 을 강제로 삽입시켰습니다.<br>
(원래 notepad 는 myhack.dll 을 로딩하지 않습니다.)<br>
notepad 프로세스에 로딩된 myhack.dll 은 notepad 프로세스 메모리에 대한 (정당한) 접근권한이 생겼기 때문에 사용자가 원하는 어떤 일이라도 수행할 수 있습니다. (예: notepad 에 통신기능을 추가하여 메신저나 텍스트 웹브라우저 등으로 바꿔버릴 수도 있습니다.)<br>

## DLL Injection 사용 목적

LoadLibrary() API 를 이용해서 어떤 DLL 을 로딩시키면 해당 DLL 의 DllMain() 함수가 실행됩니다.<br>
DLL Injection 의 동작원리는 외부에서 다른 프로세스로 하여금 LoadLibrary() API 를 호출하도록 만드는 것이기 때문에 (일반적인 DLL loading 과 마찬가지로) 강제 삽입된 DLL 의 DllMain() 함수가 실행됩니다.<br>

또한 삽입된 DLL 은 해당 프로세스의 메모리에 대한 접근권한을 갖기 때문에 사용자가 원하는 다양한 일(버그 패치, 기능 추가, 기타)을 수행 할 수 있습니다.<br>
그런데 문제는 대부분 악의적인 용도로 사용된다는 것입니다.<br>

**악성 코드**

정상적인 프로세스(winlogon.exe, services.exe, svchost.exe, explorer.exe, etc)에 몰래 숨어들어가 악의적인 짓들을 합니다. 다른 악성 파일을 다운받거나, 몰래 백도어를 열어두고 외부에서 접속하거나, 키로깅 등의 나쁜짓을 하는 것이죠.<br>
정상 프로세스 내부에서 벌어지는 일이라서 일반적인 PC 사용자들은 눈치채기 어렵습니다.
만약 explorer.exe 가 80 포트로 어떤 사이트에 접속시도를 한다고 생각해보세요.<br>
일반인들은 그냥 정상 프로세스의 정상적인 동작으로 생각하기 쉽습니다.<br>

**유해 프로그램, 사이트 차단 프로그램**

부모님들께서 아이들의 건전한 PC 사용을 위해 설치하는 '프로세스 차단 프로그램' 등이 있습니다.<br>
주로 게임 프로그램과 성인 사이트 접속 등을 방지하는 역할을 하지요.<br>
아이들 입장에서야 원수(?)같은 프로그램이라서 미친듯이 해당 프로세스를 종료하려 듭니다.<br>
DLL Injection 기법으로 정상 프로세스에 살짝 숨어들어간다면 들키지도 않고, 프로세스 강제 종료에도 안전하게 됩니다. (Windows 핵심 프로세스를 종료하면 시스템이 같이 종료되기 때문에 결국 '차단' 하려는 목적을 달성하는 셈이지요.)<br>

**기능 개선 및 (버그) 패치** 

만약 어떤 프로그램의 소스 코드가 없거나 수정이 여의치 않을 때 DLL Injection 을 사용하여 전혀 새로운 기능을 추가하거나 (PlugIn 개념) 문제가 있는 코드, 데이타를 수정할 수 있습니다.<br>
일단 프로세스 메모리에 침투한 DLL 은 해당 프로세스의 메모리에 자유롭게 접근 할 수 있기 때문에 코드, 데이타를 고칠 수 있습니다.<br>
저도 예전에 인터넷에서 다운받은 헥사 에디터에 버그가 있길래 DLL Injection 기법을 이용해서 해당 버그 코드를 간단히 패치해서 사용한 적이 있습니다. (그냥 다른 헥사 에디터를 다운 받아도 써도 되지만 고쳐 쓰고 싶은 마음에... ^^)<br>

**API Hooking**

다음번에 설명드릴 주제인데요, API Hooking 에 DLL Injection 기법이 많이 사용됩니다.
정상적인 API 호출을 중간에서 후킹하여 제가 원하는 기능을 추가 (혹은 기존 기능을 제거)하는 목적으로 사용됩니다.<br>
이 역시 삽입된 DLL 은 해당 프로세스의 메모리에 대한 접근 권한을 가지고 있다는 특성을 잘 활용한 것입니다.<br>

---

## DLL Injection 간단 실습

notepad.exe 프로세스에 myhack.dll 을 injection 시키도록 하겠습니다.<br>
=> myhack.dll 은 www.naver.com/index.html 을 다운받도록 프로그래밍 하였습니다.<br>

[myhack.dll](/file/exe/myhack.dll)<br>
[InjectDll.exe](/file/exe/InjectDll.exe)<br>
[Process Explorer](https://docs.microsoft.com/en-us/sysinternals/downloads/process-explorer)<br>

1. InjectDll.exe 와 myhack.dll 을 다운받아 C:\ 에 복사합니다.
2. 메모장(notepad.exe) 을 실행합니다.
3. InjectDll.exe 를 실행합니다.

Process Explorer 를 이용하여 notepad.exe 프로세스에 Injection 된 myhack.dll 을 확인해 보겠습니다.

![](/file/image/dll-injection-2.png)

notepad.exe 프로세스 메모리 공간에 myhack.dll 이 들어와 있는게 보이시죠?<br>
C:\index.html (네이버 초기화면 html) 파일이 정상적으로 생겼는지 볼까요?<br>

---

## DLL Injection 구현 방법

몇 가지 구현 방법이 있습니다.<br>
그 중에서 가장 유명한 방법이 CreateRemoteThread() API 를 이용하는 방법입니다.<br>
이 방법은 윈도우즈 프로그래밍 서적의 바이블인 Jeffrey Richter 의 Programming Applications for Microsoft Windows 에 소개된 내용입니다.<br>
일단 소스 코드를 보겠습니다. (엔지니어에게는 백 마디 설명 보다는 역시 소스 코드를 한번 보는게 낫죠.)<br>
먼저 Injection 시킬 myhack.dll 소스 코드입니다.<br>

```cpp
// dllmain.cpp : DLL 애플리케이션의 진입점을 정의합니다.
#include "pch.h"

#include "stdio.h"
#include "windows.h"
#include <Urlmon.h>

#pragma comment(lib, "urlmon.lib")

#define DEF_NAVER_ADDR L"http://www.naver.com/index.html"
#define DEF_INDEX_PATH L"c:\\index.html"


DWORD WINAPI ThreadProc(LPVOID lParam)
{
	URLDownloadToFile(NULL, DEF_NAVER_ADDR, DEF_INDEX_PATH, 0, NULL);
	return 0;
}

BOOL APIENTRY DllMain( HMODULE hModule,
                       DWORD  ul_reason_for_call,
                       LPVOID lpReserved
                     )
{
	HANDLE hThread = NULL;

	switch (ul_reason_for_call)
	{
	case DLL_PROCESS_ATTACH:
		hThread = CreateThread(NULL, 0, ThreadProc, NULL, 0, NULL);
		CloseHandle(hThread);
		break;
	}

    return TRUE;
}
```

아주 간단한 코드입니다.

DllMain() 을 보시면 DLL 이 로딩(DLL_PROCESS_ATTACH)될 때 스레드(ThreadProc)를 실행합니다.<br>
ThreadProc() 의 내용은 urlmon.dll 의 URLDownloadToFile() 함수를 실행시켜서 네이버 초기화면(index.html)을 다운받습니다.<br>
프로세스에 DLL Injection 이 발생하면 해당 DLL 의 DllMain() 함수가 호출된다고 이전 포스트에서 설명드렸습니다. 따라서 notepad.exe 프로세스에 myhack.dll 이 Injection 되면 결국 URLDownloadToFile() 함수가 실행될 것입니다.<br>
* DLLMain() 에서 직접 URLDownloadToFile() 을 호출하면 간혹 hang 이 걸리는 경우가 있어서, 별도의 스레드를 생성하여 호출하도록 프로그래밍 하였습니다.<br>
이제 myhack.dll 을 notepad.exe 프로세스에 Injection 시켜줄 프로그램(InjectDll.exe)의 소스코드를 보시겠습니다.<br>

```cpp
// InjectDll.exe

#include "stdio.h"
#include "windows.h"
#include "tlhelp32.h"

#define DEF_PROC_NAME ("notepad.exe")
#define DEF_DLL_PATH ("c:\\myhack.dll")

DWORD FindProcessID(LPCTSTR szProcessName);
BOOL InjectDll(DWORD dwPID, LPCTSTR szDllName);

int main(int argc, char* argv[])
{
    DWORD dwPID = 0xFFFFFFFF;
 
    // find process
    dwPID = FindProcessID(DEF_PROC_NAME);
    if( dwPID == 0xFFFFFFFF )
    {
        printf("There is no <%s> process!\n", DEF_PROC_NAME);
        return 1;
    }

    // inject dll
    InjectDll(dwPID, DEF_DLL_PATH); 

    return 0;
}

DWORD FindProcessID(LPCTSTR szProcessName)
{
    DWORD dwPID = 0xFFFFFFFF;
    HANDLE hSnapShot = INVALID_HANDLE_VALUE;
    PROCESSENTRY32 pe;

    // Get the snapshot of the system
    pe.dwSize = sizeof( PROCESSENTRY32 );
    hSnapShot = CreateToolhelp32Snapshot( TH32CS_SNAPALL, NULL );

    // find process
    Process32First(hSnapShot, &pe);
    do
    {
        if(!_stricmp(szProcessName, pe.szExeFile))
        {
            dwPID = pe.th32ProcessID;
            break;
        }
    }
    while(Process32Next(hSnapShot, &pe));

    CloseHandle(hSnapShot);

    return dwPID;
}

BOOL InjectDll(DWORD dwPID, LPCTSTR szDllName)
{
    HANDLE hProcess, hThread;
    HMODULE hMod;
    LPVOID pRemoteBuf;
    DWORD dwBufSize = lstrlen(szDllName) + 1;
    LPTHREAD_START_ROUTINE pThreadProc;

    // #1. dwPID 를 이용하여 대상 프로세스(notepad.exe)의 HANDLE을 구함
    if ( !(hProcess = OpenProcess(PROCESS_ALL_ACCESS, FALSE, dwPID)) )
        return FALSE;

    // #2. 대상 프로세스(notepad.exe) 메모리에 szDllName 크기만큼 메모리를 할당
    pRemoteBuf = VirtualAllocEx(hProcess, NULL, dwBufSize, MEM_COMMIT, PAGE_READWRITE);

    // #3. 할당 받은 메모리에 myhack.dll 경로("c:\\myhack.dll")를 씀
    WriteProcessMemory(hProcess, pRemoteBuf, (LPVOID)szDllName, dwBufSize, NULL);

    // #4. LoadLibraryA() API 주소를 구함
    hMod = GetModuleHandle("kernel32.dll");
    pThreadProc = (LPTHREAD_START_ROUTINE)GetProcAddress(hMod, "LoadLibraryA");

    // #5. notepad.exe 프로세스에 스레드를 실행
    hThread = CreateRemoteThread(hProcess, NULL, 0, pThreadProc, pRemoteBuf, 0, NULL);
    WaitForSingleObject(hThread, INFINITE); 

    CloseHandle(hThread);
    CloseHandle(hProcess);

    return TRUE;
}
```