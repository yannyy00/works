# Project Name

 Add short description of project here > 
 This project trains an model using ~1100 images of the species Viriginia Creeper and ~2100 images of the species Poison Ivy. When run with the image of either species, the model accurately determines the species at a 99% success rate.

## The Algorithm

The reliability of the model is determeined by the number of images within its train & val folders as well as the number of epochs ran while training the model. Add an explanation of the algorithm and how it works. Make sure to include details about how the code works, what it depends on, and any other relevant info. Add images or other descriptions for your project here. 

## Running this project

# Training
1. To begin setting up and training model, enter your computer's Docker container.
    ./docker/run.sh

2. Cd into your classification folder. If your machine contain these folders, create them then run the command
     cd python/training/classification

3. Run the training script (Recommended epochs is 120)
     python3 train.py --epochs=120 --model-dir=models/works_m data/works_d
   The training will take approximately 40 minutes.

4. Once completed, export the training to a file. The model should appear under jetson-inference/python/training/classification/models as "works_m"
     python3 onnx_export.py --model-dir=models/works_m

# Running
5. Exit the docker if needed. You should return to ~/jetson-inferference
     exit

6. Set the NET and DATASET variables
    NET=models/works_m
    DATASET=data/works_d

7. Run the model with a test image
   imagenet.py --model=$NET/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=$DATASET/labels.txt $DATASET/test/cat/01.jpg cat.jpg
   
   imagenet.py --model=$NET/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=$DATASET/labels.txt $DATASET/test/cat/*test image name*.jpg *output file name*.jpg

   The terminal will report the result of the run, and a viewable output image should appear in jetson-inference/python/training/classification/




[View a video explanation here](video link)er
