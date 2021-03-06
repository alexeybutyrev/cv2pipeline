# cv2pipeline
Image Processing Pipelines built on OpenCV2

____________
Installation
____________

___________________
Virtual Environment
___________________

run:

  sudo apt-get install virualenv

create:

  mkdir envs
  cd envs
  virtualenv -p python3 cv2pipeline

If you place the envs folder one level up from the project root,
you can activate from the project root directory:

  . activate.sh

________
Package Dependencies
________

After creating a virtual environment, install the dependencies:

pip install -r requirements.txt

for RPi4, use:

pip install -r requirements.pi4.txt

You may need to install the following:

sudo apt-get install libatlas-base-dev

___________________
MacBook Air M1 Chip
___________________

There are some issues with installing packages on the MacBook Air M1.  

Easiest way to install numpy + Tensorflow is to follow the instructions here:

https://github.com/apple/tensorflow_macos

You can point this to an existing virtualenv (or it will create one for you).

#Rosetta / Compatibility Approach (works after a fashion) #

Once you have an environment with Numpy + Tensorflow, you'll need to install the Brew package manager.  
This has some issues for M1 as well... see here for instructions on M1 installation:

https://osxdaily.com/2020/11/18/how-run-homebrew-x86-terminal-apple-silicon-mac/

If you're using the M1, you'll get used to the Rosetta arch compatibility stuff soon enough :)

Once you've got Brew installed, use it to install cmake (with the Rosetta arch previx):

arch -x86_64 brew install cmake

Make sure you've activated the virtual environment in which tensorflow+numpy was installed.

Now you can install opencv (using compatibility mode):

arch -x86_64 pip install opencv-python

Then:

pip install readchar
pip install imutils

Now you're good to go (although you have to run python in compatability mode with arch -x86_64).  This is
probably not the best approach but I haven't yet figured out another way to get opencv to install on M1 
MacBook Air with the native ARM architecture.  It may require building opencv manually (the way we used
to have to do it), but that will still require finding an ARM workaround for the cmake dependency.  
Speedbumps.

# Better approach #
See this for instructions on setting up Brew for M1:

https://github.com/mikelxc/Workarounds-for-ARM-mac

Make sure to add brew to your path as detailed in the above.

After doing this, I was able to install cmake with compile from source turned on:

./brew install --build-from-source cmake

According to the instructions above, it should also work with

./brew install -s cmake

(cmake built correctly, but pip install opencv-python still failed horribly...
 so far only the rosetta arch build works...)


