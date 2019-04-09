# Overview

Tensorflow model trained to detect objects in path for IEEE Southeast Conference

# Usage
# Retraining

Add a folder with images to be trained to the classifier folder inside tf-files, and run the following command in the terminal/cmd
IMAGE_SIZE=224
ARCHITECTURE="mobilenet_0.50_${IMAGE_SIZE}"
python -m scripts.retrain \
  --bottleneck_dir=tf_files/bottlenecks \
  --how_many_training_steps=500 \
  --model_dir=tf_files/models/ \
  --summaries_dir=tf_files/training_summaries/"${ARCHITECTURE}" \
  --output_graph=tf_files/retrained_graph.pb \
  --output_labels=tf_files/retrained_labels.txt \
  --architecture="${ARCHITECTURE}" \
  --image_dir=tf_files/classifier
  
  # Increase training steps for more accuracy
  
  USE THIS IF TIME PERMITS, ACCURACY WILL INCREASE EXPONENTIALLY (not yet done)
  
  python -m scripts.retrain \
  --bottleneck_dir=tf_files/bottlenecks \
  --model_dir=tf_files/models/"${ARCHITECTURE}" \
  --summaries_dir=tf_files/training_summaries/"${ARCHITECTURE}" \
  --output_graph=tf_files/retrained_graph.pb \
  --output_labels=tf_files/retrained_labels.txt \
  --architecture="${ARCHITECTURE}" \
  --image_dir=tf_files/classifier
 
 # Testing Trained Classifier
 
 Add photos to the trained folder in tf-files and then run following command in terminal/cmd to see the accuracy of the model
 
 python -m scripts.label_image \
    --graph=tf_files/retrained_graph.pb  \
    --image=tf_files/trained/[name of image] 
 
 
  
  
