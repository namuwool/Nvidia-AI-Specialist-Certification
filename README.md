# Nvidia-AI-Specialist-Certification
Nvidia AI Specialist Certification

[ Title ]
---
Screw Collection and Classification for Construction Site Safety



Opening background information 
---
<aside>
✅ Small screws left unattended at construction sites pose a threat to machinery and worker safety, yet they are not easy to locate instantly. Currently, magnetic screwdrivers are used to prevent screw loss, but this approach has its limitations. To address these issues, an AI-based system capable of detecting and classifying screws is needed.

</aside>


General description of the current project
---
<aside>
✅ This project aims to develop an AI-based screw recognition system to easily collect screws dropped at construction sites. It detects screws that fall or roll on the ground in real-time, preventing them from entering construction machinery or being overlooked by workers. Through this, the project seeks to enhance safety and improve work efficiency at construction sites.

</aside>


Current limitations
---
<aside>
✅ There are many types of screws, so it takes a long time to train the system to recognize various kinds of screws. Additionally, the high density of objects at construction sites can cause occlusion depending on the environment, making it difficult to detect screws.

</aside>


Video Acquisition Method
---
- Various scenarios involving screws were staged and recorded, and validation was conducted by capturing situations where screws are present, rolling, or falling.

Training Video

https://youtube.com/shorts/WhT_FwY1m-Y?si=SQdWaKTVuG8Js5Oj

Validation Video

https://youtube.com/shorts/yhTtwcewjIc?si=bqMym3mMx-cj1yns

https://youtube.com/shorts/VWcLRW8vs0U?si=X9I6Jk7PkDOSeuwt

https://youtube.com/shorts/HcVqAKxXZP4?si=uQYc4MzfyEvo8hgA


[ Project Progress ]
---

**1. Image extraction**
---
**Use Adobe Express to resize the video to 640 x 640.**


https://new.express.adobe.com/tools/resize-video?url=%2Fkr%2Fexpress%2Ffeature%2Fvideo%2Fresize&placement=columns-1&locale=ko-KR&contentRegion=kr&%24web_only=true&_branch_match_id=1383263338796486643&_branch_referrer=H4sIAAAAAAAAAw2JsQrCMBgGn8ZsbVFwUAgOgiguWhDcJEm%2FtiFp%2FvAnteLgs5vl7uDGnGPaN43qSCNFxS5SytUCXasYa2%2BDa9A8d4%2Fb3ejL9qwPM3u52pwcF%2BATGSmV6qHyzCj1th2ouAz7hYheGUwIWRry8xRStRaejPKQjqprKwyFXHaLwVKQjsWP0YPZhuGlmZYElseRacIfzIRSeqwAAAA%3D

![image](https://github.com/user-attachments/assets/6c5912e6-de3d-438d-b7fa-f093be76cdfc)

<p align="center"><img src="https://github.com/user-attachments/assets/83fc166f-b2db-4931-a947-735178194483" width="400" height="450"/> <img src="https://github.com/user-attachments/assets/c5eda0d6-8e9f-4c9c-9df7-28410481d415" width="400" height="450"/> 


**2. DarkLabel (labels)**
---
• **Go to the DarkLabel.exe file**

![image (3)](https://github.com/user-attachments/assets/9f0e739e-a6e7-4d65-9bf4-1f8239e4f7b5)

Click on "Open Video" to select the video for training.

<p align="center"><img src="https://github.com/user-attachments/assets/4b26f9fc-6033-42a9-89e3-b291705af324">
  
<p align="center"><img src="https://github.com/user-attachments/assets/b8fe3f56-a170-4004-891f-afc11f1997a1"> <img src="https://github.com/user-attachments/assets/6613e7a7-92e3-470f-9151-4f59b2df3343">


Ensure that it is set to "screw," then set it to "box + Label," uncheck "labeled frames only," and proceed with labeling


<p align="center"><img src="https://github.com/user-attachments/assets/507ab6d1-df98-48ba-96bb-0134ac8658a0"> <img src="https://github.com/user-attachments/assets/ff9bfd3a-e3e7-407f-af57-c998ddea279a"width="500" height="600"/>

After completing the labeling, click the "GT SAVE AS" button, select a folder, and save. You can then confirm that the labels are saved in a .txt file format.



<p align="center"><img src="https://github.com/user-attachments/assets/620948c9-b4c0-476f-bcf2-49dbb1e887ab" height="300"/> <img src="https://github.com/user-attachments/assets/104d8659-13c8-4ec4-9d96-292a389a95f3" width="400" height="300"/>

Check extracted labeling

<p align="center"><img src="https://github.com/user-attachments/assets/e3ef4f91-ee92-4ce6-95c4-bca1b751a5e6" width="600"/>

**3. Learning data with yolov5 colab**
---
• Link your Google Drive to Colab

![image (12)](https://github.com/user-attachments/assets/fda80d63-e523-4bdc-95eb-b8db5dfdb06d)

• Clone and install the yolov5 repertoire.

![image (13)](https://github.com/user-attachments/assets/9c556329-55a8-48a5-be7d-94d091d5ed8d)

• Creating Validation Data

![image (14)](https://github.com/user-attachments/assets/54e9379d-8314-4706-b2c4-d8d100c68b0c)


Creates `images` and `labels` directories inside `val_path`.

With `exist_ok=True`, no error is raised if the directories already exist.

Fetches the list of image files from `train_path/images`.

Uses `train_test_split` to divide the data into Validation data at a specified ratio (`split_ratio`).

**Image file copying**: Copies the selected Validation image files to `val_path/images`.

**Label file copying**: Copies the corresponding `.txt` label files to `val_path/labels`.

Only copies label files if they exist (`if os.path.exists`).


**4. Model Learning**
---

![image (15)](https://github.com/user-attachments/assets/c9195a2e-6253-4129-b0f6-7730c73c1ebf)

