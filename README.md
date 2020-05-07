# Blender4SonarImage
Blender layout and python script for sonar image generation based on Blender. <br>
Version: Blender 2.80, Python 3.7 <br>
All the projects are created and supported by 
# Dependencies
- OpenEXR
⋅⋅⋅Though it's a cross-platform software, we mainly run Blender on Windows and you can find the OpenEXR version we use [here](https://github.com/LIUDINGYU/Blender4SonarImage/blob/master/OpenEXR-1.3.2-cp37-cp37m-win_amd64.whl) (which only supports Windows). Other versions can be found [here](https://packages.ubuntu.com/search?keywords=openexr) and other sources.⋅⋅
⋅⋅⋅As for installation and configuration for Blender, refer to: https://www.kunihikokaneko.com/dblab/cg/bpypip.html (Japanese version). Maybe I'll update the translation or other English versions later.⋅⋅
- OpenCV
⋅⋅⋅To use OpenCV in Blender, link it by adding the following lines in your Python script.⋅⋅
```python
import sys
sys.path.append("directory OpenCV installed/build/python/cv2/python-3.7/") 
```
⋅⋅⋅Also paste the .dll file to your workspace.⋅⋅
- Others
Other packages for Blender can be found [here](https://www.lfd.uci.edu/~gohlke/pythonlibs/#wxpython).
# Overview
Folders brick, assembly and marker include .blend files and the generated datasets based on three example scenarios mentioned in our paper. 
# How to synthetic your own dataset
- 3D modeling
- Tips for Python script
# Related research and papers


