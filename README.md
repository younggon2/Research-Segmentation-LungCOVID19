# Research on lung segmentation for COVID19 patients in CXR
This source code is for sharing deep learning-based segmentation model in CXR. It has been validated for COVID19 patients as well.

# Pre-requisities
* Python == 3.5
* Keras >= 2.0
* Tensorflow >= 1.11
* Scipy
* OpenCV
* [segmentation-models](https://github.com/qubvel/segmentation_models)
* [keras-retinanet](https://github.com/fizyr/keras-retinanet)


# Diagram
![Diagram](/img/Diagram.png)

A flowchart of the proposed algorithm for segmentation of zones of the lung in CXR of COVID-19 patient. Right (R) and left (L) lung masks are generated by an ensemble method based on the a majority voting from five lung masks predicted by models trained with different conditions. Then, left hilum and carina are detected and used to find a central point to split the whole lung into  upper and lower regions. Finally, right upper lung (RUL), right lower lung (RLL), low upper lung (LUL), and left lower lung (LLL) are obtained.

# Segmentation result comparison (Dice 0.95 for a public dataset)
![EnsembleResult](/img/EnsembleResult.png)

An example of advantages of the ensemble method for different quality of CXRs. The first to last row in each column shows an input CXR, an ground truth mask, an ensemble result, and five results predicted by the first to fifth model. (a) A clear CXR that shows none of severe noise from a portable device and obstacles like medical devices, (b) a lung mask of (a), (c) an ensemble mask from the first to the fifth masks (d)-(h). Dice coefficients of (c)-(h) are 0.955, 0.928, 0912, 0.948, 0.948, and 0.948, respectively. (i) An CXR showing severe blurry within both lung regions due to lung opacity, (j) a lung mask of (i), (k) an ensemble mask from the first to the fifth masks (l)-(p). Dice coefficients of (k)-(p) are 0.955, 0.928, 0912, 0.948, 0.948, and 0.948, respectively. (q) An CXR showing sever noise generated from a portable device, (r) a lung mask of (q), (s) an ensemble mask from the first to the fifth masks (t)-(x). Dice coefficients of (s)-(x) are 0.899, 0.783, 0.885, 0.883, 0.879, and 0.903, respectively.

# Detection result and segmentation for four regions (mAP: 0.69 for a private dataset)

![Detection](/img/DetectionResult.png)

An example of detection results for the left hilum colored at red and carina colored at green and, dividing segmented lung mask into upper and lower lungs, i.e., RUL, LUL, RLL, and LLL with a reference point colored at while. (a) detection results for the left hilum (confidence: 0.94) and the carina (0.98). (b) A center point of the detection box for the left hilum is used as the reference point to divide upper and lower lungs. (c) detection results for the left hilum (0.56) and carina (0.95). (d) A location down to approximately 2cm vertically from a center point of the detection box for the carina is used as the reference point to divide upper and lower lungs.

# Correlation of mean intensity for segmented lung with extent score
![CorrelationWithExtent](/img/CorrelationWithExtent.png)

Boxplots of mean intensities with extent scores (0-4) for four regions. (a) LUL, (b) RUL, (c) LLL, (d) RLL.

# Citation (arxiv)
If you find this study useful in your research, please consider citing this project.

```rb
@article{kim2020deep,
  title={Deep Learning-based Four-region Lung Segmentation in Chest Radiography for COVID-19 Diagnosis},
  author={Kim, Young-Gon and Kim, Kyungsang and Wu, Dufan and Ren, Hui and Tak, Won Young and Park, Soo Young and Lee, Yu Rim and Kang, Min Kyu and Park, Jung Gil and Kim, Byung Seok and others},
  journal={arXiv preprint arXiv:2009.12610},
  year={2020}
}
```
URL: https://arxiv.org/abs/2009.12610


# Reference (Github)

1. https://github.com/qubvel/segmentation_models
2. https://github.com/fizyr/keras-retinanet
