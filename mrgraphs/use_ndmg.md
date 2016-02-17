### Using ndmg
Now that your data is all set and ready to use, let's put **ndmg** to work! Let's give our end-to-end pipeline a shot. We're going to assume that you are using our demo data and you've stored it in your home directory. Open a new terminal and type the following:

    python ndmg_pipeline.py ~/data/KKI2009_113_1_DTI.nii ~/data/KKI2009_113_1_DTI.bval ~/data/KKI2009_113_1_DTI.bvec ~/data/KKI2009_113_1_MPRAGE.nii ~/atlas/MNI152_T1_1mm.nii.gz ~/atlas/MNI152_T1_1mm_brain_mask.nii.gz ~/data/outputs ~/atlas/desikan.nii.gz


To break that down a bit, let's look at the arguments specifically:

    python ndmg_pipeline.py dti bval bvec mprage atlas mask outdir [labels [labels ...]]


Let's chat about the things that might look a little funny here. `mask` is a binary mask (i.e. black and white) image of the brain in the atlas you're using. `outdir` is the base directory where you want your output files to be stored - don't worry, **ndmg** will handle the naming and organization within. Lastly, notice that `[labels [labels ...]]` block at the end? That means that **ndmg** allows you to make connectomes on multiple scales and parcellation schemes at once, you just need to pass in all of the sets of labels you'd like to use!

### Waiting for your results
The **ndmg** end-to-end pipeline takes about 30 minutes to run on my computer (a pretty basic Macbook), and feeds you output statements along the way.

### Diving deeper
Sure, the above gave you a taste of what the **ndmg** package can do, but what if you want a bit more of an intimiate knowledge of the inner workings of that pipeline we just showed? Well, you're in luck! Check out this [Jupyter Notebook](./examples/inside_run_ndmg.ipynb) that walks you through what the pipeline you just ran is doing.

