---
layout: post
title: "[Python] 실행 시간 측정 코드와 Random Batch"
date: 2023-06-03 21:46:29+0900
description: 코드 실행 시간을 재는 스니펫과, 랜덤 배치를 뽑을 때 NumPy와 Torch 중 어느 쪽이 빠른지 비교.
tags: ms
categories: dev
giscus_comments: false
---
> 원래 [티스토리 블로그](https://randomhuman.tistory.com/2)에 쓴 글을 옮겨 왔습니다. 원문 카테고리: 공부/랜덤코딩

다음을 복사해서 쓰면 쉽게 코드 실행시간을 비교 할 수 있다.

```python
import time

start_time = time.time()
## Code Space Start ##

## Code Space End ##
end_time = time.time()
elapsed_time = end_time - start_time
hours, rem = divmod(elapsed_time, 3600)
minutes, seconds = divmod(rem, 60)
print(f"Time taken: {int(hours)}시 :{int(minutes)}분 :{seconds:.2f}초")
print("Elapsed : ", elapsed_time)
```

사용 예를 들자면,

모델 훈련 시, 훈련 데이터가 Number 데이터가 아니여셔, 파이토치에서 제공하는 Torch 형태로 저장할 수 없었다.

그렇기에 데이터를 GPU에 올려둘 수 없었으며

훈련 데이터에서 Random으로 Batch 데이터를 생성 할 때, Numpy를 사용했었다.

그러다 문뜩 실행 시간에 대한 의문이 들었다

- Numpy를 이용하여 Random index를 구하고, index를 통해 Batch에 사용할 데이터를 선정하는 시간

- Torch를 이용하여 GPU로 Random index를 구하고, Random index를 다시 cpu로 옮기고 numpy로 바꾼다음,  훈련 데이터에 index를 올려 데이터를 선정하는 시간

아무리 GPU가 빠르다고 해도, CPU로 옮기고 데이터 형변환 하는 시간이 더 걸릴 거라 생각했지만

측정해본 결과 아니였다.. ㅋㅋ

그래서 데이터 1만개를 랜덤으로 뽑아보았다.

1번 테스트 결과

```python
idx = np.random.randint(0, data_size , batch_size , dtype=int)
random_batch_data = train_data[idx]

# 출력 결과
Time taken: 0시 :0분 :0.00초
Elapsed :  0.0019958019256591797
```

2번 테스트 결과

```python
idx = torch.randint(0, data_size, (batch_size,), dtype=torch.long).to(self.device)
random_batch_data= train_data[idx.cpu().numpy()]

# 출력 결과
Time taken: 0시 :0분 :0.00초
Elapsed :  0.003989458084106445
```

여러번 해봤는데, 데이터가 적을 때는 별차이 없고, 데이터가 클때는 그냥 CPU로 처리하는 게 더 빠르다.

아무래도 GPU에서 CPU로 옮기는 데 시간이 많이 걸리는 것 같다.

단, 이 경우는 훈련 데이터가 Numpy 배열로 저장되어 있기에 그런거지..

훈련 데이터를 텐서로 저장할 수 있으면 다른 결과가 나올 것 같다.
