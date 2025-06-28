# Soccer Player Reidentification
## Task - 
Given a 15-second video **(15sec_input_720p .mp4)**, identify each player and ensure that
players who go out of frame and reappear are assigned the same identity as before.<br>
## Model used for Detection - 
https://drive.google.com/file/d/1-5fOSHOSB9UXyP_enOoZNAMScrePVcMD/view <br>
The model is a basic fine-tuned version of **Ultralvtics YOLOv11**, trained for players and the ball.<br>
## Tracking - 
I used Byte Tracker for detecting the objects in the frames and the corresponding bounding Box.<br>
Stored all the detection and infomation in the **track_players.pkl** <br><br>
Drawing annotations on each player and the ball for better visualisation.<br><br>
![Screenshot 2025-06-28 154611](https://github.com/user-attachments/assets/d88b60b5-2e01-4c0f-96ca-b632e6395827) <br>
## Re-Identification - 
As the players  continoulsy leaving and entering the frames . So, for assigning continous id's to players we have to compare players based on their visual features. <br><br>
1) Step first is to extract the cropped images of all players in each frame.<br>
![player_11](https://github.com/user-attachments/assets/a5cde57d-645c-4966-8b61-4fc356a7bde2)<br>
I have extracted it in the **players_crops_images.zip** file where there are 375 frame folders each has cropped images of the players present in that frame.<br><br>
### Re-Identification Model
I used the **clip ViT-B/32 model** for Feature extraction given the image of players and then use the **cosine similarity function** to check whether two players are same or not.<br><br>
Storing the updated tracking inofrmation in the **updated_track_id.pkl** and features informtion in the **reid.pkl file**.
## Output 
Finally using the updated tracking information to produce the final output video. You can see it as **output_video.avi** .<br><br>
![Screenshot 2025-06-28 160138](https://github.com/user-attachments/assets/959ef1ab-a0a9-452f-8cd0-164412882dea)
## Alternate ideas or Approaches -
Some alternatives which I tried is first using a different feature extracting module like **torchreid OS_Net**.<br>
Also, KMeans clustering can also be used to extract only important features like only pixels corresponding to skin or face. I have attached a file which show how it can be done that is 
**Extract_features_kmeans.ipynb**. <br>
Visual Example <br><br>
![Screenshot 2025-06-28 160928](https://github.com/user-attachments/assets/790c183d-6559-4f6d-9caa-85a5c0b966c1)<br><br>
## Dependencies
```bash
pip install ultralytics supervision opencv-python pandas numpy scikit-learn torchreid torch git+https://github.com/openai/CLIP.git
```

## Final Words
Run the **soccer-player-identitification.ipynb** for your input to get the output
I have done everthing in kaggle environment for faster and efficient prodcution. <br><br>
I have written all the codes in a very simple, intuitive and structured way. 



