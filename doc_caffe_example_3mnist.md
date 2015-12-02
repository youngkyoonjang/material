---
title: C++ Example 3. MNIST dataset (python)
tags: [caffe]
keywords: start, introduction, begin, install, build, hello world,
last_updated: August 12, 2015
summary: "세 번째 예제는 MNIST 데이터셋을 읽어오도록 하겠습니다"
---

## MNIST 데이터셋 및 LMDB 준비

이번에는 MNIST 데이터셋 및 LMDB에 대해서 알아봅니다. MNIST 데이터는 기계학습에서 대표적으로 많이 사용되는 벤치마킹 데이터입니다.
28 0에서부터 9까지 10가지의 손글씨 이미지가 있는데요. 이미지 크기는 28x28, 트레이닝 이미지는 60,000장, 테스트 이미지는
10,000장으로 이루어져 있습니다. 자세한 내용은 MNIST [공식 페이지](http://yann.lecun.com/exdb/mnist/
)를 참고하세요.

이번 시간에는 Caffe에서 사용하는 LMDB포멧을 이용하여 MNIST 데이터를 읽어보고 python을 이용하여 시각화를 해보도록 하겠습니다.

### MNIST 데이터셋 다운로드

카페 소스에는 여러가지 유용한 툴들을 제공학 있는데요. 그 중의 하나가 데이터셋을 다운로드 받아서 LMDB로 변환하는 작업입니다. 먼저 아래와
같이 카페의 홈폴더($caffe_home) 아래에 있는 mnist 폴더로 이동해서 `get_mnist` 합니다.

```
cd $caffe_home/data/mnist
./get_mnist.sh
```

폴더 안에 4개 파일 (t10k-images-idx3-ubyte, t10k-labels-idx1-ubyte, train-images-
idx3-ubyte,
train-labels-idx1-ubyte) 이 다운로드 된것을 확인할 수 있습니다.

### LMDB 변환

이번에는 LMDB 파일로 변환해 보도록 하겠습니다. 변환 툴은 홈폴더 아래에 있는 examples/mnist 폴더 안에 있습니다. 한번 실행해
보죠.

```
cd $caffe_home
sh examples/mnist/create_mnist.sh
```

그럼 두 개의 폴더 (mnist_test_lmdb, mnist_train_lmdb)가 생성된걸 확인할 수 있습니다. 각 폴더에는 LMDB 형태로
트레이닝 데이터와 테스트 데이터가 생성되어 있습니다. 이런 식으로 카페에서는 공식적으로 LMDB 또는 LevelDB 포멧을 데이터로 사용합니다.
임의의 데이터는 둘 중 하나의 포멧으로 변환한 후에 사용해야 하는데요. 변환하는 C++ 코드는 다음번에 한번 알아보도록 하겠습니다.

## Python code


    %matplotlib inline
    import numpy as np
    import matplotlib.pyplot as plt
    import lmdb
    caffe_root = '/home/koosy/caffe/caffe/'
    import sys
    sys.path.insert(0, caffe_root + 'python')
    import caffe


    
