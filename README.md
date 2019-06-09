# GZ2_project

<p> Galaxy Zoo 2 Machine Learning Project by Andrew Engel</p>

<p>as a rough summary, I first generate my dataset using the 'generate skyview' notebook using a list of RA and DEC from the GZ2 catalog. The SkyView service returns SDSS optical images from the coordinate input in the u,g,r,i,z bands and saves the data as an numpy array. One of the largest struggles is that this is a lengthy and often fussy endeavor to accomplish for the 10,000 images I would like to use.</p>

<p>The real meat of the project and the original goal given to me by Professor Huerta of the NCSA at UIUC, is to reach 90% level accuracy in a network that is able to sort galaxies by morphology. I started in stumbles, first only using g-band and not telling SkyView at what angular radius to take photos, such that unknowingly I had focussed all of the images at the galaxy centers. With this dataset I was able to accomplish at best 85% accuracy with a convolutional neural network after augmenting my dataset with rotations, which my network of course should be invarient to under the cosmological principle.</p>

<p>Though I started with the CNN, I was advised that I could push my accuracy above 90% by utilizing other kinds of networks. I include my attempts on these alternative architectures in my repository for posterity, but none of them improved my accuracy. I attempted building a RESnet while still making use of the tensorflow sequential networks by using a block I had found online. I also built a transfer network following some simple tutorials online.</p>

<p>After attempting these and not producing results, I was advised to improve my dataset by including additional bands, and from this I realized I needed to set a radius for the images. Soon after realizing this, unfortunately, the SkyView service lost remote data access to SDSS for about a month and I was forced to delay</p>

<p>Currently, I am using generate skyview to generate 10,000 numpy arrays of 5 SDSS bands, and then will use some of the CNN code I have to build a network that will flow from that directory to generate a rotationall invarient network. the dataset is improved in resolution-- I was originally only using 28x28 images and now am moving to 64x64 images. As well as including all five bands.</p>

<p>The data needed to run the code is available to download here: https://drive.google.com/drive/folders/1ufX23uK4TUCGkom_WQlLFRnlU1MpGLWr?usp=sharing </p>

<p>One would also need to download the correct GZ2 file from their website: https://data.galaxyzoo.org/ ; under GZ2, table 1, csv. </p>
