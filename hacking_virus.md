### 컴퓨터 구조


컴퓨터 - 각자 다른 기능을 수행하는 여러 부품 도움으로 작동.

CPU는 컴퓨터의 작동에 핵심이 되는 연산 처리.

저장장치는 데이터 저장

GPU는 그래픽 데이터, 랜카드는 네트워크 통신, 사운드 카드는 소리 데이터 처리.

이처럼 각 특징이 뚜렷하여 컴퓨터에서 고유의 기능을 수행.

---

컴퓨터라는 하나로 작동할 수 있는 것 -> 기본 설계가 존재하기 때문

이 설계에 맞춰서 여러 하드웨어 개발. 조립해서 컴퓨터 탄생

이런 설계를 컴퓨터 구조라고 부름.

---

CPU가 사용하는 명령어롸 관련된 설계를 명령어 집합구조(ISA)라고 한다.

널리 사용되는 ISA중 하나는 인텔의 x86-64 아키텍쳐.

---

컴퓨터구조 -> 컴퓨터가 효율적으로 작동할 수 있도록 하드웨어 및 소프트웨어의 기능을 고안하고 구성하는 방법.

컴퓨터의 기능 구조에 대한 설계, 명령어 집합구조, 마이크로 아키텍쳐, 기타 하드웨어 및 컴퓨팅 방법에 대한 설계 등이 포함.

대표적으로 폰 노이만 구조, 하버드 구조, 수정된 하버드 구조가 있음.

CPU의 하드웨어적 설계는 마이크로 아키텍처 라고 불리며, 정의된 명령어 집합을 효율적으로 처리할 수 있도록 CPU의 회로를 설계하는 분야.

폰 노이만 구조와 ISA중 x86-64에 대해 배워보자.


### 폰노이만 구조

폰 노이만은 컴퓨터에 연산, 제어, 저장 세가지 핵심 기능이 필요하다고 생각.

근대 컴퓨터는 연산과 제어를 위해 중앙처리장치(CPU), 저장을 위한 기억장치(Memory),를 사용.
그리고 장치간 데이터나 제어신호를 교환할 수 있도록 bus라는 전자 통로 사용.


![image](https://user-images.githubusercontent.com/94778099/229751182-5b627bb6-9f8e-4a4d-802e-f66421b59c36.png)


CPU

프로그램의 연산처리, 컴퓨터의 두뇌 역할.

코드 불러오고 실행하고 저장하는 모든 과정이 CPU에서 일어난다.

산술/논리 연산을 처리하는 산술논리장치(ALU)와 CPU를 제어하는 제어장치(Control unit), CPU에 필요한 데이터를 저장하는 레지스터로 구성.




기억장치

컴퓨터가 동작하는데 필요한 여러 데이터를 저장하기 위해 사용

주기억장치와 보조기억장치로 분류.

프로그램 실행 과정에서 필요한 데이터들을 임시로 저장하기 위해 사용되는 RAM.

반대로 장기간 보관하기 위해 사용되는 HDD와 SSD.



버스

컴퓨터 부품과 부품 사이 또는 컴퓨터와 컴퓨터 사이에 신호를 전송하는 통로

데이터버스 - 데이터가 이동

주소버스 - 주소를 지정 

제어버스 - 읽기/쓰기 제어

가 있고 이 외에도 랜선이나 데이터 전송 소프트웨어, 프로토콜 등도 버스라고 불리운다.


명령어 집합 구조(ISA)

CPU가 해석하는 명령어의 집합.

프로그램은 기계어로 이루어져 있고, 실행하면 이 명령어들을 cpu가 읽고 처리.


ISA는 여러가지가 있다.


인텔의 X86-64 -> 고성능 프로세서를 설계하기 위해 사용

많은 전력 소모, 발열이 심함. 그러므로 안정적으로 전력 공급하고 냉각할 수 있는 PC가 적합.

드론, 공유기, 인공지능 스피커 같은 임베디드 시스템에선 불가능.

전력과 발열소모가 적은 ARM이나 MIPS 또는 AVR의 프로세서 사용.



X86-64 아키텍처

32비트 CPU아키텍처인 IA-32를 64비트에서 쓸 수 있도록 확장.


n비트 아키텍처 -> cpu가 한번에 처리할 수 있는 데이터의 크기.

컴퓨터 과학에서 CPU가 이해할 수 있는 데이터의 단위라는 의미에서 WORD라고 부름.

32비트 아키텍처에서 ALU는 32비트까지 계산 가능

레지스터의 용량 및 각종 버스들의 대역폭이 32비트.

이들로 구성된 CPU는 설계 상 32비트의 데이터까지만 처리 가능.


WORD가 크면 뭐가 유리할까?

32비트 아키텍처에서는 4기가 바이트가 최대로 제공 가능한 가상 메모리의 크기.

64비트 아키텍처에선 이론상 16엑사 바이트(엄청큼)의 가상메모리를 제공 가능.

아무튼 가상 메모리 제공부터 넘사벽이다.


### x86-64 아키텍처 레지스터

레지스터 - CPU가 데이터를 빠르게 저장하고 사용할 때 이용하는 보관소.

산술에 필요한 데이터 저장, 주소 저장, 참조, 다양한 용도로 사용

x64 아키텍처에는 범용 레지스터, 세그먼트 레지스터, 명령어 포인터 레지스터, 플래그 레지스터가 있음.


### 범용 레지스터

주용도는 있지만 그 외에 다양한 용도로 사용될 수 있는 레지스터

X86-64에서 각각의 범용 레지스터는 8바이트 저장 가능. 2^64-1까지의 수 나타낼 수 있다.

자주 쓰이는 범용 레지스터들. 이 외에도 r8,r9.. r15까지의 범용 레지스터까지 존재.


이름  -  주용도

rax (accumulator register) - 함수의 반환 값

rbx (base register) - 주된 용도 X

rcx (counter register) - 반복문의 반복 횟수, 각종 연산의 시행 횟수

rdx (data register) - 주된 용도 X

rsi (source index) - 데이터를 옮길 때 원본을 가리키는 포인터

rdi (destination index) - 데이터를 옮길 때 목적지를 가리키는 포인터

rsp (stack pointer) - 사용중인 스택의 위치를 가리키는 포인터

rbp (stack base pointer) - 스택의 바닥을 가리키는 포인터


### 세그먼트 레지스터

x64 아키텍처에는 cs, ss, ds, es, fs, gs 총 6가지의 세그먼트 레지스터가 존재.

각 레지스터의 크기는 16비트.

과거엔 비트가 적어서 방법을 이용해 접근할 수 없는 주소에 접근햇엇는데 64비트가 되고 나서는 사용 가능한 주소 영역이 굉장히 넓어져서 이런 용도로는 사용 ㄴ

현대의 x64에서 cs, ds ss 레지스터는 코드 영역과 데이터, 스택 메모리 영역을 가리킬 때 사용.

나머지 레지스터는 운영체제 별로 용도를 결정할 수 있게 범용적인 용도로 제작됨.


### 명령어 포인터 레지스터

프로그램 -> 기계어 코드로 이루어 짐.

CPU가 어느 부분의 코드를 실행할지 가리키는게 명령어 포인터 레지스터의 역할.

이름은 rip이며 크기는 8바이트.


### 플래그 레지스터

프로세서의 현재 상태를 저장하고 있는 레지스터.

x64에선 RFLAGS라고 불리는 64비트 크기의 플래그 레지스터가 존재. 과거 16비트 플래그 레지스터가 확장된 것.

깃발을 올리고 내리는 형식으로 신호를 전달하듯 자신을 구성하는 여러 비트들로 CPU의 현재 상태를 표현.

64비트라 64개 쓸 수 있지만 거의 20개만 사용함.

![image](https://user-images.githubusercontent.com/94778099/229761982-6f2a02c4-1e2b-46d6-994a-05c9ab3682d7.png)


자주사용하는 것

CF(Carry Flag) 부호 없는 수의 연산 결과가 비트의 범위를 넘을 경우 설정.

ZF(Zero Flag) 연산의 결과가 0일경우 설정.

SF(Sign Flag) 연산의 결과가 음수일 경우 설정.

OF(Overflow Flag) 부호 있는 수의 연산 결과가 비트 범위를 넘을경우 설정.


플래그 사용하는 간단한 예시.

3의 값을 가지는 a, 5의 값을 가지는 b

a에서 b를 빼면 연산의 결과가 음수이므로 SF가 설정.

CPU는 SF를 통해 a가 b보다 작았음을 알 수 있음.


### 레지스터 호환
![image](https://user-images.githubusercontent.com/94778099/229764524-2da7be4d-b28f-4602-9557-534d6bc67f2c.png)


### 요약

범용 레지스터 - 주 용도는 있으나 그 외 용도로도 자유롭게 사용 가능. rax, rbx, rcx, rdx, rsi, rdi, rsp ,rbp, r8~r15가 있음.

세그먼트 레지스터 - 과거엔 메모리 세그멘테이션이나 가용 메모리 확장을 위해 사용 됐는데 요즘엔 메모리 보호로 사용. cs, ss, ds, es, fs ,gs 가 있음.

플래그 레지스터 - 현재의 cpu상태를 저장하는 레지스터

명령어 포인트 레지스터 - CPU가 사용해야 할 코드를 가리킴. x64에선 rip가 잇음.



----


### call 함수

1. call (주소값) 코드에 rip레지스터가 도달.
2. call 다음 명령어 수행 해야 하므로 call 명령어가 있던 다음 주소값을 스택에 저장함.
3. rip을 이동시킴.

결론. rip의 값은 call 되는 주솟값으로 이동. rsp(사용중인 스택의 현재 위치)는 한칸 위로 올라가게 됨.

![image](https://user-images.githubusercontent.com/94778099/230279976-5ed4d240-3d23-4e14-8ffd-ea677c1644e0.png)

### leave 함수

우리가 쓰는 stack 공간엔 여러가지의 스택이 있음.

예를들어 3f8이 rsp고 rbp가 400인 스택과

408이 rsp고 rbp가 418인 스택.

우리가 위에꺼 스택을 쓰다가 다른 스택을 접근할려면 지역변수가 오염될 수 있기 떄문에 leave를 써서 탈출해야 함.

![image](https://user-images.githubusercontent.com/94778099/230280634-aa3a6117-7c80-4a4a-93fd-63c2571c88a5.png)

### ret 함수

우리가 call을 쓰면 스택에 주솟값이 저장되고 call뒤에 적혓던 주솟값으로 rip이 이동했었다

이제 스택에 있던 주솟값으로 다시 돌아가서 실행되는게 ret함수다.

call 0x401000이 되면 rip은 0x401000으로 이동.

그 다음 주솟값인 0x400005는 스택에 저장된다.

rip은 0x401000에서 잘 실행되다가 0x401008에서 ret를 만나게 된다.

그러면 rip은 스택에 저장되어 있던 0x400005으로 이동하게 되고 사용중인 현재의 스택 위치인 rsp는 한칸 내려가게 된다.



---
PE파일

Portable Excutable 파일 은 윈도우 실행파일이라고 부름.
윈도우에서 사용되는 거라고 생각 ㄱㄱ
Unix의 COFF(Common Object File Format)기반으로 만들어 짐.

PE 파일 종류

실행계열			-EXE, SCR
라이브러리 계열		-DLL, OCX, CPL, DRV
드라이버 계열		-SYS, VXD
오브젝트 파일 계열		-OBJ

OBJ파일 빼고 다른것들은 실행이 가능한 파일이다.
DLL, SYS는 다른 형태의 실행방법(디버거, 서비스, 기타)을 이용하여 가능.

메모장 파일을 뜯어서 헥스데이터로 보면
000000E0을 보면 50 45 00 00 4C.. 로 되어 있는데 50 45가 PE를 뜻한다.
그리고 위에 보면 MZ라고 되어있는데(MZ세대아님) 그것도 PE파일임을 뜻하는 것중 하나
뒤에서 설명 할 예정


PE구조

다양한 정보 PE Header에 구조체 형식으로 저장.
Dos header 부터 section header까지 PE Header. 밑에 section들은 PE BODY
파일에서는 offset, 메모리에서는 VA(버츄얼 어드레스)로 위치를 표현.

Offset, VA, RVA
파일에선 Offset, 메모리에선 VA로 위치표현.

Offset			-파일의 첫 바이트 부터 거리
VA(버츄얼 어드레스)	-프로세스 가상 메모리의 절대주소
RVA(Relative Virtual Address)-기준(ImageBase)으로부터 상대 주소.

VA = RVA + ImageBase

PE Header에 많은 정보들은 RVA형태로 된 것들이 존재한다.
왜?
PE파일이 가상 메모리의 특정 위치에 로딩될 때
다른 PE 파일이 로딩되어 있을 수 있어서 재배치 과정을 통해 빈 공간에 로딩 되어야 해서.

만약 VA로 되어 있으면 정상적으로 안되는데, RVA로 되어있다면 재배치가 발생되어도
ImageBase에 대한 상대주소는 안바뀌어 문제없이 액세스가 가능하다..

아무튼 헤더에는 RVA형태로 존재한다.

Null Padding
섹션들 보면 사이사이 null이 있음
파일이나 메모리에서 섹션 시작 위치는 각각 최소 기본 단위의 배수에 해당하는 위치.
그래서 빈공간은 NULL로 채움
보면 파일에선 00000400 00007C00, 00008400으로 시작하고
메모리에선 01001000, 01009000, 0100B000으로 시작하는 거 보면 알듯.

이거를 Alignment라고 하는데 내부 연산 등 처리상의 효율성을 위해 그랬다.



이제 DOS Header에 대해 알아보자

FILE에서 헤더부분 중 제일 위에 있는 친구다

DOS 파일에 대한 하위 호환성을 고려해서 만들어 짐.
구조체 이름은 _IMAGE_DOS_HEADER
winnt.h에 정의 되어 있고, 64바이트임.

주요 멤버

e_magic
	DOS signature(매직넘버)임.
	PE파일을 나타내는 첫 2바이트이고, MZ(4D5A)로 고정되어 있음.
	MZ가 아니면 로더는 해당파일을 PE로 인식 안함.
	왜 MZ냐면 설계한 이름 이름 이니셜임.

e_lfanew
	NT Header가 시작되는 위치의 오프셋을 뜻함.
	e_lfanew값이 가리키는 위치에 NT Header 구조체가 있어야 한다.
	파일마다 값이 다름.

//

DOS stub 부분
위에 헤더 다음줄에 있는 곳.
00000040 ~ 000000D0 까지 (불 규칙 한듯?)(PE 전까지인듯?)

DOS환경에서 실행되는 코드를 가진 영역이다. 16비트 어셈블리 명령어, 32비트 윈도우 OS에선 실행X
그 말은 DOS stub 없어도 실행은 된다는 거다.
여기 적힌건 일종의 옵션임.

코드와 데이터의 혼합으로 이루어 졌고, DOS에서 실행하면 This program cannot be run in DOS mode
출력하고 종료한다고 한다.


그 다음 NT Header에 대해 보자
이 역시 winnt.h에 정의되어 잇음.

구조체 이름은 _IMAGE_NT_HEADERS
DOS Header의 멤버 중 e_lfanew에 저장된 주솟값이 이 부분을 가리킨다.
NT Header은 파일 실행에 필요한 정보가 저장되어 있다(중요한 부분)
NT Header의 구조체에는 총 3개의 멤버로 구성되어 있다.

1. Signature	2.File Header	3.Optional Header

하나씩 알아 보자.

Signature는 제일 첫 멤버로 50 45 00 00 h(헥스라는 뜻인듯) 를 가진다 (변경할 수 없다고 한다.)
50 45 00 00 은 PE 00 을 뜻함

NT Header의 File Header

winnt.h 에 구조체가 존재함.

아래 적을 멤버 4가지 -> 정확한 세팅이 아닐 시 정상적으로 파일 실행이 불가. (중요)

---

Machine	- 파일의 실행 대상 플랫폼을 나타냄. 예를들어 Machine이 IMAGE_FILE_MACHINE_I386(0x014c)면 32비트고..
IA64(0x0200)면 Intel Itanium, AMD64(0x8664)면 x64처럼 플랫폼을 나타냄.

---

NumberOfSections - 코드, 데이터, 리소스 등의 섹션 개수를 뜻함. -> 반드시 0보단 클 것

정의된 섹션 개수 > 실제 섹션 개수 -> 실행 에러

정의된 섹션 개수 < 실제 섹션 개수 -> 정의된 개수만큼 인식이 됨.

---

SizeOfOptionalHeader - 다음에 나오는 Optional Header 구조체의 크기를 알려준다.

---

Characteristics - 파일의 속성을 나타내는 값. 실행파일인지 DLL파일인지 등 정보들이 bit OR연산을 통해 최종값으로 설정됨.

exe파일이면 (0x0002) dll파일이면 (0x2000) 이런 식..

---

TimeDateStamp - 파일의 실행에 영향을 미치지 않는 값. 해당 파일의 빌드 시간을 나타냄.


![image](https://github.com/19GHYun/2023_01/assets/94778099/b4de5f32-e239-48b3-94d3-c5e713fbea05)

리틀 엔디안 이니까 저렇게 들어간거임.

처음 2개 -> 뒤에서 01 4C -> x86 -> 32비트

00 03 -> NumberOfSection. 파일에 존재하는 섹션 갯수는 3개

TimeDateStamp -> 그 1초마다 1증가해서 나온 값인듯 하다. 48 02 52 87 이 되겠지. 이건 2008년 어쩌구를 뜻함

Offset to Symbol table -> 00 00 00 00

Number of symbols -> 00 00 00 00

Size of optional header -> 00 E0 -> 다음에 이어지는 Optional Header의 길이는 16 * 14

Characteristics -> 01 0F -> bit or연산 해가지고 이렇게 된거 같은데 아무튼 저거 4개 정의되어 잇다.

---

NT헤더의 Optional Header ㅈㄴ 김

---

Magic - 이 친구가 0x10B면 구조체가 32비트 구조체고 0x20B면 64비트 구조체.

---

AddressOfEntryPoint - 파일이 메모리에 매핑된 후 코드 시작 주소. ImageBase값에 이 값을 더해서 코드 시작 지점을 설정한다.

(Entry Point의 RVA를 가짐)

---

ImageBase - PE파일이 로딩되는 시작 주소.(메모리에)

EXE와 DLL파일은 user memory 영역인 0~ 7FFFFFFF 사이에 위치하고 SYS파일은 Kernel memory영역인 80000000 ~ FFFFFFFF에 로딩된다.

ImageBase 값에 AddressOfEntryPoint값이 더해져서 그 코드가 어디 메모리에 저장되기 시작한지 알 수 있다.

ImageBase들은 같겠지만 프로그램들 마다 AddressOfEntryPoint가 다를 것.

PE파일이 로딩 -> PE파일이 실행 -> 프로세스가 생김 -> 프로세스가 메모리에 로딩 -> EIP레지스터 값이 세팅 -> ImageBase + AddressOfEntryPoint의 값이 셋팅.

그러면 그 프로세스가 실행 될 듯?

---

SetionAlignment, FileAlignment - 메모리/파일에서 섹션의 최소 단위를 나타내며, 이 두개 값은 같거나 다를 수 있음. 각 섹션은 반드시 Alignment의 배수여야 한다.

섹션에서 크기가 남아도 0으로 채워서 Alignment값을 맞춤.

---

SizeOfImage - 메모리에 로딩될 때 가상 메모리에서 PE Image가 차지하는 크기.

일반적으로 파일 크기와 로딩된 크기는 다름. 각 섹션의 로딩 위치와 메모리 점유 크기는 섹션 헤더에 정의된다.

---

SizeOfHeader - PE파일 헤더의 전체 크기. -> FileAlignment의 배수임.

파일 시작에서 SizeOfHeader 옵셋만큼 떨어진 위치에서 첫번째 섹션이 존재한다.

---

Subsystem - 동작 환경을 정의한 것. 이 값을 통해 sys인지 exe인지 dll인지 구분. 0x1이면 sys 0x2면 GUI 0x3이면 CLI

---

NumberOfRvaAndSize - DataDirectory배열의 개수. 일반적으로 16개의 디렉터리를 가지지만 해당 멤버로 디렉터리 수를 정할 수 있음. 이 말은 일반적으로 16이지 16이 아닐 수 있다.

---

DataDirectory
![image](https://github.com/19GHYun/2023_01/assets/94778099/53879503-0592-4fe1-9025-44cd72684818)

IMAGE_DATA_DIRECTORY구조체의 배열로써 디렉토리 별로 각각의 정보를 담는다.

Export Directory - DLL등의 파일에서 외부에 함수를 공개하기 위한 정보들을 가짐.

Import Directory - 프로그램 실행을 위해 Import하는 DLL이름과 사용할 함수 정보가 담긴 INT주소와 IAT주소 같은 정보가 담김.

TLS Directory - 스레드 지역 저장소 초기화 섹션에 대한 포인트

IAT Directory - IAT의 시작번지를 가리킨다.

https://kit6509.tistory.com/entry/IMAGEDATADIRECTORY-%EA%B5%AC%EC%A1%B0%EC%B2%B4-%EB%B0%B0%EC%97%B4

![image](https://github.com/19GHYun/2023_01/assets/94778099/0077791a-0a26-4103-9495-5fc0ab7a7267)

이렇게 0부터 14까지 15개로 있고 나머지 16번째는 0으로 채워져 있다고 한다.

![image](https://github.com/19GHYun/2023_01/assets/94778099/cb5e45b3-2413-4a02-81b9-003ddccf4653)

처음부터.

magic -> 01 0B  -> IMAGE_OPTIONAL_HEADER32구조체

magic linker version.. minor linker version .. size of code .. size of initialized data .. size of uninitialized data.. 를 지나고

address of entry point -> 00 00 73 9D

base of code .. base of data.. 를 지나고

imagebase -> 01000000 -> DLL파일이라




![image](https://github.com/19GHYun/2023_01/assets/94778099/712eef4b-70cc-4404-bad8-2824e38b1fc6)

section alignment -> 00 00 10 00 -> 최소 단위 16 * 16 * 16.

file alignment -> 00 00 02 00 -> 최소 단위 2 * 16 * 16

major OS version.. minor OS version .. major image version.. minor image version .. major subsystem version.. minor subsystem version.. win32 version value 을 지나고

size of image -> 00 01 40 00 -> 메모리가 로딩될 때 가상 메모리에서 PE Image가 차지하는 크기는 저정도



![image](https://github.com/19GHYun/2023_01/assets/94778099/250f0186-96e0-4632-87a9-e264146e794e)


size of headers -> 00 00 04 00 -> PE Header 의 전체 크기는 00 00 04 00 위의 file alignment의 배수임을 확인 가능

checksum을 지나고

subsystem -> 00 02 -> 동작환경 GUI으로 세팅 되어잇음.

DLL characteristics... size of stack reserve... size of heap reserve... size of heap commit.. loader flags.. 를 지나고

number of directories 




