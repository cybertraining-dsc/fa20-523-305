# Applying Computer Vision to Medical Imaging

Computer vision technology has made great strides in the past decade. The most obvious proof of this statement comes from looking at early consumer image classification programs. Early programs from the early 2010s struggled to find the difference between a cat and a person. Now, consumer image classification programs can accurately tell the difference between two cats. With these improvements, there are great applications for computer vision to aid with radiology.

## Specific Application Areas

The five most common modalities of medical imaging are: X-Rays, CT scans, MRI, ultrasound, and PET scan [1]. Within these major modalities, there are various special types of each imaging technique such as an fMRI, which is called a functional MRI. Then there are the more niche imaging techniques that are used. For example, Diffusion Tensor Imaging (DTI) is a technique that allows visualization of the white matter in the brain. One application of this imaging technique is coming up with a way to diagnose certain mental illness from imaging [2]. Seeing as mental health issues are typically tougher to diagnose, this would be a major breakthrough. 

Oncology seems to be a major area of study for computer vision in medical imaging. Logically this makes sense as cancers seems to create anomalies that can be seen in medical imaging. Thoracic imaging focuses on looking at the lungs, and computer vision could aid with finding anomalies that could lead to the early detection of cancer which in turn creates a better prognosis. An application that is only based on analyzing normal images or video, is analyzing a colonoscopy. Certain structures in the colon can create colorectal cancer if not correctly identified and classified as benign or malignant. Another imaging technique that can be rather difficult to analyze correctly are mammograms, and correctly identifying the various anomalies that are present as either malignant or benign [3].

## How Computer Vision can be used in Medical Imaging

In a perfect world, a sufficiently advanced AI could be the only entity to ever examine a certain medical image before providing a prognosis. In reality our technology is far from achieving this lofty goal. In the meantime, AI can still be used to improve radiologist workflows. In some studies, it was found that a radiologist would have to look at one image every three to four seconds to stay caught up with their workload in an 8-hour day. It is obvious why this could cause issues with accuracy. Now think about having the same time to look at an image, but instead of a raw image, the image comes with suggestions of diagnosis, and points to specific areas for the radiologist to focus on. This would improve the effectiveness of radiologists without relying completely on the AI model to be 100% accurate [3].

## Modeling Techniques 

There are two main techniques that are currently being employed to work with computer vision and medical imaging. The first technique is extra certain features from the image based on qualifications that are input to the system. For example, the user of the system might put in to extract the texture and shape of anomalies in the lower left lobe of the lungs as one of the features. Once all of these features are collected, they are fed into an expert system that selects the most promising features that could help with diagnosis. These selected features are fed into a machine learning classifier system that then sends its insights along with the image to the radiologist [3]. This system has it’s draw backs that are typical of expert systems. First off, setting the system up and giving it the parameters for the expert system is extremely complicated, and incorrect parameters in the system could heavily affect the output. 

The second technique employs deep learning. Over the years, deep learning has become a widely used method to gain insights from data, and computer vision is no exception. The deep learning models have the benefit of not requiring any setup or expert systems. Really the biggest challenge is getting a good enough training data such that the deep learning model accurately predicts in the same way that a radiologist would. Some studies have been done on testing the accuracy of such methods and they found that “deep learning technologies are on par with radiologists’ performance for both detection and segmentation tasks in ultrasonography and MRI, respectively” [3]. 

## Special Considerations

While deep learning seems to be the best method to create these systems, experts still need to be involved with the creation of these systems. One example of this is having expert radiologists evaluate training data. Just because there might be 30 years worth of data, that doesn’t mean it all can be used. The medical field is constantly evolving and making sure that the data you train your model is relevant is an important part of creating any model. Also using radiologists to shape the software that is used by radiologists would always improve the end product [4]. Too often software is built by software engineers and data scientists and doesn’t use enough advice from experts in the field, and this almost always is a detriment to the software. 

Radiologists using these deep learning tools, will require a great deal of training with these tools. They know that the AI model is not always going to be correct, and it is important that the radiologists understand how the software works so that they can make a determination of whether their opinion should be trusted over the output from the software, especially early on with newer technology [4].

## References

[1] "Different Imaging Tests Explained | UVA Radiology", UVA Radiology and Medical Imaging Blog for Patients, 2019. [Online]. Available: <https://blog.radiology.virginia.edu/different-imaging-tests-explained/>. [Accessed: 20- Oct- 2020].

[2] "Diffusion Tensor Imaging (DTI) | Psychiatry Neuroimaging Laboratory", Pnl.bwh.harvard.edu, 2020. [Online]. Available: http://pnl.bwh.harvard.edu/portfolio-item/diffusion-tensor-imaging-dti/. [Accessed: 20- Oct- 2020].

[3] A. Hosny, C. Parmar, J. Quackenbush, L. Schwartz and H. Aerts, "Artificial intelligence in radiology", Nature Reviews Cancer, vol. 18, no. 8, pp. 500-510, 2018. Available: 10.1038/s41568-018-0016-5 [Accessed 20 October 2020].

[4] "AI and the Future of Radiology", Diagnostic Imaging, 2020. [Online]. Available: https://www.diagnosticimaging.com/view/ai-and-future-radiology. [Accessed: 20- Oct- 2020].
