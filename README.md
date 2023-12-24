# nnUnetForOTSCC
This is the nnUnet v1 model for oral tongue squamous cell carcinoma.

According to GPL v3, if someone use our models to train new tongue and tongue tomor segementation models, we encourage them uploading and sharing their newly trained models for others to download.

We trained four segmentation models for whole tongue and tongue cancer with T1c and T2WI using nnUnet v1(https://github.com/MIC-DKFZ/nnUNet/tree/nnunetv1).

Note: We will upload the model to the repository as soon as possible after the publication of the paper.

# Usage
## Preparing the environment
1. Install nnU-Net accoding to nnUnet official document(https://github.com/MIC-DKFZ/nnUNet/tree/nnunetv1)
2. Put the folders in this repo to the nnUnet DATASET folder: `xx/nnUnetFrame/DATASET/nnUNet_trained_models`
3. Preprocess your onw data. Prepare datasets to DATASET/nnUNet_raw according to the instructions

## Data inference
We traing 2d and 3d_fullres for each models, once all models are trained, we use the official command to automatically determine what U-Net configuration(s) to use for test set prediction, so we identified the best U-Net configuration below: 
### Task01(tongue t1c)
```shell
Here is how you should predict test cases. Run in sequential order and replace all input and output folder names with your personalized ones

nnUNet_predict -i FOLDER_WITH_TEST_CASES -o OUTPUT_FOLDER_MODEL1 -tr nnUNetTrainerV2 -ctr nnUNetTrainerV2CascadeFullRes -m 2d -p nnUNetPlansv2.1 -t Task001_Shet1c -z
nnUNet_predict -i FOLDER_WITH_TEST_CASES -o OUTPUT_FOLDER_MODEL2 -tr nnUNetTrainerV2 -ctr nnUNetTrainerV2CascadeFullRes -m 3d_fullres -p nnUNetPlansv2.1 -t Task001_Shet1c -z
nnUNet_ensemble -f OUTPUT_FOLDER_MODEL1 OUTPUT_FOLDER_MODEL2 -o OUTPUT_FOLDER -pp /data/nnUnetFrame/DATASET/nnUNet_trained_models/nnUNet/ensembles/Task001_Shet1c/ensemble_2d__nnUNetTrainerV2__nnUNetPlansv2.1--3d_fullres__nnUNetTrainerV2__nnUNetPlansv2.1/postprocessing.json
```
### Task07_She(tongue t2)
```shell
Here is how you should predict test cases. Run in sequential order and replace all input and output folder names with your personalized ones

nnUNet_predict -i FOLDER_WITH_TEST_CASES -o OUTPUT_FOLDER_MODEL1 -tr nnUNetTrainerV2 -ctr nnUNetTrainerV2CascadeFullRes -m 2d -p nnUNetPlansv2.1 -t Task007_She -z
nnUNet_predict -i FOLDER_WITH_TEST_CASES -o OUTPUT_FOLDER_MODEL2 -tr nnUNetTrainerV2 -ctr nnUNetTrainerV2CascadeFullRes -m 3d_fullres -p nnUNetPlansv2.1 -t Task007_She -z
nnUNet_ensemble -f OUTPUT_FOLDER_MODEL1 OUTPUT_FOLDER_MODEL2 -o OUTPUT_FOLDER -pp /data/nnUnetFrame/DATASET/nnUNet_trained_models/nnUNet/ensembles/Task007_She/ensemble_2d__nnUNetTrainerV2__nnUNetPlansv2.1--3d_fullres__nnUNetTrainerV2__nnUNetPlansv2.1/postprocessing.json
```

### Task003_SheTumorT1C(tongue OTSCC t1c)
```shell
Here is how you should predict test cases. Run in sequential order and replace all input and output folder names with your personalized ones

nnUNet_predict -i FOLDER_WITH_TEST_CASES -o OUTPUT_FOLDER_MODEL1 -tr nnUNetTrainerV2 -ctr nnUNetTrainerV2CascadeFullRes -m 2d -p nnUNetPlansv2.1 -t Task003_SheTumorT1C -z
nnUNet_predict -i FOLDER_WITH_TEST_CASES -o OUTPUT_FOLDER_MODEL2 -tr nnUNetTrainerV2 -ctr nnUNetTrainerV2CascadeFullRes -m 3d_fullres -p nnUNetPlansv2.1 -t Task003_SheTumorT1C -z
nnUNet_ensemble -f OUTPUT_FOLDER_MODEL1 OUTPUT_FOLDER_MODEL2 -o OUTPUT_FOLDER -pp /data/nnUnetFrame/DATASET/nnUNet_trained_models/nnUNet/ensembles/Task003_SheTumorT1C/ensemble_2d__nnUNetTrainerV2__nnUNetPlansv2.1--3d_fullres__nnUNetTrainerV2__nnUNetPlansv2.1/postprocessing.json
```

### Task002_SheTumorT2(tongue OTSCC t2)
```shell
Here is how you should predict test cases. Run in sequential order and replace all input and output folder names with your personalized ones

nnUNet_predict -i FOLDER_WITH_TEST_CASES -o OUTPUT_FOLDER_MODEL1 -tr nnUNetTrainerV2 -ctr nnUNetTrainerV2CascadeFullRes -m 2d -p nnUNetPlansv2.1 -t Task002_SheTumorT2 -z
nnUNet_predict -i FOLDER_WITH_TEST_CASES -o OUTPUT_FOLDER_MODEL2 -tr nnUNetTrainerV2 -ctr nnUNetTrainerV2CascadeFullRes -m 3d_fullres -p nnUNetPlansv2.1 -t Task002_SheTumorT2 -z
nnUNet_ensemble -f OUTPUT_FOLDER_MODEL1 OUTPUT_FOLDER_MODEL2 -o OUTPUT_FOLDER -pp /data/nnUnetFrame/DATASET/nnUNet_trained_models/nnUNet/ensembles/Task002_SheTumorT2/ensemble_2d__nnUNetTrainerV2__nnUNetPlansv2.1--3d_fullres__nnUNetTrainerV2__nnUNetPlansv2.1/postprocessing.json
```


