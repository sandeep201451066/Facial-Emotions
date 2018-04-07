
# Facial expression recognition using CNN in Tensorflow

The package uses a convolutional neural network to classify images from files or from video/camera1 stream.

The faces are first detected using opencv, then we extract the face landmarks using dlib, and we input the raw image data with the face landmarks into a 4 layered convolutional neural network.

Better to use anaconda environemnt to easily install the dependencies (especially opencv and dlib)


# Dependencies

- Tensorflow
- Tflearn
- Numpy
- Argparse
- [optional] Hyperopt + pymongo + networkx
- [optional] dlib, imutils, opencv 3


# HOW TO USE?

### Train the model
1. Choose your parameters in 'parameters.py'

2. Launch training:

```
python train.py --train=yes
```

3. Train and evaluate:

```
python train.py --train=yes --evaluate=yes
```

N.B: make sure the parameter "save_model" (in parameters.py) is set to True if you want to train and evaluate


### Optimize training hyperparameters
1. For this section, you'll need to install first these optional dependencies:
```
pip install hyperopt, pymongo, networkx
```

2. Lunch the hyperparamets search:
```
python optimize_hyperparams.py --max_evals=20
```

3. You should then retrain your model with the best parameters

N.B: the accuracies displayed is for validation_set (not test_set)

### Evaluate model (calculating test accuracy)

1. Modify 'parameters.py':
 
Set "save_model_path" parameter to the path of your pretrained file

2. Launch evaluation on test_set:

```
python train.py --evaluate=yes
```

### Recognizing facial expressions from an image file

1. For this section you will need to install `dlib` and `opencv 3` dependencies

2. Modify 'parameters.py':

Set "save_model_path" parameter to the path of your pretrained file

3. Predict emotions from a file

```
python predict.py --image path/to/image.jpg
```

### Facial Emotions Recognization in real time from images and videos

1. For this section you will need to install `dlib`, `imutils` and `opencv 3` dependencies

2. Modify 'parameters.py':

Set "save_model_path" parameter to the path of your pretrained file

3. Predict emotions from a file

```
python predict-from-video.py
```


# Link to the dataset with extracted landmarks:

You can find the database link and the scripts to extract the landmark explained in this repository:

https://github.com/amineHorseman/facial-expression-recognition-svm



# Classification results:

#### Classification using 5 emotions

Inline-style: 
![alt text](https://github.com/amineHorseman/facial-expression-recognition-using-cnn/Classification_results_5_emotions.png "Test accuracy results")

The comparison with SVM was done using the results from this package:

https://github.com/amineHorseman/facial-expression-recognition-svm


#### Classification using 3 emotions

Quick experiments showed that the classification reached 73% after 10 epochs
