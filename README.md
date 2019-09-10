# GZ2_project

<p> Galaxy Zoo 2 Machine Learning Project by Andrew Engel</p>

<p>Using a similar dataset described by Asad Khan et al in: https://arxiv.org/pdf/1812.02183.pdf and a similar network architecture described by H. Dominguez Sanchez et al in: https://arxiv.org/pdf/1711.05744.pdf I train a convolutional neural network to do a supervised learning problem to classify galaxy zoo 1 galaxies (https://data.galaxyzoo.org/ and see paper by Chris Lintott et all https://academic.oup.com/mnras/article/410/1/166/1032478) by a binary morphology of spiral and elliptical. My best model achieves a ~95% accuracy using ~35,000 training examples of 120x120 galaxy images in 0-255 integer .npy format in the five SDSS bands [u,g,r,i,z]. I use a customized generator based on: https://stanford.edu/~shervine/blog/keras-how-to-generate-data-on-the-fly on top of which I have added a data augmentor.</p>

<p>Special thanks to Gautham Narayan, Eliu Huerta, Asad Khan, and Anil Radkrishnan for mentoring me and providing assistance throughout this project.</p>
