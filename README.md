# Blender4SonarImage
Blender layout and python script for sonar image generation based on Blender. <br>
Version: Blender 2.80, Python 3.7 <br>
All the projects are created and supported by [Dingyu Liu](https://github.com/LIUDINGYU) and [Yusheng Wang](https://github.com/sollynoay).
# Dependencies
- OpenEXR <br>
Though it's a cross-platform software, we mainly run Blender on Windows and you can find the OpenEXR version we use [here](https://github.com/LIUDINGYU/Blender4SonarImage/blob/master/OpenEXR-1.3.2-cp37-cp37m-win_amd64.whl) (which only supports Windows). Other versions can be found [here](https://packages.ubuntu.com/search?keywords=openexr) and other sources.<br>
As for installation and configuration for Blender, refer to: https://www.kunihikokaneko.com/dblab/cg/bpypip.html (Japanese version). Maybe I'll update the translation or other English versions later.<br>
- OpenCV <br>
To use OpenCV in Blender, link it by adding the following lines in your Python script.<br>
Also paste the .dll file to your workspace.<br>
```python
import sys
sys.path.append("directory OpenCV installed/build/python/cv2/python-3.7/") 
```
- Others <br>
Other packages for Blender can be found [here](https://www.lfd.uci.edu/~gohlke/pythonlibs/#wxpython).
# Overview
Folders brick, assembly and marker include .blend files and the generated datasets based on three example scenarios mentioned in our paper. Blender files consist of the 3D modeling scenario and Python script to synthesize the image. You can just copy-paste the code and run but remember to change the saving path to your own. Also you could make some slight revisions to get images you prefer.
# How to synthetic your own dataset
## 3D modeling
## Tips for Python script
- Be sure to link to OpenCV properly and change the saving path to your own directory.
- The camera's position and rotation can be easily controlled so that images can be generated from different views. Check out the code for specific statements you might need.
- Change the range of camera by modifying the variables `uplimit` and `lowlimit`.
- Images saved with prefix 'resize' are the resized rectangle images. You can adjust the scale by changing the parameters of `cv.resize()`. 
# Related research and papers
1. Seungchul Kwak, Yonghoon Ji, Atsushi Yamashita, and Hajime Asama. Development of acoustic camera-imaging simulator based on novel model. In Proceedings of the IEEE 15th International Conference on Environment and Electrical Engineering, pages 1719–1724, 2015.
2. Romulo Cerqueira, Tiago Trocoli, Gustavo Neves, Sylvain Joyeux, Jan Albiez, and Luciano Oliveira. A novel gpu-based sonar simulator for real-time applications. Computers & Graphics, 68:66–76, 2017.
3. Ngoc Trung Mai, Yonghoon Ji, Hanwool Woo, Yusuke Tamura, Atsushi Yamashita, and Hajime Asama. Acoustic image simulator based on active sonar model in underwater environment. In Proceedings of the IEEE 15th International Conference on Ubiquitous Robots, pages 775–780, 2018.


