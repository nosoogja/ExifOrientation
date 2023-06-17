# ExifOrientation
사진 정보중 Orientation 정보 처리

개발자로 일하다 보면 이미지 처리 업로드할 일이 생긴다.  아님 머 .... 돌아 가시....<br/>
폰으로 이미지를 업로드 하다 보면 Orientation 방향으로 사진이 회전되어서 처리가 된다.<br/>
이걸 해결해줄 오픈 소스는 있다.  <br/>
그런데 단 그냥 방향 정보 하나만 있으면 되는데 라는 생각이 크다.<br/>
그래서 함 그부분만 처리하는 걸 만들어 보려 노력 하였다.<br/>
캘럭시와 아이폰으로 찍은 사진은 확인을 하였으나 다른 형식이 <br/>
어떠한 방식으로 얻어 지는지 알 수 없고 구하기 어려워 구해지면 해봐야 겠다.<br/>
위 두 기기만 해도 byte align 이 다른것 같다.<br/>

대부분 브라우져가 이미지처리를 해주지만 약간식 다른 것들은 있다.<br/>
아이폰 사파리 브라우져에서 사진을 Canvas Element 에서 그리게 되면<br/>
회전된 방향으로 그려지게 된다. chrome 은 정방향으로 그려진다.<br/>

## 참고
https://www.media.mit.edu/pia/Research/deepview/exif.html
https://exiv2.org/tags.html

## m1.jpg Binary
![result()](m1.jpg)

-- m1.jpg 파일 처음 1000 bytes
ff d8 ff e0 00 10 4a 46 49 46 00 01 01 01 00 60 00 60 00 00     // (20 bytes)
ff e1 09 aa 45 78 69 66 00 00                                   // (10 bytes)
49 49 2a 00 08 00 00 00 0d 00                                   // (10 bytes) offset to data stored address 가 이곳부터 시작인듯.
0b 00 02 00 22 00 00 00 aa 00 00 00     // ProcessingSoftware
00 01 04 00 01 00 00 00 0a 00 00 00     // ImageWidth
01 01 04 00 01 00 00 00 08 00 00 00     // ImageLength
0f 01 02 00 06 00 00 00 cc 00 00 00     // Make
10 01 02 00 09 00 00 00 d2 00 00 00     // Model
12 01 03 00 01 00 00 00 01 00 00 00     // Orientation
1a 01 05 00 01 00 00 00 dc 00 00 00     // XResolution
1b 01 05 00 01 00 00 00 e4 00 00 00     // YResolution
28 01 03 00 01 00 00 00 02 00 00 00     // ResolutionUnit
31 01 02 00 07 00 00 00 ec 00 00 00     // Software
32 01 02 00 14 00 00 00 f4 00 00 00     // DateTime
13 02 03 00 01 00 00 00 01 00 00 00     // YCbCrPositioning
69 87 04 00 01 00 00 00 08 01 00 00     // Exif Offset
d4 06 00 00 
6e 6f 6d 61 63 73 20 2d 20 49 6d 61 67 65 20 4c 6f 75 6e 67 65 20 33 2e 31 32 2e 31 2e 34 32 30 36 00 // nomacs - Image Lounge 3.12.1.4206
41 70 70 6c 65 00           // Apple
69 50 68 6f 6e 65 20 36 00  // iPhone 6
00 48 00 00 00 01 00 00 00 48 00 00 00 01 00 00 00 
31 32 2e 35 2e 37 00 00       // 12.5.7
32 30 32 33 3a 30 36 3a 30 37 20 31 31 3a 33 38 3a 31 30 00 // 2023:06:07 11:38:10
20 00 9a 82 05 00 01 00 00 00 8e 02 00 00 9d 82 05 00 01 00 00 00 96 02 00 00 22 88 03 00 01 00 00 00 02 00 00 00 27 88 03 00 01 00 00 00 50 00 00 00 00 90 07 00 04 00 00 00 30 32 32 31 03 90 02 00 14 00 00 00 9e 02 00 00 04 90 02 00 14 00 00 00 b2 02 00 00 01 91 07 00 04 00 00 00 01 02 03 00 01 92 0a 00 01 00 00 00 c6 02 00 00 02 92 05 00 
01 00 00 00 ce 02 00 00 03 92 0a 00 01 00 00 00 d6 02 00 00 04 92 0a 00 01 00 00 00 de 02 00 00 07 92 03 00 01 00 00 00 03 00 00 00 09 92 03 00 01 00 00 00 10 00 00 00 0a 92 05 00 01 00 00 00 e6 02 00 00 14 92 03 00 04 00 00 00 ee 02 00 00 7c 92 07 00 96 03 00 00 f6 02 00 00 91 92 02 00 04 00 00 00 35 32 36 00 92 92 02 00 04 00 00 00 35 32 36 00 00 a0 07 00 04 00 00 00 30 31 30 30 01 a0 03 00 01 00 00 00 
01 00 00 00 02 a0 04 00 01 00 00 00 c0 0c 00 00 03 a0 04 00 01 00 00 00 90 09 00 00 17 a2 03 00 01 00 00 00 02 00 00 00 01 a3 07 00 01 00 00 00 01 00 00 00 02 a4 03 00 01 00 00 00 00 00 00 00 03 a4 03 00 01 00 00 00 00 00 00 00 05 a4 03 00 01 00 00 00 1d 00 00 00 06 a4 03 00 01 00 00 00 00 00 00 00 32 a4 05 00 04 00 00 00 8c 06 00 00 33 a4 02 00 06 00 00 00 ac 06 00 00 34 a4 02 00 22 00 00 00 b2 06 00 00 
00 00 00 00 01 00 00 00 1e 00 00 00 0b 00 00 00 05 00 00 00 32 30 32 33 3a 30 36 3a 30 37 20 31 31 3a 33 38 3a 31 30 00 32 30 32 33 3a 30 36 3a 30 37 20 31 31 3a 33 38 3a 31 30 00 e7 b7 00 00 79 25 00 00 95 f4 02 00 90 4c 01 00 18 75 00 00 c3 22 00 00 00 00 00 00 01 00 00 00 53 00 00 00 14 00 00 00 eb 03 7a 05 62 02 64 02 41 70 70 6c 65 20 69 4f 53 00 00 01 4d 4d 00 11 00 01 00 09 00 00 00 01 00 00 00 0a 
00 02 00 07 00 00 02 2e 00 00 00 e0 00 03 00 07 00 00 00 68 00 00 03 0e 00 04 00 09 00 00 00 01 00 00 00 01 00 05 00 09 00 00 00 01 00 00 00 de 00 06 00 09 00 00 00 01 00 00 00 da 00 07 00 09 00 00 00 01 00 00 00 01 00 08 00 0a 00 00 00 03 00 00 03 76 00 09 00 09 00 00 00 01 00 00 01 13 00 0e 00 09 00 00 00 01 00 00 00 04 00 14 00 09 00 00 00 01 00 00 00 04 00 17 00 09 00 00 00 01 00 00 00 00 00 19 00 09 
00 00 00 01 00 00 00 00 00 1f 00 09 00 00 00 01 00 00 00 00 00 25 00 09 00 00 00 01 00 00 00 00 00 26 00 09 00 00 00 01 00 00 00 00 00 27 00 0a

------------------------------------------------------------------
