<h1>FaceMask_detection</h1>

A face mask detector using a neural network trained on a dataset of 1500 images with and without masks. Here are a few process steps of implementation:

<h5>Dataset Size:</h5> 1500 images is a relatively small dataset, especially when training deep learning models. Consider acquiring more diverse images to improve the model's generalization to different scenarios.

<h5>Augmentation:</h5> Augmentation is a good practice for increasing dataset size and improving model robustness. Ensure that the augmentation techniques you applied are appropriate for your task and do not introduce unrealistic variations.

<h5>Model Architecture:</h5>> Using SSD_MobileNet_V1 is a good choice for real-time object detection tasks due to its balance between speed and accuracy. However, I have experimented with other architectures or fine-tuned the existing one to see if you can achieve better performance.

<h5>Training Duration and Epochs:</h5> Training for 20,000 epochs seems quite high and might lead to overfitting, especially with a smaller dataset. Monitor the model's performance on a validation set and consider using early stopping to prevent overfitting.

<h5>Validation Set:</h5> Ensuring that I have a separate validation set to monitor the model's performance during training. This helps in identifying overfitting and selecting the best model.

<h5>Hardware Acceleration:</h5> Using a Tesla GPU in Google Colab is beneficial for faster training. But sometimes I'm facing hardware limitations on my local system, so we also explore cloud-based solutions for inference if speed is crucial.

<h5>Fine-tuning:</h5> Depending on the specific use case, consider fine-tuning your model on a more domain-specific dataset. For example, if the deployment scenario involves specific lighting conditions or environments, fine-tuning a dataset that reflects these conditions can be beneficial.

<h5>Testing:</h5> Evaluate the model's performance on a diverse test set to ensure its generalization to different scenarios. Check for false positives and false negatives and iteratively improve the model based on the testing results.

<h5>Deployment:</h5> Deploying on a cloud-based environment with real-world scenarios. 

1. Set up your environment and install the required packages, briefly provided in the tfod_setup file.
 ![](Screenshots/cmd.JPG)

<h5>Note -- Follow tfod_setup instructions from the attached tfod_setup.txt file till Step-16 because Step-17 is training in the local system and you can perform the 
    below lines for faster training if you are working in Google Colab</h5>

2. I have trained in Google Colab so for that you have to mount your Google Drive in Google Colab and in Google Drive upload the file content of models
   
    Steps in Google Colab
   
     a. %tensorflow_version 1.x

     b. import os
     RESEARCH_DIR = "/content/drive/My Drive/PATH_TO_TFOD/tfod/models-1.13.0/research" #Provide your path

     c. os.chdir(RESEARCH_DIR)

     d. os.getcwd()

     e. This is training code in Python !python train.py --logtostderr --train_dir=training/ --pipeline_config_path=training/ssdlite_mobilenet_v1_coco.config

     f. Copy and paste following code in your browser console(To open console Press Ctrl+Shift+I and paste it) to prevent Google Colab from terminating- JS code1-
         
            function ClickConnect(){
            console.log("Working"); 
            document.querySelector("colab-toolbar-button").click() 
            }setInterval(ClickConnect,60000)
      
  ![](Screenshots/colabOutPut.png)
  ![](Screenshots/trainingStartedinColab.jpeg)
  
 3. After training is done in Colab, Checkpoint files are created in the "Training" folder in Models\Research\Training.Download and replace in your local system
    for generating a .pb file from ckpt file and then further testing. 
    
  ![](Screenshots/gdrive.jpg)
    
 4. Then you can proceed from Step-18 in the tfod_setup file and convert ckpt files into pb file and then run your object detection tutorial file and test images.
 
  ![](Screenshots/mask_test.png)
    
  ![](Screenshots/no_mask_test.png)
    
 5. In case you are not able to train in Google Colab, I have uploaded the "inference graph" folder in my github repo, you need to follow from Step 19, because till 
    Step 18 completed and results are stored in inference graph folder. Just u need to download the inference graph folder and paste it into the models\research folder 
    and then you can test it.   
  
  
 
