# !python train.py --img 460 --batch 40 --epochs 10 --data /content/drive/MyDrive/Rose/Dataset/Dataset/data.yaml --cfg ./models/yolov5s.yaml --weights yolov5s.pt --name result

train: weights=yolov5s.pt, cfg=./models/yolov5s.yaml, data=/content/drive/MyDrive/Rose/Dataset/Dataset/data.yaml, hyp=data/hyps/hyp.scratch-low.yaml, epochs=10, batch_size=40, imgsz=460, rect=False, resume=False, nosave=False, noval=False, noautoanchor=False, noplots=False, evolve=None, bucket=, cache=None, image_weights=False, device=, multi_scale=False, single_cls=False, optimizer=SGD, sync_bn=False, workers=8, project=runs/train, name=result, exist_ok=False, quad=False, cos_lr=False, label_smoothing=0.0, patience=100, freeze=[0], save_period=-1, seed=0, local_rank=-1, entity=None, upload_dataset=False, bbox_interval=-1, artifact_alias=latest
github: up to date with https://github.com/ultralytics/yolov5 ✅
requirements: /content/drive/MyDrive/Rose/requirements.txt not found, check failed.
YOLOv5 🚀 v7.0-162-gc3e4e94 Python-3.10.11 torch-2.0.0+cu118 CPU

hyperparameters: lr0=0.01, lrf=0.01, momentum=0.937, weight_decay=0.0005, warmup_epochs=3.0, warmup_momentum=0.8, warmup_bias_lr=0.1, box=0.05, cls=0.5, cls_pw=1.0, obj=1.0, obj_pw=1.0, iou_t=0.2, anchor_t=4.0, fl_gamma=0.0, hsv_h=0.015, hsv_s=0.7, hsv_v=0.4, degrees=0.0, translate=0.1, scale=0.5, shear=0.0, perspective=0.0, flipud=0.0, fliplr=0.5, mosaic=1.0, mixup=0.0, copy_paste=0.0
ClearML: run 'pip install clearml' to automatically track, visualize and remotely train YOLOv5 🚀 in ClearML
Comet: run 'pip install comet_ml' to automatically track and visualize YOLOv5 🚀 runs in Comet
TensorBoard: Start with 'tensorboard --logdir runs/train', view at http://localhost:6006/
Overriding model.yaml nc=80 with nc=8

                 from  n    params  module                                  arguments                     
  0                -1  1      3520  models.common.Conv                      [3, 32, 6, 2, 2]              
  1                -1  1     18560  models.common.Conv                      [32, 64, 3, 2]                
  2                -1  1     18816  models.common.C3                        [64, 64, 1]                   
  3                -1  1     73984  models.common.Conv                      [64, 128, 3, 2]               
  4                -1  2    115712  models.common.C3                        [128, 128, 2]                 
  5                -1  1    295424  models.common.Conv                      [128, 256, 3, 2]              
  6                -1  3    625152  models.common.C3                        [256, 256, 3]                 
  7                -1  1   1180672  models.common.Conv                      [256, 512, 3, 2]              
  8                -1  1   1182720  models.common.C3                        [512, 512, 1]                 
  9                -1  1    656896  models.common.SPPF                      [512, 512, 5]                 
 10                -1  1    131584  models.common.Conv                      [512, 256, 1, 1]              
 11                -1  1         0  torch.nn.modules.upsampling.Upsample    [None, 2, 'nearest']          
 12           [-1, 6]  1         0  models.common.Concat                    [1]                           
 13                -1  1    361984  models.common.C3                        [512, 256, 1, False]          
 14                -1  1     33024  models.common.Conv                      [256, 128, 1, 1]              
 15                -1  1         0  torch.nn.modules.upsampling.Upsample    [None, 2, 'nearest']          
 16           [-1, 4]  1         0  models.common.Concat                    [1]                           
 17                -1  1     90880  models.common.C3                        [256, 128, 1, False]          
 18                -1  1    147712  models.common.Conv                      [128, 128, 3, 2]              
 19          [-1, 14]  1         0  models.common.Concat                    [1]                           
 20                -1  1    296448  models.common.C3                        [256, 256, 1, False]          
 21                -1  1    590336  models.common.Conv                      [256, 256, 3, 2]              
 22          [-1, 10]  1         0  models.common.Concat                    [1]                           
 23                -1  1   1182720  models.common.C3                        [512, 512, 1, False]          
 24      [17, 20, 23]  1     35061  models.yolo.Detect                      [8, [[10, 13, 16, 30, 33, 23], [30, 61, 62, 45, 59, 119], [116, 90, 156, 198, 373, 326]], [128, 256, 512]]
YOLOv5s summary: 214 layers, 7041205 parameters, 7041205 gradients, 16.0 GFLOPs

Transferred 342/349 items from yolov5s.pt
WARNING ⚠️ --img-size 460 must be multiple of max stride 32, updating to 480
optimizer: SGD(lr=0.01) with parameter groups 57 weight(decay=0.0), 60 weight(decay=0.000625), 60 bias
albumentations: Blur(p=0.01, blur_limit=(3, 7)), MedianBlur(p=0.01, blur_limit=(3, 7)), ToGray(p=0.01), CLAHE(p=0.01, clip_limit=(1, 4.0), tile_grid_size=(8, 8))
train: Scanning /content/drive/MyDrive/Rose/Dataset/Dataset/train/labels/─▄├╩... 567 images, 81 backgrounds, 0 corrupt: 100% 648/648 [00:07<00:00, 87.67it/s]
train: New cache created: /content/drive/MyDrive/Rose/Dataset/Dataset/train/labels/─▄├╩.cache
val: Scanning /content/drive/MyDrive/Rose/Dataset/Dataset/valid/labels/─▄├╩... 121 images, 11 backgrounds, 0 corrupt: 100% 132/132 [00:01<00:00, 71.61it/s]
val: New cache created: /content/drive/MyDrive/Rose/Dataset/Dataset/valid/labels/─▄├╩.cache

AutoAnchor: 3.31 anchors/target, 1.000 Best Possible Recall (BPR). Current anchors are a good fit to dataset ✅
Plotting labels to runs/train/result/labels.jpg... 
Image sizes 480 train, 480 val
Using 2 dataloader workers
Logging results to runs/train/result
Starting training for 10 epochs...

      Epoch    GPU_mem   box_loss   obj_loss   cls_loss  Instances       Size
        0/9         0G     0.1116    0.01821    0.06235         69        480:   0% 0/17 [02:29<?, ?it/s]WARNING ⚠️ TensorBoard graph visualization failure Sizes of tensors must match except in dimension 1. Expected size 30 but got size 29 for tensor number 1 in the list.
        0/9         0G     0.1071    0.02038     0.0638         22        480: 100% 17/17 [14:27<00:00, 51.04s/it]
                 Class     Images  Instances          P          R      mAP50   mAP50-95: 100% 2/2 [01:13<00:00, 36.99s/it]
                   all        132        121    0.00301      0.766     0.0168    0.00394

      Epoch    GPU_mem   box_loss   obj_loss   cls_loss  Instances       Size
        1/9         0G    0.07277    0.02185    0.05991         17        480: 100% 17/17 [12:11<00:00, 43.03s/it]
                 Class     Images  Instances          P          R      mAP50   mAP50-95: 100% 2/2 [01:11<00:00, 35.87s/it]
                   all        132        121    0.00332      0.968     0.0412     0.0128

      Epoch    GPU_mem   box_loss   obj_loss   cls_loss  Instances       Size
        2/9         0G     0.0589    0.02051    0.05456         19        480: 100% 17/17 [12:12<00:00, 43.07s/it]
                 Class     Images  Instances          P          R      mAP50   mAP50-95: 100% 2/2 [01:09<00:00, 34.67s/it]
                   all        132        121      0.109       0.35      0.146     0.0575

      Epoch    GPU_mem   box_loss   obj_loss   cls_loss  Instances       Size
        3/9         0G    0.05018    0.01752    0.05136         15        480: 100% 17/17 [12:12<00:00, 43.11s/it]
                 Class     Images  Instances          P          R      mAP50   mAP50-95: 100% 2/2 [01:10<00:00, 35.19s/it]
                   all        132        121     0.0926      0.435       0.13     0.0684

      Epoch    GPU_mem   box_loss   obj_loss   cls_loss  Instances       Size
        4/9         0G    0.04824    0.01559    0.04843         13        480: 100% 17/17 [12:16<00:00, 43.33s/it]
                 Class     Images  Instances          P          R      mAP50   mAP50-95: 100% 2/2 [01:06<00:00, 33.31s/it]
                   all        132        121      0.198       0.17      0.136     0.0557

      Epoch    GPU_mem   box_loss   obj_loss   cls_loss  Instances       Size
        5/9         0G    0.04233    0.01407    0.04515          8        480: 100% 17/17 [12:17<00:00, 43.41s/it]
                 Class     Images  Instances          P          R      mAP50   mAP50-95: 100% 2/2 [01:07<00:00, 33.74s/it]
                   all        132        121      0.191      0.394      0.245       0.12

      Epoch    GPU_mem   box_loss   obj_loss   cls_loss  Instances       Size
        6/9         0G    0.04433    0.01333    0.04395         11        480: 100% 17/17 [12:10<00:00, 42.99s/it]
                 Class     Images  Instances          P          R      mAP50   mAP50-95: 100% 2/2 [01:09<00:00, 34.68s/it]
                   all        132        121      0.157      0.496      0.245      0.135

      Epoch    GPU_mem   box_loss   obj_loss   cls_loss  Instances       Size
        7/9         0G    0.03818    0.01367    0.04417         22        480: 100% 17/17 [12:10<00:00, 42.96s/it]
                 Class     Images  Instances          P          R      mAP50   mAP50-95: 100% 2/2 [01:06<00:00, 33.48s/it]
                   all        132        121      0.172      0.604       0.33      0.216

      Epoch    GPU_mem   box_loss   obj_loss   cls_loss  Instances       Size
        8/9         0G    0.03349    0.01245     0.0418         14        480: 100% 17/17 [12:18<00:00, 43.46s/it]
                 Class     Images  Instances          P          R      mAP50   mAP50-95: 100% 2/2 [01:07<00:00, 33.72s/it]
                   all        132        121     0.0302       0.61      0.121     0.0532

      Epoch    GPU_mem   box_loss   obj_loss   cls_loss  Instances       Size
        9/9         0G    0.03194     0.0127    0.04184         16        480: 100% 17/17 [12:21<00:00, 43.63s/it]
                 Class     Images  Instances          P          R      mAP50   mAP50-95: 100% 2/2 [01:07<00:00, 33.51s/it]
                   all        132        121     0.0317      0.929      0.204      0.107

10 epochs completed in 2.272 hours.
Optimizer stripped from runs/train/result/weights/last.pt, 14.4MB
Optimizer stripped from runs/train/result/weights/best.pt, 14.4MB

Validating runs/train/result/weights/best.pt...
Fusing layers... 
YOLOv5s summary: 157 layers, 7031701 parameters, 0 gradients, 15.8 GFLOPs
                 Class     Images  Instances          P          R      mAP50   mAP50-95: 100% 2/2 [00:54<00:00, 27.40s/it]
                   all        132        121      0.173      0.616      0.331      0.217
               꼬깔콘고소한맛        132         22      0.107      0.273       0.16      0.104
               농심매운새우깡        132         22      0.122      0.409      0.124     0.0774
                    콘초        132         22      0.152      0.545      0.312      0.242
                농심바나나킥        132         22      0.343      0.909      0.438      0.282
               포카칩오리지널        132         11      0.172      0.727      0.349      0.233
        도도한나쵸미니미크림어니언맛        132         11     0.0866      0.448      0.108     0.0483
                 허니버터칩        132         11      0.225          1      0.824      0.533
Results saved to runs/train/result