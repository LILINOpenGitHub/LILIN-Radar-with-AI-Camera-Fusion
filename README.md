# LILIN-Radar-with-AI-Camera-Fusion
LILIN Radar is able to fusion AI camera's video and metadata

#  Get recognition results
Get run-time recognition results.  Both HTTP based and websocket are supported.

Syntax: 
```
http://<serverIP:8592>/getalarmmotion
```

Syntax:
```
ws://<serverIP:8592>/getalarmmotion
```

Syntax:
```
curl --verbose --get --http0.9 --user "admin:Pass1234" http://192.168.0.200:8592/getalarmmotion
```

--myboundary
\r\n
Content-Length: <CLength>
\r\n
Content-Type: text/html; charset=utf-8
\r\n
\r\n
CamTime: <TimeStamp>\r\n
{
"AiEngine":<JSON>
"AiRadar":<JSON>
}


## AI Engine
Only filtered V3 radar points are included under the AI Engine cJSON section.
| Parameter	| Value  | Description | 
| --- |  --- |  --- | 
| CLength	| Integer| HTTP content length| 
| TimeStamp	| String | Date & time info, eg. 2019-09-27 00:53:48| 
| id | Integer | The object sequence of a frame |
| channel_id | Integer | The channel ID, fix to 1 if it is an IP camera |
| camera_name | String | The name of the camera |
| res_height | Integer | The canvas resolution in height of the bounding box drawing even the AI is in 4K recognition. |
| res_width | Integer | The canvas resolution in width of the bounding box drawing even the AI is in 4K recognition. |
| confidence | Integer | The confidence threshold of zone #1 |
| confidence2 | Integer | Reserve for future use |
| progress_bar | Integer | The setting writing progress when apply back to the camaera. |
| engine_type | Integer | The license type of the license key |
| label_name | String | The classified object name |
| class_id | Integer | The classified object ID |
| obj_type | String | Reserve for future use |
| obj_tracking_id | Integer | The tracking ID of a classified object |
| obj_dwell_time | Integer | The tracked object's time in second |
| color_id | Integer | The color ID, see [color table](https://github.com/LILINOpenGitHub/LILIN-Edge-Aida-Camera/blob/main/Color%20ID/ColorID.json) |
| color | String | The name of the color |
| PosX | Float | This represents the X position of the target in the radar coordinate system |
| PosY | Float | This represents the Y position of the target in the radar coordinate system |
| X | Integer | This represents the X position of the target in the image canvas |
| Y | Integer | This represents the Y position of the target in the image canvas |
| radar_tab_x | Integer | This represents the X coordinate position of the radar data on the user interface (e.g., map or radar chart) |
| radar_tab_y | Integer | This represents the Y coordinate position of the radar data on the user interface (e.g., map or radar chart) |
| obj_speed | Float | The speed of the object |
| parent_idx | Integer | This parameter represents the parent object index |
| isInsideZone_1 | Integer | Indicates if the radar point is displayed in zone 1 |
| isInsideZone_2 | Integer | Indicates if the radar point is displayed in zone 2 |
| isInsideZone_3 | Integer | Indicates if the radar point is displayed in zone 3 |
| isInsideZone_4 | Integer | Indicates if the radar point is displayed in zone 4 |
| isSpeedDetect_1 | Integer | Indicates if object speed detection is enabled in zone 1 |
| isSpeedDetect_2 | Integer | Indicates if object speed detection is enabled in zone 2 |
| isSpeedDetect_3 | Integer | Indicates if object speed detection is enabled in zone 3 |
| isSpeedDetect_4 | Integer | Indicates if object speed detection is enabled in zone 4 |
| detection_zone_id | Integer | zone # 1 ~ 4 |
| behavior_id | Integer | The behavior ID of an object in a zone, see [behavior table](https://github.com/LILINOpenGitHub/LILIN-Edge-Aida-Camera/blob/main/behaviorID/behaviorID.json) |



Other relevant information on the webpage
| Parameter	| Value  | Description | 
| --- |  --- |  --- | 
| counter_count | Array | An array indicating counts of different categories |
| something_vanish_in_zone1 | String | Indicates if something vanished in zone 1 |
| something_vanish_in_zone2 | String | Indicates if something vanished in zone 2 |
| something_vanish_in_zone3 | String | Indicates if something vanished in zone 3 |
| something_vanish_in_zone4 | String | Indicates if something vanished in zone 4 |
| Count	| Integer | The total count of objects detected |
| configdirty |	Integer | Configuration status flag |
| AI_fps | Integer | The zone show frames per second |
| ptz_p_degree | String | The PTZ camera pan degree |




## AiRadar
V1 to V3 radar points are included under the AI Engine cJSON section.
| Parameter	| Value  | Description | 
| --- |  --- |  --- | 
| Time | String | Radar data timestamp |
| FrameNum | String | Radar data frame number |
| ptz_p_degree | String | The PTZ camera pan degree |
| RadarArray | JSON Array |	Array of radar detection information |
├─ tid | String | Tracking ID of the radar object |
├─ Type	| String | Type of radar data (1 ~ 3 correspond to V1 to V3)  |
├─ PosX | String | This represents the X position of the target in the radar coordinate system |
├─ PosY | String | This represents the Y position of the target in the radar coordinate system |
├─ velX | String | X velocity of the object detected by radar |
├─ velY	| String | Y velocity of the object detected by radar |
├─ csX	| String |	Calibrated X position (reserved) |
├─ csY	| String |	Calibrated Y position (reserved) |
├─ Speed	| String |	Speed of the object detected by radar |
├─ world_radar_x	| String |	World coordinate X position of the radar object |
├─ world_radar_y	| String |	World coordinate Y position of the radar object |
├─ world_radar_x_scaled	| String |	Scaled world coordinate X position of the radar object |
└─ world_radar_y_scaled	| String |	Scaled world coordinate Y position of the radar object |
├─ plot	| String |	Indicates if the object should be plotted |
└─ class_id	| Integer |	Classification ID of the radar object |


Example: 
```
{
  "AiEngine": [
    {
      "id": 0,
      "channel_id": 1,
      "camera_name": "",
      "res_height": 600,
      "res_width": 800,
      "confidence": 80,
      "confidence2": 80,
      "progress_bar": 1,
      "engine_type": 4,
      "label_name": "person",
      "class_id": 0,
      "obj_type": 2,
      "obj_tracking_id": 1,
      "obj_dwell_time": 3,
      "color_id": 3,
      "color": "",
      "PosX": 0.36486899852752686,
      "PosY": 10.813270568847656,
      "x": 0,
      "y": 10,
      "radar_tab_x": 410,
      "radar_tab_y": 175,
      "obj_speed": 2.5,
      "parent_idx": 0,
      "isInsideZone_1": 0,
      "isInsideZone_2": 0,
      "isInsideZone_3": 0,
      "isInsideZone_4": 0,
      "isSpeedDetect_1": 0,
      "isSpeedDetect_2": 0,
      "isSpeedDetect_3": 0,
      "isSpeedDetect_4": 0,
      "detection_zone_id": 0,
      "behavior_id": 0
    }
  ],
  "counter_count": [0, 0, 0, 0, 0, 0, 0, 0],
  "something_vanish_in_zone1": "No",
  "something_vanish_in_zone2": "No",
  "something_vanish_in_zone3": "No",
  "something_vanish_in_zone4": "No",
  "Count": 1,
  "configdirty": 0,
  "AI_fps": 209,
  "ptz_p_degree": "0",
  "AiRadar": {
    "Time": "1720164926551",
    "FrameNum": "2134",
    "ptz_p_degree": "0",
    "RadarArray": [
      {
        "tid": "80",
        "Type": "3",
        "PosX": "0.364869",
        "PosY": "10.813271",
        "velX": "-0.232253",
        "velY": "0.702959",
        "csX": "0.000000",
        "csY": "0.000000",
        "Speed": "2.501018",
        "world_radar_x": "0",
        "world_radar_y": "10",
        "world_radar_x_scaled": "410",
        "world_radar_y_scaled": "175",
        "plot": "Yes",
        "class_id": -3
      }
    ]
  }
}
```
