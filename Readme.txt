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

