# FPN
-----------------

My Results on pascal_voc2012 with pretrained FPN_iter_370000.ckpt:
CUDA_VISIBLE_DEVICES=0 python ./faster_rcnn/test_net.py --gpu 0 --weights
output/FPN_end2end/voc_0712_trainval/FPN_iter_370000.ckpt
--imdb voc_2012_test --cfg ./experiments/cfgs/FPN_end2end.yml --network
FPN_test

AP for aeroplane = 0.9307
AP for bicycle = 0.2078
AP for bird = 0.7622
AP for boat = 0.6472
AP for bottle = 0.3007
AP for bus = 0.8024
AP for car = 0.1888
AP for cat = 0.9164
AP for chair = 0.1178
AP for cow = 0.9082
AP for diningtable = 0.2955
AP for dog = 0.7173
AP for horse = 0.1252
AP for motorbike = 0.2300
AP for person = 0.6727
AP for pottedplant = 0.3492
AP for sheep = 0.8675
AP for sofa = 0.5945
AP for train = 0.9128
AP for tvmonitor = 0.2478
Mean AP = 0.5397

compared to declared mAP=0.7832 over pascal_voc0712.

alt_opt training:

nohup ./experiments/scripts/FPN_alt_opt.sh 0 FPN_alt_opt pascal_voc0712
--set RNG_SEED 42 TRAIN.SCALES "[800]" > FPN_alt_opt.log 2>&1 &



end2end training:

nohup ./experiments/scripts/FPN_end2end.sh 1 FPN pascal_voc0712 --set
RNG_SEED 42 TRAIN.SCALES "[800]" > FPN.log 2>&1 &

tail -f FPN.log


------------------------

TODO:
1. imporve end2end training result
2. check roi_pooling used interpolation or not
3. fix bugs in alt_opt training
