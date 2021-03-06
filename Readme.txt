The files for the following can be found at https://github.com/sunitavillarreal/CVProject

1. To download images using Selenium, access the 'webscraping.ipynb' file, and change the download file location to a local folder on your computer. Also, edit the list of queries with keywords of your interest. 

2. To download images using the Twitter API, access the 'twitter_image_scraping_file.ipynb' file, change the first four access keys to your own. Also, edit the list of keywords of interest under 'hashtags.'

The original dataset can be found here: https://drive.google.com/file/d/1yQm8JcHxtMbHI4FMNoqGlXbOyLYaukvJ/view?usp=sharing
The synthetic image dataset can be found here: https://drive.google.com/file/d/1pTEtFS6wNaNqBDkkeRMJkOGyDTgHMEfQ/view?usp=sharing

Due to the size of our trained model and code base we are unable to upload it into github.
To recreate the results from our project using StyleGANv2 please download the source code and saved models from the following link:
https://drive.google.com/file/d/1v_-OMnrMtTsqv2Vd0pf8NOrOz7GgLytB/view?usp=sharing

To use this code please place it on the Carya cluster or a local machine with roughly 32Gb of VRAM.
A conda environment will need to be made first, we provide the "environment.yml" file in the provided download link that can be used with conda to recreate the conda environment.

To generate the images from a our provided pretrained model 
    Edit the "job.immigration_generate.bash.slurm" file:
        Edit the email line with your email to receive a notification for when the job starts and finishes
        Edit line 15 "conda activate /project/hoskere/Subin/stylegan2-ada-pytorch-main_edited/envs" to the path your conda environment is installed
    create a job on the cluster using "job.immigration_generate.bash.slurm" file
        run the following on the cluster terminal to do so "sbatch job.immigration_generate.bash.slurm"
    Generated images will be placed in the "out" folder

To train StyleGANv2 from scratch using the immigration dataset
    Edit the "job.image_generate.bash.slurm" file:
        Edit the email line with your email to receive a notification for when the job starts and finishes
        Edit line 15 "conda activate /project/hoskere/Subin/stylegan2-ada-pytorch-main_edited/envs" to the path your conda environment is installed
    create a job on the cluster using the "job.image_generate.bash.slurm"
        run the following on the cluster terminal to do so "sbatch job.image_generate.bash.slurm"



The SV human detection folder we provide contains two notebooks 
    "Person detector.ipynb" can be used to train a classifier to detect for humans using the crowdhuman and pass dataset
    "Filter Images.ipynb" can be used to filter images for humans using a selected trained model
    We provide a link to a trained model for human detection here:https://drive.google.com/file/d/1dOhx13jXWEq0S2Q0_D5AcRP_wwDe6kcJ/view?usp=sharing
    This is a trained resnext101_32x8d model with additional Linear layers, the provided notebooks are able to utilize this model
    Link to the Pass dataset can be found here:https://www.robots.ox.ac.uk/~vgg/data/pass/
    Link to the crowdhuman dataset can be found here:https://www.crowdhuman.org/
    
#######################################################################################
remove_duplicate_image.ipynb  
This notebook is to detect and remove the duplicate images in the dataset. The way to use it is:
# dir_path: the fold path of the dataset
# remove_duplicate: the function to detect and remove the duplicated images

dir_path = ???./duplicatedimages_foldpath???
remove_duplicate(dir_path)

#################################################################################################
OneclassSVM.ipynb
This notebook is the whole code including feature extract, dimention reduction and one-class-svm. 
If you want to do other dataset, only need to change the directory of the dataset in the load dataset section, then run the whole cell.

#################################################################################################
CNN_binary_classifier.ipynb
This notebook implement CNN binary classifier with pre-trained ResNet50. The best model is saved as save_fine_tune_model.h5, this file is too large to upload, the google drive link: https://drive.google.com/file/d/1NHU0FfQYQNBSbMT8G9EmQhfLJ9LnJaEb/view?usp=sharing 

The way to use this model is down below:
# Load test images
test_datagen = ImageDataGenerator(
    data_format='channels_last')
test_generator = test_datagen.flow_from_directory(
    "/content/images_notation_train_test/test",
    target_size=(IMAGE_SIZE, IMAGE_SIZE),
    batch_size=batch_size,
    class_mode='binary'
    )
model = load_model('/content/save_fine_tune_model.h5')
predict_generator(test_generator, model) 


