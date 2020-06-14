# Blender4SonarImage
Blender layout and python script for sonar image generation based on Blender. <br>
Version: Blender 2.80, Python 3.7 <br>
All the projects are created and supported by [Dingyu Liu](https://github.com/LIUDINGYU) and [Yusheng Wang](https://github.com/sollynoay).
# Overview
- Folders brick, assembly and marker include .blend files and our generated datasets based on these three example scenarios mentioned in our paper. Blender files consist of the 3D modeling scenario and Python script to synthesize the image. You can just copy-paste the code and run but remember to change the saving path to your own. Also you could make some slight revisions to get images you prefer (follow the guidance below).
- [OpenEXR-1.3.2-cp37-cp37m-win_amd64.whl](https://github.com/LIUDINGYU/Blender4SonarImage/blob/master/OpenEXR-1.3.2-cp37-cp37m-win_amd64.whl): OpenEXR dependency version used in our project.
- [rotate_view.blend](https://github.com/LIUDINGYU/Blender4SonarImage/blob/master/rotate_view.blend): Python script in this .blend file provides an alternative way to rotate the camera along its local axes. Might be useful to you.
# Dependencies
- OpenEXR <br>
Though it's a cross-platform software, we mainly run Blender on Windows and [the OpenEXR version we use](https://github.com/LIUDINGYU/Blender4SonarImage/blob/master/OpenEXR-1.3.2-cp37-cp37m-win_amd64.whl) only supports Windows. Other versions can be found [here](https://packages.ubuntu.com/search?keywords=openexr), so as other sources.<br>
As for installation and configuration for Blender, refer to: https://www.kunihikokaneko.com/dblab/cg/bpypip.html (Japanese version). Maybe I'll update the translation or other English versions later.<br>
- OpenCV <br>
To use OpenCV in Blender, link it by adding the following lines in your Python script.<br>
Also paste the .dll file to your workspace.<br>
```python
import sys
sys.path.append("directory OpenCV installed/build/python/cv2/python-3.7/") 
```
- Others <br>
Blender has its own embedded Python interpreter and modules, and you can use Blender very efficiently with them. Find other useful packages for Blender [here](https://www.lfd.uci.edu/~gohlke/pythonlibs/#wxpython).

# How to synthesize your own dataset
## 3D modeling 
- Download Blender 2.80 or the newest version [here](https://www.blender.org/).
- Simulate your own scenario:<br>
Add objects based on your own real acoustic images, that is, you need to imitate your scene in blender layout. The reflection characteristics of materials, like diffuse reflection or specular reflection, of objects can be defined to achieve more abundant scenarios. With Blender's powerful GUI, a lot of scenes can be simulated easily.
- Modify the configuration of camera and objects to generate different images:<br>
You can do it in two ways: directly change the location or scale in **Layout**, or change the configuration by Python script in **Scripting** using:
```
# e.g.
camera.location.x = 0.01
camera.rotation_euler[0] = 0.01 * (math.pi / 180.0)
```
- Generate synthetic acoustic images: <br>
Use the Python script in this [.blend file](/assembly/marker_simulation.blend). **Remember to configure your Opencv and change the storage path for the results.** You can modify the range of last for-loop to change the number of the images you'd like.
- Others:<br>
Some tutorials that might be helpful:
[Blender Tutorials](https://www.youtube.com/channel/UCrXMyWVRmiXdMTpxxCsPuCQ/playlists), [blenderBinge](https://www.youtube.com/channel/UCrXMyWVRmiXdMTpxxCsPuCQ/playlists)

## CycleGAN training
- Download and configure CycleGAN implemented in Pytorch. Follow more detailed and intuitive tutorial [here](https://github.com/junyanz/pytorch-CycleGAN-and-pix2pix).
- Prepare the two train sets (trainA and trainB) for training:<br>
Conventionally put your target images in trainB, which means prepare synthetic acoustic images for trainA and some real acoustic images for trainB. Several hundreds would be enough in my experience.
- Train the network:<br>
Number of epoches depends on the complexity of the scenario in your images and the diversity of your datasets. Roughly it should be less than 80. Also, lambda_A and lambda_B can be finetuned to get more realistic results.
- Test and apply the model to more synthetic images to get your dataset.
## Tips for Python script
- Change the range of camera by modifying the variables `uplimit` and `lowlimit`.
- Images saved with prefix 'resize' are the resized rectangle images. You can adjust the scale by changing the parameters of `cv.resize()`. Raw fan-shaped acoustic images are also available.

# Related research and papers
1. Seungchul Kwak, Yonghoon Ji, Atsushi Yamashita, and Hajime Asama. Development of acoustic camera-imaging simulator based on novel model. In Proceedings of the IEEE 15th International Conference on Environment and Electrical Engineering, pages 1719–1724, 2015.
2. Romulo Cerqueira, Tiago Trocoli, Gustavo Neves, Sylvain Joyeux, Jan Albiez, and Luciano Oliveira. A novel gpu-based sonar simulator for real-time applications. Computers & Graphics, 68:66–76, 2017.
3. Ngoc Trung Mai, Yonghoon Ji, Hanwool Woo, Yusuke Tamura, Atsushi Yamashita, and Hajime Asama. Acoustic image simulator based on active sonar model in underwater environment. In Proceedings of the IEEE 15th International Conference on Ubiquitous Robots, pages 775–780, 2018.
4. Dingyu Liu, Yusheng Wang, Yonghoon Ji, Hiroshi Tsuchiya, Atsushi Yamashita, and Hajime Asama. CycleGAN-based Realistic Image Dataset Generation for Forward-looking Sonar. Advanced Robotics, 2020. (Under review)
