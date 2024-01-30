# CGCNN
Application of Feng et al.'s DOSnet to predicting bond valence data from density of states data

# I. Background 
The density of states (DOS) of a material is a fundamental descriptor of its electronic structure, 
capturing the distribution of the material’s available electrons as a function of its energy levels. This 
provides insights into various properties such as conductivity, reactivity, and optical behavior, making 
DOS highly relevant to the prediction of these properties. Traditional approaches have focused on the 
manual extraction of features from the DOS, involving the selection and calculation of specific features 
such as peak height or band gaps [1-5]. Identifying what aspects of the DOS are relevant to predicting the 
target data requires expertise and may introduce subjectivity to the model, potentially limiting its 
prediction accuracy by failing to capture complex relationships within the DOS data. However, increases 
in computational power and improved algorithms have made it easier to handle the high dimensionality of 
DOS data, allowing for its direct integration into machine learning models. This eliminates the need for 
manual feature extraction and potentially provides less subjective, more accurate predictions. Zhu et al. 
used this approach to predict band gaps in organic semiconductors by feeding raw DOS data to a deep 
learning model, achieving a mean absolute error (MAE) of 0.08 eV [5]. Fung et al. built upon this 
approach through the development of DOSnet, a 1D convolutional neural network (CNN) used to extract 
features from unaltered surface atom DOS data, which they used to predict absorption energy with a 
MAE 0.138 eV [6]. This shift towards the use of featureless DOS data for machine learning has the 
potential to capture more subtle interdependencies within the DOS data and reduce bias while presenting 
more efficient, accurate material property predictions and discoveries.  
# II. Scope  
Understanding local bonding environments through bond valence analysis offers valuable insights 
into ion migration pathways, activation energy, and overall conductivity, guiding the design of materials 
with enhanced ionic transport properties. As part of a larger effort to predict conductive properties in 
crystalline materials, this proposal seeks to leverage Fung et al.’s model to featurize DOS data for 
predicting bond valence data. Combining the raw DOS and crystal structure data, which holds crucial 
spatial information, could offer a featurization model greater context for its convolutional filters, yielding 
more nuanced and useful feature extraction. This project will evaluate if Fung et al.’s DOSnet can be 
applied to the prediction of bond valence data and whether the addition of crystal structure data will 
improve the performance of the model.  
# III. Procedure 
The first step in this process will be obtaining and processing the DOS, crystal structure, and bond 
valence data for a large number of materials, ideally 104. This will be done by writing a program to return 
all materials in the Materials Project for which this data exists using pymatgen, the Materials Project 
Python library, and extracting and cleaning this data for each material. This DOS and crystal structure 
data will be concatenated for each material along a common axis to create a combined feature vector, and 
these vectors will be split into training, validation, and testing sets. Next, after setting up an environment 
with the relevant libraries, the DOSnet Github repository will be cloned and the model configurations 
(‘net.py’ and ‘params.json’) will be modified to reflect the new specifics of the input data, such as vector 
size and number of hidden layers. Next, the model will be trained and tested, adjusting hyperparameters 
as needed based on validation performance. Once the model achieves satisfactory performance, DOSnet's 
built-in feature importance analysis will be used to identify which input features were most significant to 
the bond valence predictions. 
# References: 
[1] Fung, V. X., Hu, G., Ganesh, P., & Sumpter, B. G. (2020). Machine learned features from density of 
states for accurate adsorption energy prediction. Nature Communications, 11(1), DOI: 10.1038/s41467
020-14699-w
