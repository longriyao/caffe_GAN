##Deep Convolutional Generative Adversarial Nerworks with caffe implementation
This project uses GAN to implement gray image colorization. The network copys from  [ aleju/colorizer.](https://github.com/aleju/colorizer) 
##Changed Files:
    caffe.proto:
    	Add the new line:
    		  optional bool param_propagate_down = 6;

    net.cpp
    	Add the following lines:
    		if(param_spec->has_param_propagate_down()){
       	 		param_need_backward = param_spec->param_propagate_down();
      		}

    		
##Usage:
1. The Installation completely the same as [Caffe](http://caffe.berkeleyvision.org/). Please follow the [installation instructions](http://caffe.berkeleyvision.org/installation.html). Make sure you uncomment WITH_PYTHON_LAYER := 1 to support for python layer.
	add the caffe_GAN/caffe_GAN/gan_example/lib/layers path to $PYTHONPAT
2. Building the dataset:
	* Download [Labeled Faces in the Wild](http://vis-www.cs.umass.edu/lfw/) and extract it somewhere
	* In `gan_example/` run `python lib/utils/generate_dataset.py --path="lfw"`, where `lfw` is the path to your LFW dataset
	* Generate the train.txt file:
	* In `out_unaug_64x64/` run `ls -1 > ../train.txt`
3. Train
	* `gan_example/` run `./train.sh` begin training
	

