# Image Analysis for Automatic Cell Counting
---
## Overview
This project focuses on applying image analysis techniques to microscopy images to automate the delineation of a Region of Interest (ROI) and the subsequent counting of human promyelocytic leukemia (HL60) cells. Automated cell counting based on computer vision improves precision and facilitates researchers' work by replacing subjective manual counting.

---

## Methodology

### Task 1: Region of Interest (ROI) Delineation
Two different approaches were implemented and compared to detect the counting grid:
*   **Line Detection (Hough Transform):** Pre-processing with a bottom-hat filter followed by thresholding to detect the four most prominent lines bounding the ROI.
*   **Binary Morphological Filters:** A non-linear spatial filtering approach using mathematical morphology (closing, erosion, and opening) to simplify the image and define the counting region.

**Conclusion for Task 1:** Morphological filters outperformed the line detection method, achieving an average Jaccard index of 0.991 on the test set.

---

### Task 2: Cell Segmentation and Counting
For cell recognition, the Circle Hough Transform was utilized to identify circular structures. To optimize precision, two different image pre-processing techniques were compared:
*   **Morphological Filters:** Application of a bottom-hat filter, closing, multilevel thresholding, and binary thresholding.
*   **Clustering:** Application of a bottom-hat filter followed by K-means clustering (k=3) to segment the image based on intensity.

Bounding boxes were then projected based on the detected circles' coordinates. Cells overlapping the exterior lower and right boundaries of the ROI were excluded from the final count.

---

## Results
The performance of the cell counting algorithm was evaluated using Recall (Sensitivity), Precision, and F-measure. A cell was considered correctly detected if the Jaccard index between the generated bounding box and the ground truth was greater than 0.5.

*   **Clustering Pre-processing:** Yielded moderate results, with an average F-measure of approximately 0.724 on the test set.
*   **Morphological Filters Pre-processing:** Achieved highly satisfactory results, with an average Precision of 0.912 and an average F-measure of 0.915 on the test set.

---

## Conclusion
The most effective pipeline for this problem involves using binary morphological filters for both the ROI delineation and the image pre-processing phase prior to circle detection. The system proved to be globally viable and robust, generalizing well to unseen test data.

---

*Faculdade de Engenharia da Universidade do Porto (FEUP) - Bioengineering Degree, Biomedical Image Analysis*

---

## References
1. Özkan, A., İşgör, S. B., Şengül, G., & İşgör, Y. G. (2018). Computer vision based automated cell counting pipeline: A case study for HL60 cancer cell on hemocytometer. Biomedical Research, 29(14), 2956-2962.
