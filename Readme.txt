Due to the size of our trained model and code base we are unable to upload it into github.
To recreate the results from our project using StyleGANv2 please download the source code and saved models from the following link:
https://drive.google.com/file/d/1v_-OMnrMtTsqv2Vd0pf8NOrOz7GgLytB/view?usp=sharing

To use this code please place it on the Carya cluster or a local machine with roughly 32Gb of VRAM.
A conda environment will need to be made first, we provide the "environment.yml" file that can be used with conda to recreate the conda environment.

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



To 

