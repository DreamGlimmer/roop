Take a video and replace the face in it with a face of your choice. You only need one image of the desired face. No dataset, no training.

That's it, that's the software. You can watch some demos [here](https://drive.google.com/drive/folders/1KHv8n_rd3Lcr2v7jBq1yPSTWM554Gq8e?usp=sharing).

![demo-gif](demo.gif)

## Installation
> Do not create any issues regarding installation problems. I am only responsible for issues in this program, use google for help.

1. install `python`, `pip` and `git`
2. install `ffmpeg`
3. run the following commands in terminal:
```
git clone https://github.com/s0md3v/roop
cd roop
pip install -r requirements.txt
```
4. Download [this file](https://1drv.ms/u/s!AsHA3Xbnj6uAgxhb_tmQ7egHACOR?e=CPoThO) and keep it in **roop** directory

### GPU Accleration (Optional)
If you have a good enough GPU, you can use it to speed-up the face-swapping process by running `run.py` with `--gpu` flag.
If you plan on doing it, you will need to install the appropriate `onnxruntime-*` package as follows:

#### NVIDIA
Install `cuda` and then,
```
pip install onnxruntime-gpu
```
#### AMD
Install ROCM-based torch packages from [here](https://pytorch.org/get-started/locally/) and then,

```
git clone https://github.com/microsoft/onnxruntime
cd onnxruntime
./build.sh --config Release --build_wheel --update --build --parallel --cmake_extra_defines CMAKE_PREFIX_PATH=/opt/rocm/lib/cmake ONNXRUNTIME_VERSION=$ONNXRUNTIME_VERSION onnxruntime_BUILD_UNIT_TESTS=off --use_rocm --rocm_home=/opt/rocm
pip install build/Linux/Release/dist/*.whl
```

## Usage
> Note: When you run this program for the first time, it will download some models ~300MB in size.

Executing `python run.py` command will launch this window:
![gui-demo](gui-demo.png)

Choose a face (image with desired face) and the target image/video (image/video in which you want to replace the face) and click on `Start`. Open file explorer and navigate to the directory you launched `run.py` from. You will find a directory named `<video_title>` where you can see the frames being swapped in realtime. Once the processing is done, it will create a video file named `swapped-<video_title>.mp4`. That's it.

Don't touch the FPS checkbox unless you know what you are doing.

Additional command line arguments are given below:
```
-h, --help            show this help message and exit
-f SOURCE_IMG, --face SOURCE_IMG
                        use this face
-t TARGET_PATH, --target TARGET_PATH
                        replace this face
--keep-fps            keep original fps
--gpu                 use gpu
--keep-frames         don't delete frames directory
```

Looking for a CLI mode? Using the -f/--face argument will make the program in cli mode.

## Future plans
- [ ] Replace a selective face throughout the video
- [ ] Support for replacing multiple faces

## Credits
- [ffmpeg](https://ffmpeg.org/): for making video related operations easy
- [deepinsight](https://github.com/deepinsight): for their [insightface](https://github.com/deepinsight/insightface) project which provided a well-made library and models.
- and all developers behind libraries used in this project.
