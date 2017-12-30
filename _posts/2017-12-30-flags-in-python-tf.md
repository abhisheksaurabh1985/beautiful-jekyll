---
layout: post
title: Flags in Python and Tensorflow
tags: [Python, Machine Learning, Software Engineering]
---
<p align="justify">
Flags in Python allows us to change the configurable parameters of the script straight from the command line. In other words, they can be used to define some switches in the code. This functionality assumes significance in machine learning because the models usually require a lot of parameters to be defined at the beginning. Number of neurons in the hidden unit, learning rate, type of optimization method are some of the examples. Using `flags` we can define the default values and also some explanatory text which will be displayed on the command line.  
</p>

<p align="justify">
Following is an example of flags in Tensorflow. The script requires two parameters to be passed at runtime. When no parameters are passed, it prints the default value. Also note the output when `--help` is used at runtime.  
</p>

```python
import tensorflow as tf

FLAGS = tf.app.flags.FLAGS
tf.app.flags.DEFINE_integer('data_num', 100, """Flag of type integer""")
tf.app.flags.DEFINE_string('img_path', './img', """Flag of type string""")


def main(argv):
    print(FLAGS.data_num, FLAGS.img_path)


if __name__ == '__main__':
    tf.app.run()
```

Display help using `python tf_flags_example.py --help`. Following is the output.
```
usage: tf_flags_example.py [-h] [--data_num DATA_NUM] [--img_path IMG_PATH]

optional arguments:
  -h, --help           show this help message and exit
  --data_num DATA_NUM  Flag of type integer
  --img_path IMG_PATH  Flag of type string
```

Run script without parameters `python tf_flags_example.py`. Output `(100, './img')` is with the default parameters defined in the flags. When the same script is run with the parameters at the command line i.e. `python tf_flags_example.py --data_num 35`, we get the following output: `(35, './img')`





