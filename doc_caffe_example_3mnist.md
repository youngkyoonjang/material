---
title: C++ Example 3. MNIST dataset (python)
tags: [caffe]
keywords: start, introduction, begin, install, build, hello world,
last_updated: August 12, 2015
summary: "세 번째 예제는 MNIST 데이터셋을 읽어오도록 하겠습니다"
---


## MNIST 데이터셋 및 LMDB 준비

이번에는 MNIST 데이터셋 및 LMDB에 대해서 알아봅니다. MNIST 데이터는 기계학습에서 대표적으로 많이 사용되는 벤치마킹 데이터입니다. 28 0에서부터 9까지 10가지의 손글씨 이미지가 있는데요. 이미지 크기는 28x28, 트레이닝 이미지는 60,000장, 테스트 이미지는 10,000장으로 이루어져 있습니다. 

이번 시간에는 Caffe에서 사용하는 LMDB포멧을 이용하여 MNIST 데이터를 읽어보고 python을 이용하여 시각화를 해보도록 하겠습니다.

### MNIST 데이터셋 다운로드


    
