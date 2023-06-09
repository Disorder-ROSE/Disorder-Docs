yolov5 링크: https://drive.google.com/drive/folders/1lYeQuv5x81tRhSttatl-xmQzwODMV1d8?usp=sharing
# 1. 데이터셋 Train, Validation, Test 7:2:1로 분류
한 과자당 이미지가 총 114개이기 때문에
Train=77+4(분류하고 남은거), Validation=22, Test=11 개로 각각 분류하였다.

그리고 이 데이터셋으로 yolo를 img 460, batchsize 40, yolov5s, epoch 10 로 돌렸는데 결과가 너무 좋지 않았다(3시간 소요).

여러개의 과자를 여러개로 인식을 못하거나, 아예 인식을 못하는 과자도 있었다.

# 2. 분류한 데이터셋으로 코드를 조금씩 변형하며 학습
img 480, batchsize 20, yolov5m 으로 변경하여 다시 돌렸더니 저번결과보단 좋아졌다(3시간 소요).

코드 변형 전보단 좋아졌으나, 여러개 있는 과자들이 인식이 안되었는데 여러개 인식하는 모습을 보임, 하지만 과자이름을 잘못 인식하는 경우가 있었다

그래서 데이터 증식 방법을 사용하여 이미지양을 늘리기로 하였다.

# 3. 데이터 증식 generator 
- shift range 상하좌우이동
- horizon flip 좌우반전/상하반전 (상하반전은 편의점 진열대에 뒤집혀 진열되어있을 가능성은 거의 없으므로 안하기로함)

shift range 로만 양을 늘렸을땐 이미지양이 2배가 되었는데,

두 방법 모두를 써 이미지 데이터셋 양을 늘리니 원래 원본이미지의 양x4배가 되었다.

이미지양이 많이 늘었기 때문에 yolo로 학습시키기 위해선 yolov5m->s로 다시 줄이면 될 것 같았다.

- shift range 이미지 추가 후 학습결과: 
![image](https://user-images.githubusercontent.com/101008357/236688329-c045854d-3619-4d43-9d7c-fef407483326.png)
터져서 batchsize 20 -> 10 으로 줄이고 다시 돌리기로 했다. 대신 더 오래 걸린다.

- horizon flip 이미지 추가 후 학습결과: 에러발생. 
![image](https://github.com/Disorder-ROSE/Disorder-Docs/assets/101008357/9b302ee5-00b1-409a-9b72-dc87ae942d6b)
데이터셋 문제(filp추가한 코드 문제)

구체적으로는 이미지쪽은 정상적으로 증가되었으나, 라벨링 코드를 잘못 짜서 다시 짜주었음.

아래의 결과들은 4번과정(이미지 Resize후 진행한 결과)

```python
!python train.py --img 480 --batch 10 --epochs 50 --data /content/drive/MyDrive/Rose/Dataset/data.yaml --cfg ./models/yolov5m.yaml --weights yolov5m.pt --name result7
```
![image](https://github.com/Disorder-ROSE/Disorder-Docs/assets/101008357/76e39fd2-24d3-4adf-80ea-7a341cd3ed1f)
```python
!python train.py --img 480 --batch 20 --epochs 60 --data /content/drive/MyDrive/Rose/Dataset/data.yaml --cfg ./models/yolov5m.yaml --weights yolov5m.pt --name result8
```
![image](https://github.com/Disorder-ROSE/Disorder-Docs/assets/101008357/aa2c3922-5276-4712-a0ec-753267b51e2e)
```python
!python train.py --img 480 --batch 10 --epochs 100 --data /content/drive/MyDrive/Rose/Dataset/data.yaml --cfg ./models/yolov5m.yaml --weights yolov5m.pt --name result9
```
![image](https://github.com/Disorder-ROSE/Disorder-Docs/assets/101008357/a78deeb6-e310-4e29-8130-03d8316951cf)
```python
!python train.py --img 480 --batch 10 --epochs 40 --data /content/drive/MyDrive/Rose/Dataset/data.yaml --cfg ./models/yolov5m.yaml --weights yolov5m.pt --name result10
```
![image](https://github.com/Disorder-ROSE/Disorder-Docs/assets/101008357/7d50df84-b096-4a97-a172-af98b91d15dd)

# 4. 이미지 Resize
이미지 크기를 640*640으로 줄여주었음.

이유: 용량문제, 다운속도

# 5. 이미지 shuffle
이미지 shift, reverse로도 성능이 나오지않아 이유를 생각해본 결과 

train, valid, test에 원천이미지를 순서대로 나눠 저장하여서

test에는 train에 없는 측면이미지로만 저장되어

정확하게 측정되지 않았을수도있다 판단되어

이미지를 shuffle하여 그 shuffle된 이미지에서 다시 shift, reverse하기로 함

![image](https://github.com/Disorder-ROSE/Disorder-Docs/assets/101008357/9725f549-39b1-4870-b609-e33cd238a801)
mAP50이 많이 오른것을 확인

# 6. 이미지 몇개 빼기
원본 데이터셋 이미지 114개에서 보편적으로 사람이 과자 사진을 찍을때 이렇게 안찍을것 같다고 느껴지는 이미지 24개를 뺐음

뺀 이미지: 측면 이미지, 여러 개의 과자가 있는 이미지
![image](https://github.com/Disorder-ROSE/Disorder-Docs/assets/101008357/14ea2dc2-ba58-4541-b55b-41f591bb1a0d)

![image](https://github.com/Disorder-ROSE/Disorder-Docs/assets/101008357/5ab16f2c-cddb-4f00-af0c-fe544f2f47f6)
하지만 mAP는 크게 달라지지 않았다




