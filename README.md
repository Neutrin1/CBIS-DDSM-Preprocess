# CBIS-DDSM-PREPROCESS
如果你想使用CBIS-DDSM数据集训练乳腺癌分类器或分割模型，本仓库可以帮助你从原始文件夹中轻松提取乳房X光照片和掩码。
替换好路径，直接运行各个文件即可。
各个文件已经于2025.5由本人亲自调试完成。

## 设置
1. 该数据集可以直接从[官方网站](https://wiki.cancerimagingarchive.net/pages/viewpage.action?pageId=22516629)下载。
2. 如果你想深入了解CBIS-DDSM数据集，可以查看这篇[论文](https://www.nature.com/articles/sdata2017177)。它描述了如何使用数据集以及数据集是如何构建的。

## 数量描述
尽管[论文](https://www.nature.com/articles/sdata2017177)指出CBIDS-DDSM有753个钙化病例和891个肿块病例，但很难确定这个数据集实际有多少图像。根据CSV文件中提供的元数据，CBIS-DDSM包含3103张乳房X光照片，其中465张具有多个异常。2458张(79.21%)乳房X光照片属于训练集，645张(20.79%)属于测试集。此外，还包含3568张裁剪的乳房X光照片和3568个掩码。

## 仓库函数的简要说明
### Mammograms_code.ipynb:
这个脚本包含一个函数，用于检索本地机器上所有乳房X光照片的路径，并在数据框中将每个图像路径与其病理学合并。随后将数据框保存为CSV文件。

### mask_code.ipynb:
这个脚本包含一个函数，用于检索本地机器上所有补丁的路径，然后在数据框中将每个掩码路径与其病理学合并。随后将此数据框保存为CSV文件。注意：掩码比乳房X光照片多，因为一些乳房X光照片有多个病变。

### convert_dicom.ipynb:
CBIS-DDSM提供的图像(乳房X光照片、掩码和异常裁剪)以DICOM格式保存。这个函数将DICOM中的16位乳房X光照片保存为重新缩放的16位PNG文件。

### Original_Split.ipynb:
这个脚本根据官方[论文](https://www.nature.com/articles/sdata2017177)提供的标准化分割创建测试和训练集。所有图像的路径存储在数据框中，并保存为CSV文件。


CBIS-DDSM-PREPROCESS
If you want to use the CBIS-DDSM dataset to train breast cancer classifiers or segmentation models, this repository can help you easily extract mammograms and masks from the original folders. Simply replace the paths and run each file directly. All files have been personally debugged and verified by me in May 2025.

Setup
The dataset can be downloaded directly from the official website.
If you want to learn more about the CBIS-DDSM dataset, you can check this paper. It describes how to use the dataset and how it was constructed.
Quantity Description
Although the paper states that CBIDS-DDSM has 753 calcification cases and 891 mass cases, it's difficult to determine exactly how many images are in this dataset. According to the metadata provided in the CSV files, CBIS-DDSM contains 3103 mammograms, of which 465 have multiple abnormalities. 2458 (79.21%) mammograms belong to the training set, and 645 (20.79%) belong to the test set. Additionally, there are 3568 cropped mammograms and 3568 masks.

Brief Description of Repository Functions
Mammograms_code.ipynb:
This script contains a function to retrieve the paths of all mammograms on the local machine and merges each image path with its pathology in a dataframe. The dataframe is then saved as a CSV file.

mask_code.ipynb:
This script contains a function to retrieve the paths of all patches on the local machine, then merges each mask path with its pathology in a dataframe. This dataframe is then saved as a CSV file. Note: There are more masks than mammograms because some mammograms have multiple lesions.

convert_dicom.ipynb:
Images (mammograms, masks, and abnormality crops) provided by CBIS-DDSM are saved in DICOM format. This function saves the 16-bit mammograms from DICOM as rescaled 16-bit PNG files.

Original_Split.ipynb:
This script creates test and training sets according to the standardized split provided by the official paper. The paths of all images are stored in a dataframe and saved as a CSV file.