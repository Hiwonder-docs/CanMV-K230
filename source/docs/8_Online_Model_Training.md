# 8. Online Model Training

<p id="anther_8_1"></p>
## 8.1 Training Data Preparation

The [**7. Touch Control Course - Touch Photography**](https://docs.hiwonder.com/projects/CanMV-K230/en/latest/docs/7_Touch_Control_Course.html#touch-photography) routine is utilized to collect the corresponding dataset. Refer to the 7.3 Touch Photography section of the **7. Touch Control Course** for specific procedures on capturing and saving the dataset images.

## 8.2 Online Training Platform Registration

Online training model address: https://www.kendryte.com/zh/training/dataset

1.  Click the `X` button to cancel login.

<img class="common_img" src="../_static/media/chapter_9/section_1/media/image30.png" width="600px"/>

2.  Click the top right corner to switch to English.

<img class="common_img" src="../_static/media/chapter_9/section_1/media/image31.png" width="600px"/>

3.  After switching, click the **Sign in** or **Sign up** option in the top right corner.

<img class="common_img" src="../_static/media/chapter_9/section_1/media/image32.png" width="600px"/>

4.  Accessing the KENDRYTE allows for either registration or login, and registration is demonstrated here as an example.

<img class="common_img" src="../_static/media/chapter_9/section_1/media/image2.png" width="600px"/>

5.  Click the **Register** button to begin registration.

<img class="common_img" src="../_static/media/chapter_9/section_1/media/image3.png" width="600px"/>

6.  Fill in the corresponding personal information and click **Register**.

<img class="common_img" src="../_static/media/chapter_9/section_1/media/image4.png" width="600px"/>

## 8.3 Initiating Online Model Training

1.   After successful registration, the account logs in automatically and then clicks **Create Dataset** on the right.

<img class="common_img" src="../_static/media/chapter_9/section_1/media/image5.png" width="600px"/>

2.   Taking `Image Detection` as an example to create a dataset, enter the dataset name and select the corresponding recognition and annotation types.

<img class="common_img" src="../_static/media/chapter_9/section_1/media/image6.png" width="600px"/>

3.   Click the **Configuration** button in the top-right corner.

<img class="common_img" src="../_static/media/chapter_9/section_1/media/image7.png" width="600px"/>

4.   Click the `Upload Image` button to upload the corresponding dataset to the cloud platform.

<img class="common_img" src="../_static/media/chapter_9/section_1/media/image8.png" width="600px"/>

5.   Upload the prepared dataset to the model training cloud platform.

<img class="common_img" src="../_static/media/chapter_9/section_1/media/image9.png" width="600px"/>

6.   Click the **Annotate** button after the image upload is complete.

<img class="common_img" src="../_static/media/chapter_9/section_1/media/image10.png" width="600px"/>

7.   Click `New Tag` to add labels for the corresponding categories.

<img class="common_img" src="../_static/media/chapter_9/section_1/media/image11.png" width="600px"/>

8.   Add `green`, `red`, and `yellow` labels for traffic light recognition.

<img class="common_img" src="../_static/media/chapter_9/section_1/media/image12.png" width="600px"/>

9.   Select the corresponding color tag, using green as an example, and drag the mouse to annotate the target object.

<img class="common_img" src="../_static/media/chapter_9/section_1/media/image13.png" width="600px"/>

10.   Apply corresponding annotations to all images.

<img class="common_img" src="../_static/media/chapter_9/section_1/media/image14.png" width="600px"/>

11.   Click the return button upon completion of all annotations.

<img class="common_img" src="../_static/media/chapter_9/section_1/media/image15.png" width="600px"/>

12.   Next, click the **Train** button to start model training.

<img class="common_img" src="../_static/media/chapter_9/section_1/media/image16.png" width="600px"/>

13.   Fill in the corresponding training parameters.

```
* Platform: Select K230
* nncase Version: The latest version is selected.
* Iterations: This value is adjusted based on the dataset, typically set around 200. The system automatically ceases training when the loss remains stable, and change < 0.05 for 30~50 consecutive epochs.
* Batch Size: Select 8.
* Learning Rate: Enter 0.001.
* Label Box Limit: Enter 5, which indicates the maximum number of target boxes allowed per image.
```

<img class="common_img" src="../_static/media/chapter_9/section_1/media/image17.png" width="400px" width="500px"/>

14.   Click **Confirm** to automatically redirect to the training interface and wait for the training. Note that queuing may be required during busy periods.

<img class="common_img" src="../_static/media/chapter_9/section_1/media/image18.png" width="600px"/>

15.   As training occurs in the cloud, the webpage or browser may be closed without affecting the process.

<img class="common_img" src="../_static/media/chapter_9/section_1/media/image19.png" width="600px"/>

16.   During the process, hover the mouse over the training result chart to view real-time loss data.

<img class="common_img" src="../_static/media/chapter_9/section_1/media/image21.png" width="600px"/>

17.   Upon training completion, the registered email address receives a notification indicating the end of model training.

<img class="common_img" src="../_static/media/chapter_9/section_1/media/image20.png" width="600px"/>



## 8.4 Model Download and Deployment

1.   First, click `Records` on the left, then click `Download` on the right to save the trained model and deployment materials locally.

<img class="common_img" src="../_static/media/chapter_9/section_1/media/image22.png" width="600px"/>

2.   Extract the downloaded compressed package locally.

<img class="common_img" src="../_static/media/chapter_9/section_1/media/image23.png" width="600px"/>

3.  The detailed directory structure of the archive is as follows.

   ```
   **_image_1_2_2.py # 1.2.2 firmware image inference script, full code
   **_video_1_2_2.py # 1.2.2 firmware video inference script, full code
   **_image_1_3.py # 1.3 firmware image inference script, highly encapsulated
   **_video_1_3.py # 1.3 firmware video inference script, highly encapsulated
   README.pdf # Official tutorial document
   det_results # Verification test results
   mp_deployment_source # micropython deployment resource directory
   |- *.kmodel # kmodel file
   |- deploy_config.json # Deployment configuration file
   ```

4.  Extract the downloaded archive to a local directory. Focus exclusively on the sample program, as well as the model and configuration files located within the `mp_deployment_source` directory.

<img class="common_img" src="../_static/media/chapter_9/section_1/media/image24.png" width="600px"/>

5.   Copy the entire `mp_deployment_source` folder to the `This PC\CanMV\sdcard` directory on the K230 development board SD card.

<img class="common_img" src="../_static/media/chapter_9/section_1/media/image25.png" width="600px"/>

6.   Using the video inference program as an example, drag the decompressed `det_image_1_2_2.py` into the CanMV IDE.

<img class="common_img" src="../_static/media/chapter_9/section_1/media/image26.png" width="600px"/>

7.   The program requires minor modification regarding the corresponding path.

<img class="common_img" src="../_static/media/chapter_9/section_1/media/image27.png" width="600px"/>

Slightly modify the import path in the `det_image_1_2_2.py` program.

Original program:

 ```python
root_path = "/sdcard/mp_deployment_source/"
 config_path = root_path + "deploy_config.json"
deploy_conf = {}
 debug_mode = 1
 ```

 Modified to:

 ```py
root_path = "/sdcard/mp_deployment_source/"
 config_path = "/sdcard/mp_deployment_source/deploy_config.json"
deploy_conf = {}
 debug_mode = 1
 ```

8.   The display mode can also be selected.

<img class="common_img" src="../_static/media/chapter_9/section_1/media/image28.png" width="600px"/>

Select the display mode by slightly modifying the display section of the `det_image_1_2_2.py` program.

 LCD display mode:

 ```py
 display_mode = "lcd"
 if display_mode == "lcd":
     DISPLAY_WIDTH = ALIGN_UP(800, 16)
     DISPLAY_HEIGHT = 480
 else:
     DISPLAY_WIDTH = ALIGN_UP(1920, 16)
     DISPLAY_HEIGHT = 1080
 OUT_RGB888P_WIDTH = ALIGN_UP(640, 16)
 OUT_RGB888P_HEIGH = 360
 ```

HDMI display mode:

```py
 display_mode = "hdmi"
 if display_mode == "lcd":
  DISPLAY_WIDTH = ALIGN_UP(800, 16)
     DISPLAY_HEIGHT = 480
    else:
  DISPLAY_WIDTH = ALIGN_UP(1920, 16)
     DISPLAY_HEIGHT = 1080
    OUT_RGB888P_WIDTH = ALIGN_UP(640, 16)
 OUT_RGB888P_HEIGH = 360
```

9.   The achieved effect is shown in the figure below.

<img class="common_img" src="../_static/media/chapter_9/section_1/media/image29.png" width="600px"/>
