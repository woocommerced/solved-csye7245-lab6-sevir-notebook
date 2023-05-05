Download Link: https://assignmentchef.com/product/solved-csye7245-lab6-sevir-notebook
<br>
This lab demonstrates analyzing the results of training, visualizing the results on Synthetic Radar Data from SEVIR Dataset (Storm Event Imagery Dataset for Deep Learning Applications in Radar and Satellite Meteorology) using the pretrained models.

<strong>Why this use case?</strong>

The Earth’s weather is continuously monitored by sensors that collect terabytes of data every day. Over the US, satellite observations provided by GOES-R series satellites (GOES-16 &amp; GOES-17), and weather radar data provided by the national network of WSR-88D (NEXRAD) radars are two major sources of weather sensing used by forecasters, decision makers, and the general public.

Figure 1: The Storm EVent ImagRy (SEVIR) dataset contains over 10,000 spatially and temporally aligned sequences across the five image types.

Archives of these two sensing modalities make up petabytes of data that include images of clouds in both visible and infrared, depictions of precipitation intensity, and detection of lightning. Recently, there has been a great deal of work to use deep learning to better leverage these rich data sources, specifically for applications like short term weather forecasting, synthetic weather radar for areas lacking traditional weather radar, improved data assimilation for improved numerical weather prediction, and many others. Furthermore, access to datasets like GOES &amp; NEXRAD is becoming easier as cloud services such as Google Earth Engine, Amazon Open Data Registry, IBM’s PAIRS and others provide access to Earth system datasets.




<h1><strong>Dataset</strong></h1>

SEVIR is a collection of temporally and spatially aligned image sequences depicting weather events captured over the contiguous US (CONUS) by GOES-16 satellite and the mosaic of NEXRAD radars. Figure 1 shows a set of frames taken from a SEVIR event. SEVIR contains five image types: GOES-16 0.6 µm visible satellite channel (vis), 6.9 µm and 10.7 µm infrared channels (ir069, ir107), a radar mosaic of vertically integrated liquid (vil), and total lightning flashes collected by the GOES-16 geostationary lightning mapper (GLM) (lght). See Table 1 for details. Each event in SEVIR consists of a 4-hour length sequence of images sampled in 5 minute steps. The lightning modality is the only non-image type, and is represented by a collection of GLM lightning flashes captured in the 4 hour time window. SEVIR events cover 384 km x 384 km patches sampled at locations throughout the continental U.S. (CONUS). The pixel resolution in the images differ by image type, and were chosen to closely match the resolution of the original data. Since the patch dimension of 384 km is constant across sensors, the size of each image differs (as shown in Table 1).




<h1><strong>Experiment Setup</strong></h1>

We implemented this lab using <a href="https://mybinder.org/">https://mybinder.org/</a> which helps to open notebooks in an executable environment, making your code immediately reproducible and launch our <a href="https://github.com/MIT-AI-Accelerator/neurips-2020-sevir">neurips-2020-sevir</a> repository as follows:







Once the repository is build, we can access it in a Juypter Dashboard environment with the folder structure similar to that in <strong>neurips-2020-sevir</strong> repository




<strong>Downloading pretrained models</strong>

<strong> </strong>

Before downloading the models, we created the following folders for downloaded data:




<ol>

 <li>/data/sample: Location for placing the synrad testing sample data</li>

</ol>







<ol start="2">

 <li>models/synard: Location for placing the pretrained models</li>

</ol>

To download the models trained in the paper, we can execute the following:

cd models/

python download_models.py

<strong> </strong>

<strong>Alternatively, we used the below command to download the pretrained models:</strong>




wget -O models/synrad/gan_mae_weights.h5 “<a href="https://www.dropbox.com/s/d1e2p36nu4sqq7m/gan_mae_weights.h5?dl=1">https://www.dropbox.com/s/d1e2p36nu4sqq7m/gan_mae_weights.h5?dl=1</a>”







wget -O models/synrad/mse_vgg_weights.h5 “<a href="https://www.dropbox.com/s/a39ig25nxkrmbkx/mse_vgg_weights.h5?dl=1">https://www.dropbox.com/s/a39ig25nxkrmbkx/mse_vgg_weights.h5?dl=1</a>”







wget -O models/synrad/mse_weights.h5 “<a href="https://www.dropbox.com/s/6cqtrv2yliwcyh5/mse_weights.h5?dl=1">https://www.dropbox.com/s/6cqtrv2yliwcyh5/mse_weights.h5?dl=1</a>”







wget -O data/sample/synrad_testing.h5 “<a href="https://www.dropbox.com/s/7o3jyeenhrgrkql/synrad_testing.h5?dl=1">https://www.dropbox.com/s/7o3jyeenhrgrkql/synrad_testing.h5?dl=1</a>”










Navigate through the notebooks folder and access the <strong>AnalyzeSyntheticRadar.ipynb </strong>notebook which we implemented analysis of synthetic radar data




<strong>Path: </strong>neurips-2020-sevir/notebooks/AnalyzeSyntheticRadar.ipynb

<h1><strong>Tests</strong></h1>

<strong>Installed the required libraries:</strong>




<strong>Plotting the metrics:</strong>




<h1><strong>Results</strong></h1>

After running the trained models on samples from the test set, we used the basic color maps and loaded part (1000 data points) of the test dataset, ran the model and finally plotted output loss along with inputs using default cmap which ideally resulted in the following cmap:

Three examples of the synthetic weather radar model trained using three different loss functions. MSE leads to an accurate, albeit overly smoothed, prediction. The content and adversarial losses are able to provide additional textures that are visually more similar to the target.

<h1><strong>Lessons learned</strong></h1>

<ol>

 <li>Learned the concept of transferred learning that is utilizing pretrained model for sample test</li>

 <li>Learned the usage of TensorFlow and its library called Keras to load pretrained models</li>

 <li>Learned how to leverage executable environment tools like mybinder to replicate or reproduce code</li>

</ol>




<h1><strong>References</strong></h1>

<a href="https://proceedings.neurips.cc/paper/2020/file/fa78a16157fed00d7a80515818432169-Paper.pdf">https://proceedings.neurips.cc/paper/2020/file/fa78a16157fed00d7a80515818432169-Paper.pdf</a>

<a href="https://github.com/MIT-AI-Accelerator/neurips-2020-sevir">https://github.com/MIT-AI-Accelerator/neurips-2020-sevir</a>








