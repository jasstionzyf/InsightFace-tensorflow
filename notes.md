python create_tfrecord.py --dataset_dir=/data_hadoop_2/mlib_data/images/Asian-Celeb/ --num_shards=1 --validation_size=0.01 --tfrecord_filename=Asian-Celeb_1 --CUDA_VISIBLE_DEVICES=0 --maxNum_perClass=2000 --minNum_perClass=0 --tfrecord_dir=/data_hadoop_2/mlib_data/tfrecords/Asian-Celeb/


python create_tfrecord.py --dataset_dir=/data/vcgstarimage/image_vcg_vgg_no_margin/ --num_shards=1 --validation_size=0.01 --tfrecord_filename=image_vcg_vgg_no_margin_20190416 --CUDA_VISIBLE_DEVICES=0 --maxNum_perClass=2000 --minNum_perClass=0 --tfrecord_dir=/data_hadoop_2/mlib_data/tfrecords/persons_vgg_vcg_no_margin_20190416/

hdfs://172.16.241.100:9000/data/mlib_data/tfrecords/persons_vgg_vcg_no_margin_20190413_validation_00000-of-00001.tfrecord
hdfs://172.16.241.100:9000/data/mlib_data/tfrecords/persons_vgg_vcg_no_margin_20190413_train_00000-of-00001.tfrecord








insightface-tensorflow:

python evaluate.py --config_path=./configs/config_ms1m_100.yaml --model_path=/Volumes/v2/mlib_data/models/arcefaces/config_ms1m_100_334k/best-m-334000 --val_data=/Volumes/v2/mlib_data/models/arcefaces/faces_emore/lfw.bin

/Volumes/v2/mlib_data/models/arcefaces/config_ms1m_100_334k/best-m-334000



python generateTFRecord.py --mode=mxrec --image_size=112 --read_dir=/Volumes/v2/mlib_data/models/arcefaces/faces_emore --save_path=/Volumes/v2/tfrecords/MS1M-ArcFace/all.tfrecord


MS1M-ArcFace:
/Volumes/v2/mlib_data/models/arcefaces/faces_emore




nohup python generateTFRecord.py --mode=folders --image_size=112 --read_dir=/data/vcgstarimage/image1/ --save_path=/data_hadoop_2/mlib_data/tfrecords/Asian-Celeb/Asian-Celeb.tfrecord > Asian-Celeb.out &




python generateTFRecord.py 
--mode=folders
--image_size=112
--read_dir=$DIRECTORY_TO_THE_TRAINING_DATA$
--save_path=$DIRECTORY_TO_SAVE_TFRECORD_FILE$/xxx.tfrecord


CLASSPATH=$(${HADOOP_HDFS_HOME}/bin/hadoop classpath --glob) nohup python train_softmax.py --config_path=./configs/Asian-Celeb.yml > ./Asian-Celeb.out &

hdfs://172.16.241.100:9000/data/mlib_data/tfrecords/MS1M-ArcFace

/data_hadoop_2/mlib_data/tfrecords/MS1M-ArcFace



bin/hadoop fs -put /data_hadoop_2/mlib_data/tfrecords/MS1M-ArcFace/all.tfrecord hdfs://172.16.241.100:9000/data/mlib_data/tfrecords/MS1M-ArcFace/





关于arcface模型的训练， 我几个问题有点困惑：
1:  如果用arcface模型，比如基于



/data/scripts/InsightFace-tensorflow/output/20190410-175517/checkpoints/









基于vcg 的名人训练数据生成person verification 的测试集类似于lfw验证集
基于asin 训练集进行arcface模型的训练，然后用该模型对vcg的验证集进行验证， 看看准确率
，如果准确率足够好，那么名人识别的流程如下：将位置的头像提取特征然后基于已知的名人特征集合进行搜索， 返回最相似的名人特征， 
计算他们之间的距离， 如果小于某个阀值，则认为此头像属于这个名人


