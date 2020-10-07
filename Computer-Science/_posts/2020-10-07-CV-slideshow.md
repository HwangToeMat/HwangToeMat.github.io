---
title: (ComputerVision) 01. SlideShow 만들기
image: https://github.com/HwangToeMat/HwangToeMat.github.io/blob/master/Computer-Science/image/CV/01/img0.png?raw=true
description: >
 ComputerVision을 본격적으로 공부하기전 OpenCV사용법을 익히기 위해 슬라이드쇼 기능을 구현해본다.
author: author1
layout: post
order: 16
---

# [ComputerVision] 01. SlideShow 만들기 - OpenCV 기초

ComputerVision을 본격적으로 공부하기전 OpenCV사용법을 익히기위해 슬라이드쇼 기능을 구현해보기

## 메인 코드

```python
def run(img_dir='image', screen='full', delay=2):

    img_lst = glob.glob('.\\{}\\*.jpg'.format(img_dir))

    if not img_lst:
        print("There are no jpg files in 'image' folder")
        sys.exit()

    if screen == 'full':
        # 전체 화면
        cv2.namedWindow('image', cv2.WINDOW_NORMAL) 
        cv2.setWindowProperty(
            'image', cv2.WND_PROP_FULLSCREEN, cv2.WINDOW_FULLSCREEN)
    elif screen == 'window':
        # 창 화면
        cv2.namedWindow('image', cv2.WINDOW_NORMAL)

    cnt = len(img_lst)
    idx = 0
    delay *= 1000

    while True:
        img = cv2.imread(img_lst[idx])

        if img is None:
            print('Image load failed!')
            break

        cv2.imshow('image', img)
        if cv2.waitKey(delay) >= 0: # 키보드 입력시 슬라이드 종료
            break

        idx += 1
        if idx >= cnt:
            idx = 0

    cv2.destroyAllWindows()
```

## 사용법

```
usage: SlideShow.py [-h] [--img_dir IMG_DIR] [--screen SCREEN] [--delay DELAY]

optional arguments:
  -h, --help         show this help message and exit
  --img_dir  이미지가 있는 폴더의 이름
  --screen  'window'입력시 창 모드, 'full'입력시 전체화면 모드
  --delay  슬라이드쇼에서 사진이 나오는 간격(초)
  
example:
  python SlideShow.py --screen window --delay 1 # 창 모드, 1초간격으로 실행
  
```

## 완성된 SlideShow의 모습

<img src="https://github.com/HwangToeMat/HwangToeMat.github.io/blob/master/Computer-Science/image/CV/01/img1.gif?raw=true" style="max-width:100%;margin-left: auto; margin-right: auto; display: block;">
