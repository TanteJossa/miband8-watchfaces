# miband8-watchfaces
mi ;) exploration in creating watch faces for the mi band


steps
1. read instructions (https://www.bandbbs.cn/threads/7188/#post-346061)
```
Foreword: Due to personal reasons, and I thought it was unnecessary (lazy ) before , it caused me to dove for a while (, because many people needed it, I made an article.
Note: This tutorial is only based on Mi Band 8 as an example, other tools supported by this tool You can also refer to the model of the model; some content may be incomplete, and it will be updated slowly later.
Thanks to @huangtao1189 for pointing out an animation error
and put a sample dial, you can refer to it
1. Download and configuration: (Skip if already downloaded)

1.1: Download
First, click this link to download, or go to the corresponding section and set it to the top to download. After decompression, you can get this file 1686503509617.png
1.2: Configure the application
Right-click "EasyFace.exe", click Properties, find compatibility at the top, check "Run this program as an administrator", and then click "Apply".
1686503848984.png





2. Create a new project file and place image resources
2.1: The initial opening of the new project file
is like this (may not be the same as yours, I adjusted the position),1686504375874.png
At this time, click the first icon in the upper left corner to create a new project.
1686504739451.png
A box pops up, fill in the information and select Mi Band 8 for the bracelet type to confirm.
1686504886630.png
Then the following content is generated inside the folder:
1686505001152.png
/examples
---images
---output
---examples.fprj
images: Store image resources (png); just place images, please do not put other files (such as psd, txt), etc., and do not create folders inside.
output: output folder, used to store output files.
Example.fprj: project file, used to save the project.

2.2: Import image resources
Just put in the png file for production, and the software will display it. (No need to create folders inside)




3. Production - Main Body
3.1: Basemap (Background)
Click "Toolbox-Basic Controls-Picture", draw one casually, and change "x, y" to "0, 0", as shown in the figure.
1686506214531.png
Then drag the picture from the "Picture Browser" to the "Properties-Picture" column.
1686506484798.png

3.2: Time
to click "Toolbox-Basic Controls-General Digital Display", draw a suitable size, drag the picture from "Picture Viewer" to the "Properties-Digital Picture List" column (numbers 0~symbols must be dragged in) ), after which the controls can be displayed. Then copy this control and paste a total of 4 controls (why 4 will be explained later).
PS: For 8Pro, please directly use the data source of hours and minutes, because the mechanism is different from 8Pro, and the gray words at the bottom are written for 8 users.

! ! ! Note that each individual control (such as picture list, number list) can only use one set of pictures and cannot be reused. Four controls correspond to four sets of pictures to be copied. ! ! !

Modify the corresponding picture of the pasted control, add the data source as "hour-tens", "hour-one", "minute-ten", "minute-one", and then modify the xy position. Can.
The effect is as shown in the figure

1686506979980.png1686508068941.png
PS: Why not just use "hour" and "minute"? The reason is because this data source is for the pointer dial, not simply 0 to 24, because when applied to the pointer, the hour will move a little bit according to the minute, not directly from 11 to 12. This value is estimated to have a decimal point, so after 30 minutes, 23.6 and then displayed on the digital component will be 10% 24. (Written for 8)

3.3: The date
is the same as the time, just change the data source to date and adjust the number of digits to 2.1686508695083.png

3.4:
Click "Toolbox-Basic Controls-Picture List", draw a suitable size, adjust the default index value to 0, and the number to 7, drag the picture from "Picture Viewer" to "Properties-Picture List-Name" One column; then set the index value, the index value corresponding to Sunday is 0, and the index value is 1~6 from Monday to Saturday. After filling in, set the data source to "week".
1686509331618.png

3.5: The number of steps, heart rate, calories, power
is the same as the time setting here, just change the data source to the corresponding, change the number of digits, and adjust the details as needed.
Note: If you do not want to display the 0 in front of the number, you can turn on the high-order blanking.
1686509782947.png

3.6 :
Click on "Toolbox-Basic Controls-Picture List" to draw a suitable size. The default index value is adjusted to 10, and the quantity is 10. Drag and drop pictures from "Picture View" to "Properties-Picture List" -Name" column; then set the index value, if the first picture wants to switch when the power is XX, just fill in XX for the index value, and then fill it in order.
1686510214519.png

3.7: High Blanking
If you want the number to display 1 instead of 001, just turn on "Properties - High Blanking".
1686510455465.png



3.8: Picture
Click "Toolbox-Basic Controls-Picture", draw a suitable size, and then drag the picture from "Picture Browse" to the "Properties-Picture" column.
Note: If the picture is transparent, please fill in _RGBA in the control name.
1686510716660.png
3.9: Bluetooth, Do Not Disturb, Lock
Click "Toolbox-Basic Controls-Picture List", draw a suitable size, the default index value is adjusted to 0, and the number is 2; then fill in the index value, 0 means off, 1 means on, According to this idea, you can make it and select the corresponding data source.
1686511044899.png

3.10: Animation (Xiaomi Mi Band 8 does not currently support it)
Click "Toolbox-Basic Controls-Picture List", draw a suitable size, and then name it asanim_[xx@yy]
xx: number of runs, 0 - infinite
yy: time frame, unit: milliseconds (ms), the smaller the number, the faster the picture moves
If you use an image with a transparent background, add _RGBA to the name suffix, and fill in the index from 0.
1686583470623.png1686583477747.png

3.11: Jumpable components (not supported by Mi Band 8 and 8Pro),
please update the version to V30.
Click "Toolbox-Basic Controls-Picture", draw an appropriate size; set the name tobtn_[XXXXX], if the picture has a transparent background, add a suffix_RGBA(egbtn_[XXXXX]_RGBA).
If I want to set the jump to the heart rate, thenreplace withbtn_[XXXXX]_RGBA,the effect is as follows. Other component IDs are as follows:XXXXXhrmbtn_[hrm]_RGBA

Steps: steps
Calories: calories
Standing: standing
Activity: moving
Heart rate: hrm
blood oxygen: spo2
pressure: stress
weather: weather
alarm clock: alarm
music: music
Click to expand...

4. Make-AOD
It is currently known that Xiaomi Mi Band 8 must make AOD, otherwise it will switch to the system default dial and
create a new dial, named AOD, and save it in the same directory as the project file.
Afterwards, the manufacturing method is the same as that of the main body of the dial.
Screenshot_20230613-183434_Sunflower remote control.png

After the production is completed, there is no need to compile, just save it and return to the main project file of the dial.
Screenshot_20230613-183531_Sunflower remote control.png


5. Compile the dial
5.1: Improve the dial information
, click on the blank part, fill in the name and select the preview image.
Note: The preview image of Mihuan 8 needs to be 122*310, and 7Pro is 220*358; and the rounded corners should be cut.
1686511580189.png

5.2:
Click the icon in the upper left corner of the compile dial to start compiling.
1686511668685.png
If these two items are displayed, it means the compilation is successful
1686511790383.png
output to \example\example\output
1686512069197.png
The suffix .face is the compiled product, which can be directly brushed into
the end

Frequently Asked Questions:
Q: The background of the picture is not transparent
A: Add _RGBA to the control name.

Q: The pictures are garbled, and the packaging always fails.
A: Please check whether the pictures in this picture list are of the same size! ! ! Different sizes of pictures in the same picture collection may cause garbled characters, or lead to entering the after-sales mode! ! ! Q: Other questions A: Follow-up supplement. ```
