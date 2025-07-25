# Poison Ivy/Virginia Creeper Identification

 This project trains an model using ~1100 images of the species Viriginia Creeper and ~2100 images of the species Poison Ivy. When run with the image of either species, the model accurately determines the species at a 99% success rate.

## The Algorithm

The reliability of the model is determeined by the number of images within its train & val folders as well as the number of epochs ran while training the model. Add an explanation of the algorithm and how it works. Make sure to include details about how the code works, what it depends on, and any other relevant info. Add images or other descriptions for your project here. 

## Running this project

# Downloading images

1. Navigate to your data folder

     cd jetson-inference/python/training/classification/data
   
3. Download the zip file of the images with the command below

     wget -O work.zip --content-disposition -L --max-redirect=20 "https://www.dropbox.com/scl/fi/5neoaazgn53iuhgne5uk7/project.zip?rlkey=xkxn8kzzfmvpygiaybjn84yz9&st=diqvay9o&dl=1"

5. Extract the files from the zip

     unzip work.zip


# Training

1. Navigate into the jetson-inference folder

     cd ~/jetson-inference
   
3. To begin setting up and training model, enter your computer's Docker container.

     ./docker/run.sh

5. Cd into your classification folder. If your machine contain these folders, create them then run the command

     cd python/training/classification

7. Run the training script (Recommended epochs is 120)

     python3 train.py --epochs=120 --model-dir=models/a_project data/project
   
   *The training will take approximately 40 minutes.

9. Once completed, export the training to a file. The model should appear under jetson-inference/python/training/classification/models as "works_m"
     python3 onnx_export.py --model-dir=models/a_project

# Running
1. Exit the docker if needed. You should return to ~/jetson-inferference

     exit

3. Navigate back to nvidia@nvidia

     cd~

5. Cd into jetson-inference/python/training/classification.

     cd jetson-inference/python/training/classification
   
7. Set the NET and DATASET variables

     NET=models/a_project
     DATASET=data/project

9. Run the model with a test image

     imagenet.py --model=$NET/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=$DATASET/MyLabels.txt $DATASET/test/Creeper/Ctest8.jpg output.jpg

      OR

     imagenet.py --model=$NET/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=$DATASET/MyLabels.txt $DATASET/test/*test image name*.jpg *output file name*.jpg

   The terminal will report the result of the run, and a viewable output image should appear in jetson-inference/python/training/classification/




[View a video explanation here](https://youtu.be/F080bepTbSA)
