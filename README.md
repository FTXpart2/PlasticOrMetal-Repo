# PlasticOrMetal

Welcome! This is a project created using the processing power of a Jetson Nano. It is designed to tackle the environmental issue of sorting between plastic and metals as those 2 are usually mixed together. Once an image is registered the AI model will train it and design it to be able to detect the differences with a accuracy defined by its training. Below are the steps on how to run this.



# Steps 
1. Go to your terminal and run  `git clone https://github.com/FTXpart2/PlasticOrMetal-Repo.git`
 
2. Now go into the cloned directory, inside that directory `git clone https://github.com/dusty-nv/jetson-inference.git`

3. After you do that, go to jetson-inference and run `./docker/run.sh`

4. Inside docker you go to `cd python/training/classification
`
5. In the classification folder run `python3 train.py --model-dir=models/PlasticOrMetal data/PlasticOrMetal` (This will take a while)

6. Once you finish the training, you need to export to onnx doing `python3 onnx_export.py --model-dir=models/PlasticOrMetal`

7. When you are done, set your NET and DATASET variables using
   `NET=models/PlasticOrMetal
    DATASET=data/PlasticOrMetal`

8. After setting your variables you will be able to run! Run the following command below

   `imagenet.py --model=$NET/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=$DATASET/labels.txt $DATASET/test/<dataset>/.jpg .jpg`

   The dataset allows you to choose which one you want which in this case is either Metal or Plastic. Choose a JPG from that file to scan and the 2nd jpg choose which name you want to set it as the test image.

   
