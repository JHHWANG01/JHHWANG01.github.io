---
layout: archive
permalink: /portfolio-archive/
title: "Posts by Portfolio"
author_profile: true
---

<hr>
# <center> Skill-Portfolio </center>

#### 개인신상

* 성 명
    `황정현`
* 생년월일
    `1994.01.01`
* 연락처
    `010-2254-0970`
* 이메일
    deert101@gmail.com

#### 최종학력사항

`2009.03 ~ 2012.03`  수원 동원고등학교 <br><br>
`2014.01 ~ 2015.10` 군대 <br><br>
`2013.03 ~ 2019.03`  한신대학교 (정보통신학부) <br><br>

#### 자격증 & 어학점수

`2012.01` 운전면허증 <br>
`2017.08` 토익 615 <br>
`2018.11` 정보처리기사 <br>

#### 학교 활동

`2015.03 ~ 2016.03` 실습실 조교 (근로 장학) <br><br>
`2016.03 ~ 2017.12` 인터넷 어플리케이션 랩실장 <br><br>
`2017.03 ~ 2018.06` 신입생 세미나 교육 <br><br>
`2017.03 ~ 2017.12` 유닉스 조교 , 운영체제 조교 <br><br>
`2018.03 ~ 2018.06` 논문(창문 관리 시스템) <br><br>

#### 인턴
`2018.09 ~ 2018.12` (주) 뉴젠씨앤아이 (4개월)<br> <br>
`실무`   회사 제품의 이슈 확인 및 테스트 <br> <br>
	테스트 결과 토대로 문서작업 <br> <br>
	회사 제품 가이드 제작<br><br>
	유지보수 툴 개발 <br> <br>

#### 프로젝트 수행사항

`2018.03 ~ 2018.06` 
	* 아두이노와 앱 인벤터를 이용한 환경수치확인 <br>
	* 아두이노와 앱 인벤터 활용 <br>
`2018.03 ~ 2018.06` 
	* 유지보수 툴 개발 <br>
	* 자바 스윙을 사용하여 유지보수에 필요한 정보 파싱. <br>

## <Center> Project Report</Center>

- Project Name : 아두이노와 앱 인벤터를 창문관리시스템
- 참가인원 : 2명
- 앱 인벤터 코딩 및 아두이노 코딩
- 수행목표 : 안드로이드 폰과 연결하여 각 환경정보 확인해줌.
- 사용기술 : Arduino , C , Appinventor
- 주요 코드

```java
if (Serial1.available())
 {
   data=Serial1.read();
   delay(1);
 }

    if(data=='1'){
    window_open();
     delay(1000);
     }
    else if(data=='2'){
     window_close();
     delay(1000);
   }
  if(data=='3'){
    blind_open();
     delay(1000);
     }
    else if(data=='4'){
     blind_close();
     delay(1000);
   }
}

float getdust()
{
 digitalWrite(ledPower, LOW); // power on the LED
 delayMicroseconds(delayTime);

 dustVal=analogRead(dustPin);
 calcVoltage = dustVal * (5.0 / 1024);

 delayMicroseconds(delayTime2);

 digitalWrite(ledPower, HIGH);
 delayMicroseconds(offTime);
 delay(100);

  dustDensityug = (0.17 * calcVoltage - 0.1)*1000;
  return (dustDensityug);
}
```
- 개발 내용 (동영상 봐주시기 바랍니다.)
  1. 미세먼지 , 수분감지 , 자외선 감지 센서 이용<br>
  2. 각 환경에 따라 핸드폰에 나오는 그림변경 <br>
      - ex ) 비가오면 비 그림 
  3. 미세먼지가 높으면 창문 모터 회전 <br>
  4. 수분 감지 센서에 감지되면 창문 모터 회전 <br>
  5. 자외선 수치가 높으면 창문 모터 회전 <br>
  
![어플흐름도](/assets/images/미세먼지 툴/어플리케이션 흐름도.png) <br> <br>
![앱인벤터코딩1](/assets/images/미세먼지 툴/앱인벤터.png) <br> <br>
![앱인벤터코딩2](/assets/images/미세먼지 툴/앱인벤터 화면구성.png) <br> <br>




- 프로젝트 동영상
    - [해당영상](https://youtu.be/WEudRjVYw7s})



## <Center> Project Report</Center>

- Project Name : 유지보수 툴 개발
- 참가인원 : 2명
- 자바 코딩
- 수행목표 : 자바 스윙을 이용하여 유지보수에 필요한 정보 파싱
- 사용기술 : Java, Mssql, AES256 , SHA256, log back
- 주요 코드 일부

```java
static int cpui=1000, cpucal=0;
	static double cpuload, cpuj=0.0 , cpusum=0, CPUsage=0;
	static String cpuresult = null;
	//CPU 사용량
	public String SystemCPU() {
		String result = null;
		final OperatingSystemMXBean osBean = (com.sun.management.OperatingSystemMXBean)ManagementFactory
	    		.getOperatingSystemMXBean();

	    while(cpui<=3000){ //총 3초. 3번 측정. (맨 처음에 측정되는 값은 제외시킬거임)
	    	cpuload = osBean.getSystemCpuLoad();

	    	if(cpuload < 0.0)
	    		continue;

	    	CPUsage=cpuload*100;
	    	//System.out.println("CPU Usage : "+Math.round(CPUsage)+"%");

	    	if(cpui>1999) //처음에 측정되는 cpu값은 제외하는 조건문
	    		cpusum += CPUsage;
	    	try {
	    		Thread.sleep(cpui);
	    	} catch (InterruptedException e) {
	    		e.printStackTrace();
	    	}
	    	cpui=cpui+1000; //1초 증가시키는 증감식. 1000 == 1초
	    	cpuj++;
	    }
	    cpucal = (int) Math.round(cpusum/(cpuj-1)); //평균값 계산

	    if(serverPcRISKCase.equals("1")) { //serverPcRISKCase 는 환경설정(Preferences)에서 가져오는거임.
	    	if(cpucal < 50) {
	    		cpuresult = "양호";
	    		result = "CPU : " + Integer.toString(cpucal) + "%";
	    	}
	    	else if(cpucal < 80) {
	    		cpuresult = "점검필요";
	    		result = "CPU : " + Integer.toString(cpucal) + "%\n" + "(담당자와 상의하여 불필요한 프로세스 중지 안내)";
	    	}
	    	else {
	    		cpuresult = "점검필요";
	    		result = "CPU : " + Integer.toString(cpucal) + "%\n" + "(담당자와 상의하여 불필요한 프로세스 중지 안내)";
	    	}
	    }
	    else if(serverPcRISKCase.equals("2")) {
	    	if(cpucal < 80) {
	    		cpuresult = "양호";
	    		result = "CPU : " + Integer.toString(cpucal) + "%";
	    	}
	    	else {
	    		cpuresult = "양호";
	    		result = "CPU : " + Integer.toString(cpucal) + "%\n" + "(80%가 넘지만 case2 이므로 양호.)";
	    	}
	    }
	    else {
	    	cpuresult = "점검필요";
	    	result = "#환경설정에서 serverPcRISKCase 값을 다시 확인하시오.";
	    	logger.error("#환경설정에서 serverPcRISKCas 값 재확인");
	    }
		return result;
	}
	//CPU 사용량 양호기준 출력
	public String SystemCPUStatus() {
		return cpuresult;
	}
  ```


- 개발내용
  1. 목표 & 시작
  	![목표](/assets/images/유지보수툴/목표.png)<br><br>
	![시작](/assets/images/유지보수툴/시작.png) <br><br>
	![2](/assets/images/유지보수툴/2.png) <br><br>
	![3](/assets/images/유지보수툴/3.png) <br><br>
	
  2. 로그인 UI (__SHA256__ 암호화) / Password Change
  	![시작](/assets/images/유지보수툴/로그인.png) <br><br>
	
  3. 기본 정보 UI (텍스트 문서에 저장되어 있는 값을 암복호화(__AES__) 하여 불러옴)
  	![기본정보화면](/assets/images/유지보수툴/기본정보화면.png) <br><br>
	
  4. 알림창 (기본정보 - > 시스템 정보 넘어갈 때 5초 정도소요)
  	![알림창](/assets/images/유지보수툴/알림창.png) <br><br>
	
  5. 시스템 정보 
  	![시스템정보](/assets/images/유지보수툴/시스템정보.png) <br><br>
	
  6. __로그백__ 이용하여 오류에 대한 로그 정리
  	![logback](/assets/images/유지보수툴/logback.png) <br><br>
	
  7. 유지보수 수동화 과정 가이드.
   	![수동화툴](/assets/images/유지보수툴/수동화툴.png) <br>
  <br>


- 프로젝트 동영상
	- [해당영상](https://www.youtube.com/watch?v=zFkvgAK9E74&feature=youtu.be})
