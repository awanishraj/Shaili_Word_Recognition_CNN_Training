# CNN Training code

Training and testing requires the following files that can be edited as required

* train_test.prototxt
	* Input path of 'training' and 'testing' LMDB files
	* Network architecture - Same as LeNet. Changes to last layer for number of classes
* solver.prototxt
	* Parameters for the training algorithm
* deploy.prototxt
	* Network architecture for feature extraction process
	
	
Need to run following commands in sequence:

* To generate LMDB from Training images

	`[PATH_TO_CAFFE]/build/tools/convert_imageset --backend=lmdb --resize_height=50 --resize_width=100 --shuffle ./ list_tmp.txt [TRAIN_LMDB_OUTPUT_PATH]`
	
	`[PATH_TO_CAFFE]/build/tools/convert_imageset --backend=lmdb --resize_height=50 --resize_width=100 --shuffle ./ list_tmp.txt [TEST_LMDB_OUTPUT_PATH]`
	
* To begin training
	* Edit train_test.prototxt, solver.prototxt, and deploy.prototxt appropriately
	* Run the following command to begin training
	
		`[PATH_TO_CAFFE]/build/tools/caffe train -solver solver.prototxt`
	* Use `nohup` to run the training in background
	
		`nohup [PATH_TO_CAFFE]/build/tools/caffe train -solver solver.prototxt > train.log &`
		
* Upload following files to Android mobile
	* weights.caffemodel
	* deploy.prototxt
	* classes.txt (All class names in correct sequence)
	
## Sample trained files
'android_hiwiki' directory contains a sample of trained files that can be copied to android mobile to work with Shaili app

## Contact
Contact developer at awanishraj.iitm@gmail.com