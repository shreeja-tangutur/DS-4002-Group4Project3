# DS-4002-Group4Project3
UVA DS 4002 Group 4 - Project 3 (Image data)

## Software and Platform

Types of software used: Github, HOG Transfer model, kNN

Necessary add-on packages: pandas, cv2, numpy, matplotlib, sklearn, os module 

The platform: Windows/ Mac

## Map of Documentation
DS-4002-Group4Project3/
│
├── DATA/
│   ├── Data AppendixMI3P3.pdf
│   └── Nutrition Food Proj_Cleaned/
│       └── Nutrition Food Proj -B0-.folder (1)/
│           └── train/
│               ├── American-Cheese/
│               ├── Apple/
│               ├── Avocado/
│               ├── Banana/
│               └── ... [many food category folders]
│
├── OUTPUT/
│   ├── Food Category Counts.png
│   ├── hog_classification_metrics.png
│   ├── hog_classification_report.csv
│   ├── hog_confusion_matrix.csv
│   ├── hog_confusion_matrix.png
│   ├── hog_evaluation_summary.csv
│   └── Image Count per Folder.png
│
├── SCRIPTS/
│   ├── Exploratory Analysis.md
│   └── HOG_LR_Apporach.ipynb
├── LICENSE
└── README.md
```

## Instruction for Reproducing Results
Clone the GitHub repository and download the csv files containing the dataset. The data is already cleaned, so run the analysis scripts listed in SCRIPTS folder. The "Exploratory Analysis" produces the exploratory plots, the "HOG_LR_Apporach" does the transfer learning and histogram of oriented gradients, and the []. The results should match the ones in the OUTPUT folder. Our results reveal…

- The HOG appraoch produces an accuracy rate of 52%

- The kNN approach produces an accuracy rate of []

## References