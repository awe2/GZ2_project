# GZ2_project

<p> Galaxy Zoo 2 Machine Learning Project by Andrew Engel</p>

<p>as a rough summary, I first generate my dataset using the 'generate skyview' notebook using a list of RA and DEC from the GZ2 catalog. The SkyView service returns SDSS optical images from the coordinate input in the u,g,r,i,z bands and saves the data as an numpy array. One of the largest struggles is that this is a lengthy and often fussy endeavor to accomplish for the 10,000 images I would like to use.</p>

<p>The real meat of the project and the original goal given to me by Professor Huerta of the NCSA at UIUC, is to reach 90% level accuracy in a network that is able to sort galaxies by morphology. I started in stumbles, first only using g-band and not telling SkyView at what angular radius to take photos, such that unknowingly I had focussed all of the images at the galaxy centers. With this dataset I was able to accomplish at best 85% accuracy with a convolutional neural network after augmenting my dataset with rotations, which my network of course should be invarient to under the cosmological principle.</p>

<p>Though I started with the CNN, I was advised that I could push my accuracy above 90% by utilizing other kinds of networks. I include my attempts on these alternative architectures in my repository for posterity, but none of them improved my accuracy. I attempted building a RESnet while still making use of the tensorflow sequential networks by using a block I had found online. I also built a transfer network following some simple tutorials online.</p>

<p>After attempting these and not producing results, I was advised to improve my dataset by including additional bands, and from this I realized I needed to set a radius for the images. Soon after realizing this, unfortunately, the SkyView service lost remote data access to SDSS for about a month and I was forced to delay</p>

<p>Currently, I am using generate skyview to generate 10,000 numpy arrays of 5 SDSS bands, and then will use some of the CNN code I have to build a network that will flow from that directory to generate a rotationall invarient network. the dataset is improved in resolution-- I was originally only using 28x28 images and now am moving to 64x64 images. As well as including all five bands.</p>

<p>The data needed to run the code is available to download here: https://drive.google.com/drive/folders/1ufX23uK4TUCGkom_WQlLFRnlU1MpGLWr?usp=sharing </p>

<p>One would also need to download the correct GZ2 file from their website: https://data.galaxyzoo.org/ ; under GZ2, table 1, csv. </p>

<p>Currently, ...w_augmentation is the work in progress file, I am using a custom data generator that has augmentation built into it to read the arrays. I normalize each array to the filters maximum = 1 and minimum = 0 for each galaxy. I perform flips, rotations of 45 degrees, shifts of 4 pixels horizontal or vertically, and zooms in range (0.75,1.3). rotations are applied to all, normalization is applied to all, all other augmentations only occur if random.random() returns a value > 0.75, which would be 25% of the time.

<p>w/o augmentation, the best validation accuracy I can achieve is 0.85. In the most recent attempt, I have also thrown away the small sample of 'oddities,' GZ2 labels that were labeled as 'A,' mostly stars. If I wanted to, I could write a binary classifier for stars and galaxies that would serve the purpose of that third class in the pipeline.</p>

<p>w/ augmentation, best score I have achieved is 0.87, the highest I have ever gotten. Still a bit shy of 0.90, but creeping closer.</p>

<p>Plans for what will be done after I have a model that sorts to high precision will be to work on data visualization methods ecspecially interpretability. https://distill.pub/2018/building-blocks/ is a wonderful article about the subject. I think it would be neat to see if my network can identify features of galaxies that are unknown that are useful in identification, and whether these features can be used to discover new science.</p> 
