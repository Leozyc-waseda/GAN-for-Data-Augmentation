
# CycleGAN and CUTGAN for Data Augmentation

#  1 开始基础配置

- clone CycleGAN的repo
```sh
$ git clone https://github.com/junyanz/pytorch-CycleGAN-and-pix2pix
cd pytorch-CycleGAN-and-pix2pix
#配置好运行CycleGAN必须的环境变量，在requeirements.txt文件里
#强烈推荐用anaconda建一个新的环境
$ pip install -r requirements.txt
```
#  2 数据集准备，训练你自己的数据集
- CycleGAN的目的是把Domain X的图片转成Domain Y的图片，并且同时可以把Domain Y的图片转成Domain X的图片。简单的说就是，【马→斑马】同时，【斑马→马】的转换是可以的.
- 为此你要准备一个文件夹比如我的```GAN_train_dataset```里面有```train A ：干净```，```train B：脏```.
![Image text](https://github.com/Leozyc-waseda/SoilingDataset/blob/master/github_images/%E6%88%AA%E5%B1%8F2020-07-12%20%E4%B8%8B%E5%8D%886.11.18.png)
- 同时里面还有测试的文件夹，用于测试模型```test A```，和```test B```.

#  3 训练，train your model
```sh
python train.py --dataroot ./GAN_train_dataset/soiling --name soiling_GAN --model cycle_gan
```
如果想要查看训练过程，和loss图标
```
#运行
python -m visdom.server
#再点击
http://localhost:8097
```
#  4 测试，test your model
```sh
python test.py --dataroot ./GAN_train_dataset/soiling --name maps_cyclegan --model cycle_gan
#测试结果可以在文件夹中index.html以网页的形式查看

```

