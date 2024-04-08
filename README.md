# Assignment2_PartA
building and training the model for iNaturalist dataset
dl_assn2_parta consist of two files
1. dl_assn2_parta.ipynb
2. dl_assn2_parta.py

run dl_assn2_parta.py with the optinal arguments by using the wandb API key.

arguments are as follows

'-wp', '--wandb_project', type=str, default="Assignment2_PartA", help="wandb project name"

'-nF', '--num_filters', type=int, default=32, choices = [16,32, 64], help="number of filters"

'-sF', '--filter_size', type=int, default=3, choices = [3, 5, 7], help="filter size"

'-aF', '--activation_fun', type=str, default="mish", choices = ['relu','gelu','silu','mish'], help="activation function"

 '-fC', '--filter_config', type=str, default="same", choices = ['same','double','half'], help="filter configuration"
 
'-n', '--neurons', type=int, default=128, choices = [128, 256], help="dense layer neurons")

'-opt', '--optim_name', type=str, default="nadam", choices = ['sgd','adam','nadam'], help="optimizer for backprop"

'-bS', '--batchSize', type=int, default=32, choices = [32, 64], help="batch size"

'-d', '--dropOut', type=float, default=0.2, choices = [0.2, 0.3], help="dropout rate"

'-ag', '--data_aug', type=str, default="no", choices = ['yes', 'no'], help="data augmentation"

'-bN', '--batchnorm', type=str, default="no", choices = ['yes', 'no'], help="batch normalization"

'-nE', '--num_epochs', type=int, default=5, choices = [5, 10], help="number of epochs"

'-lR', '--learning_rate', type=float, default=1e-3, choices = [1e-3, 1e-4], help="learning rate"
   
    
    
This initiates a call to train_cnn() which will build the cnn model and train it as per the requirement, this will produce validation and test accuracy and logs it in wandb CS23M005/Assignment2_PartA.

Detailed description of the functions:
1. parse_args()
   
     This function takes the input from the command line arguments and call train_cnn() with required parameters.
   
     This function has default values in which case if user does not provide arguments
   
3. train_cnn()
   
     This is the major function which will get the data loader from get_data()
   
     defines an object model using ConvNet() for training
   
     trains the model for each epoch by doing forward and backward propagations (not explicit but comes with in)
   
     After training the model, it will calculate train accuracy/loss, validation accuracy/loss using check_accuracy()
   
5. ConvNet()
   
     This function will create a cnn with 5 convolutional hidden layer each followed by a maxpool and activation function
   
     This class has getWH() which will calculate the output W,H using input W,H

     This class has forward() which will do the layer connections appropriately

   
7. get_data()
   
     This function will generate the train_loader/validation_loader from the iNaturalist dataset with the required
   transformation (with and withou data augmentation)
   
8. check_accuracy()
    
     This function will do the plain forward propagation and calculate accuracy/loss w.r.t predictions vs targets
