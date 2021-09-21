---
layout: sinlge
title:  "java_BufferedReader, StingTokenizer&String.split()"
---
#java_BufferedReader, StingTokenizer&String.split()

BufferedReader은 이름처럼 버퍼를 이용하여 읽고 쓰는 함수이다. 
이 함수는 버퍼를 이용하기 때문에 이 함수를 이용하면 입출력의 효율이 비교할 수 없을 정도로 좋아진다. 


나는 항상 Scanner를 이용하여 입력을 받아왔다. 
Scanner는 띄어쓰기와 엔터를 경계로 입력 값을 인식하기 때문에 따로 가공할 필요가 없어서 사용하기 매우 편리하다. 
반면에 BufferedReader는 엔터만 경계로 인식하고 받은 데이터가 String으로 고정되기 때문에 데이터를 따로 가공해야해서 조금 번거롭다. 
이러한 이유에도 불구하고 BufferedReader를 쓰는 이유는 Scanner에 비해서 **빠르기** 때문이다.

버퍼를 사용하지 않는 입력은 *키보드의 입력이 키를 누르는 즉시 바로 전달된다*. 
버퍼를 사용하는 입력은 *키보드의 입력이 있을 때마다 한 문자씩 버퍼로 전송한다. 그 후 버퍼가 가득 차거나, 개행 문자가 나타나면, 버퍼의 내용을 한 번에 전송한다.*

한 번 거쳐가는데도 더 빠른 이유는 하드 디스크는 원래 속도가 굉장히 느리다. 하드뿐만 아니라 키보드나 모니터와 같은 외부 장치와의 데이터 입출력은 생각보다 시간이 걸리는 작업이다. 버퍼링 없이 키보드가 눌릴 때마다 눌린 문자의 정보를 목적지로 바로 이동시키는 것보다 중간에 메모리 버퍼를 둬서 데이터를 한번에 묶어서 이동시키는 것이 더욱 효율적이고 빠르기 때문이다. 

예시로 흙을 파서 버릴때, 한번 삽질할 때마다 가서 버리는 것보다, 수레에 가득 채워서 한번에 나르는 것이 더 효율적인것과 같은 것이다. 즉, 모아뒀다가 한 번에 전송하는게 훨씬 더 효율적이다.

공식 문서에는
*Reads text from a character-input stream, buffereing characters so as to provide for the efficient reading of characters, arrays, and lines. The buffer size may be specified, or the default size may be used.*
**입력 스트림에서 문자를 읽는 함수인데, 문자나 배열, 라인들을 효율적으로 읽기 위해서 문자들을 버퍼에 저장하고(버퍼링) 읽는 방법을 취한다. 버퍼 사이즈는 우리가 지정할 수도 있지만 지정안할 경우에는 기존 디폴트 사이즈가 사용된다.**
라고 나와있다.

##BufferedReader 사용법
###선언
*import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;*
public static void main(String[] args)*throws IOEception{}*
필요


```python
import java.io.BufferedReader;
import java.io.IOExeption;
import java.io.InputStreamReader;

class BufferedReader{
    public static void main(String[] args)throws IOException{  //  throws IOException -> 예외처리
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        String s = br.readLine();  //  String                                                    
        int i = Integer.parseInt(bf.readLine());  //  Int 형변환                                              
    }
}
```

###Read한 데이터 가공 

방법 1. StringTokenizer 사용
*import java.util.StringTokenizer;*
필요 


```python
StringTokenizer st = new StringTokenizer(s);  //  StringTokenizer인자값에 입력 문자열 넣음   
int a = Integer.parseInt(st.nextToken());  //  첫번째 호출
int b = Integer.parseInt(st.nextToken());  //  두번째 호출                                                            
```

방법 2. String.split() 사용


```python
String array[] = s.split(" ");  //  공백마다 데이터끊어서 배열에 넣음
```

####StringTokenizer는 빈 문자열을 토큰으로 인식하지 않지만 split는 빈 문자열을 토큰으로 인식하는 차이가 있다. 
StringTokenizer는 결과값이 문자열이라면 split는 결과 값이 문자열 배열이다.

보통 속도면에서는 StringTokenizer을 사용하는 것이 유리하다. 다만 복잡한 문자열을 정규표현식을 이용하여 분리할 경우에는 String.split()을 이용하는 것이 옳다. 


```python

```
