
# I. Generate documentation 

### 1. Install Sphinx
```sh
pip install -U Sphinx
```

### 2. Initialize the Sphinx Configuration
```sh
sphinx-quickstart
```
- Fill out some basic configurations

### 3. Update the conf.py File
```sh
import os
import sys
sys.path.insert(0, os.path.abspath(CODE_ROOT))
```
```sh
html_theme = 'sphinx_rtd_theme'
```
- pip install sphinx-rtd-theme
```sh
extensions = ['sphinx.ext.autodoc', 'sphinx.ext.napoleon']
```

### 4. Auto-generate the rst Files
```sh
sphinx-apidoc -f -o source  $CODE_ROOT
```

### 5. Build the HTML

- Add "modules" in index.rst
```sh
.. toctree::
   :maxdepth: 2
   :caption: Contents:

   modules
```
```sh
make html
```

### 0. Modify code and rebuild html
```sh
sphinx-apidoc -f -o source  $CODE_ROOT
make html
```

### 0. Code sample for auto generated-documenting
```sh
import cv2
import numpy as np
from typing import Tuple

class A:
    def resize_im(self, im: np.ndarray, out_size: Tuple[int, int])->np.ndarray:
        '''
        :param im: rgb (mxnx3 np.ndarray) or gray (mxn np.ndarray) image
        :param out_size:  output's size (width, height)
        :return: resized image
        '''
        return cv2.resize(im, dsize=out_size, interpolation=cv2.INTER_CUBIC)
```


# II. Publish on Github.io

- Copy "build/html" to $ROOT and rename to "docs"
- Add  an empty file ".nojekyll"
- Push to a github repository 
- In settings/pages, point "source" to docs
- In About settings, specific URL for website

## References:
- [Sphinx Guide](https://betterprogramming.pub/auto-documenting-a-python-project-using-sphinx-8878f9ddc6e9)