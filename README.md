# HaarCascade
Opject detection with Haar Cascade classification with openCV
All files including training results as xml. 
The following stems needs to be taken assuming that opecv already is compiled
***
1. Create project folder to put everything there. There should be a sample image from the object and list of background images.
2. Create samples with opencv create samples:

>> opencv_createsamples -img home/.../pos_samp.jpg -bg home/.../temp/bg_data.txt -info info/info.lst -pngoutput home/.../info -maxxangle 0.5 -maxyangle 0.5 -maxzangle 0.5 -num 10

the following will appear:

Info file name: info/info.lst
Img file name: home/.../pos_samp.jpg
Vec file name: NULL
BG  file name: home/.../bg_data.txt
Num: 10
BG color: 0
BG threshold: 80
Invert: FALSE
Max intensity deviation: 40
Max x angle: 0.5
Max y angle: 0.5
Max z angle: 0.5
Show samples: FALSE
Width: 24
Height: 24
Max Scale: -1
RNG Seed: 12345
Create training samples from single image applying distortions...
Done

Then you should create .vec data for training cascade classifier
>> opencv_createsamples  -info info/info.lst  -w 24 -h 24  -vec posvec.vec -num 10
Info file name: info/info.lst
Img file name: (NULL)
Vec file name: posvec.vec
BG  file name: (NULL)
Num: 10
BG color: 0
BG threshold: 80
Invert: FALSE
Max intensity deviation: 40
Max x angle: 1.1
Max y angle: 1.1
Max z angle: 0.5
Show samples: FALSE
Width: 24
Height: 24
Max Scale: -1
RNG Seed: 12345

And finally training: I did the training for 10 stages:

>> opencv_traincascade -data data -vec positives.vec -bg bg_data.txt -numPos 1000  -numNeg 1500  -numStages 10 -w 20 -h 40
PARAMETERS:
cascadeDirName: data
vecFileName: positives.vec
bgFileName: bg_data.txt
numPos: 1000
numNeg: 1500
numStages: 10
precalcValBufSize[Mb] : 1024
precalcIdxBufSize[Mb] : 1024
acceptanceRatioBreakValue : -1
stageType: BOOST
featureType: HAAR
sampleWidth: 20
sampleHeight: 40
boostType: GAB
minHitRate: 0.995
maxFalseAlarmRate: 0.5
weightTrimRate: 0.95
maxDepth: 1
maxWeakCount: 100
mode: BASIC
Number of unique features given windowSize [20,40] : 312260

===== TRAINING 0-stage =====
<BEGIN
POS count : consumed   1000 : 1000
NEG count : acceptanceRatio    1500 : 1
Precalculation time: 7
+----+---------+---------+
|  N |    HR   |    FA   |
+----+---------+---------+
|   1|        1|        1|
+----+---------+---------+
|   2|        1|        1|
+----+---------+---------+
|   3|    0.996| 0.429333|
+----+---------+---------+
END>
Training until now has taken 0 days 0 hours 1 minutes 35 seconds.

===== TRAINING 1-stage =====
<BEGIN
POS count : consumed   1000 : 1004
NEG count : acceptanceRatio    1500 : 0.413451
Precalculation time: 8
+----+---------+---------+
|  N |    HR   |    FA   |
+----+---------+---------+
|   1|        1|        1|
+----+---------+---------+
|   2|        1|        1|
+----+---------+---------+
|   3|        1|        1|
+----+---------+---------+
|   4|    0.996| 0.625333|
+----+---------+---------+
|   5|    0.999| 0.784667|
+----+---------+---------+
|   6|    0.996| 0.383333|
+----+---------+---------+
END>
Training until now has taken 0 days 0 hours 4 minutes 44 seconds.

===== TRAINING 2-stage =====
<BEGIN
POS count : consumed   1000 : 1008
NEG count : acceptanceRatio    1500 : 0.181466
Precalculation time: 9
+----+---------+---------+
|  N |    HR   |    FA   |
+----+---------+---------+
|   1|        1|        1|
+----+---------+---------+
|   2|        1|        1|
+----+---------+---------+
|   3|        1|        1|
+----+---------+---------+
|   4|        1|        1|
+----+---------+---------+
|   5|    0.999| 0.682667|
+----+---------+---------+
|   6|    0.999|    0.516|
+----+---------+---------+
|   7|    0.998| 0.366667|
+----+---------+---------+
END>
Training until now has taken 0 days 0 hours 8 minutes 27 seconds.

===== TRAINING 3-stage =====
<BEGIN
POS count : consumed   1000 : 1010
NEG count : acceptanceRatio    1500 : 0.0703697
Precalculation time: 9
+----+---------+---------+
|  N |    HR   |    FA   |
+----+---------+---------+
|   1|        1|        1|
+----+---------+---------+
|   2|        1|        1|
+----+---------+---------+
|   3|        1|        1|
+----+---------+---------+
|   4|        1|        1|
+----+---------+---------+
|   5|    0.999| 0.732667|
+----+---------+---------+
|   6|    0.999| 0.643333|
+----+---------+---------+
|   7|    0.998| 0.497333|
+----+---------+---------+
END>
Training until now has taken 0 days 0 hours 12 minutes 9 seconds.

===== TRAINING 4-stage =====
<BEGIN
POS count : consumed   1000 : 1012
NEG count : acceptanceRatio    1500 : 0.0411455
Precalculation time: 10
+----+---------+---------+
|  N |    HR   |    FA   |
+----+---------+---------+
|   1|        1|        1|
+----+---------+---------+
|   2|        1|        1|
+----+---------+---------+
|   3|        1|        1|
+----+---------+---------+
|   4|        1|        1|
+----+---------+---------+
|   5|        1|        1|
+----+---------+---------+
|   6|        1| 0.915333|
+----+---------+---------+
|   7|    0.996|    0.636|
+----+---------+---------+
|   8|        1| 0.677333|
+----+---------+---------+
|   9|        1|    0.706|
+----+---------+---------+
|  10|    0.998| 0.538667|
+----+---------+---------+
|  11|    0.996| 0.311333|
+----+---------+---------+
END>
Training until now has taken 0 days 0 hours 17 minutes 41 seconds.

===== TRAINING 5-stage =====
<BEGIN
POS count : consumed   1000 : 1016
NEG count : acceptanceRatio    1500 : 0.012379
Precalculation time: 9
+----+---------+---------+
|  N |    HR   |    FA   |
+----+---------+---------+
|   1|        1|        1|
+----+---------+---------+
|   2|        1|        1|
+----+---------+---------+
|   3|        1|        1|
+----+---------+---------+
|   4|    0.996| 0.784667|
+----+---------+---------+
|   5|    0.996| 0.784667|
+----+---------+---------+
|   6|    0.999|    0.772|
+----+---------+---------+
|   7|        1|     0.81|
+----+---------+---------+
|   8|    0.996| 0.524667|
+----+---------+---------+
|   9|    0.997| 0.488667|
+----+---------+---------+
END>
Training until now has taken 0 days 0 hours 22 minutes 20 seconds.

===== TRAINING 6-stage =====
<BEGIN
POS count : consumed   1000 : 1019
NEG count : acceptanceRatio    1500 : 0.00679003
Precalculation time: 10
+----+---------+---------+
|  N |    HR   |    FA   |
+----+---------+---------+
|   1|        1|        1|
+----+---------+---------+
|   2|        1|        1|
+----+---------+---------+
|   3|        1|        1|
+----+---------+---------+
|   4|        1|        1|
+----+---------+---------+
|   5|        1|        1|
+----+---------+---------+
|   6|        1|        1|
+----+---------+---------+
|   7|    0.998| 0.612667|
+----+---------+---------+
|   8|    0.998| 0.612667|
+----+---------+---------+
|   9|    0.996|    0.458|
+----+---------+---------+
END>
Training until now has taken 0 days 0 hours 26 minutes 34 seconds.

===== TRAINING 7-stage =====
<BEGIN
POS count : consumed   1000 : 1024
NEG count : acceptanceRatio    1500 : 0.00354793
Precalculation time: 9
+----+---------+---------+
|  N |    HR   |    FA   |
+----+---------+---------+
|   1|        1|        1|
+----+---------+---------+
|   2|        1|        1|
+----+---------+---------+
|   3|        1|        1|
+----+---------+---------+
|   4|        1|        1|
+----+---------+---------+
|   5|    0.999| 0.785333|
+----+---------+---------+
|   6|    0.997|     0.67|
+----+---------+---------+
|   7|    0.998| 0.708667|
+----+---------+---------+
|   8|    0.997| 0.712667|
+----+---------+---------+
|   9|    0.998| 0.749333|
+----+---------+---------+
|  10|    0.997|     0.57|
+----+---------+---------+
|  11|    0.997|    0.474|
+----+---------+---------+
END>
Training until now has taken 0 days 0 hours 31 minutes 35 seconds.

===== TRAINING 8-stage =====
<BEGIN
POS count : consumed   1000 : 1027
NEG count : acceptanceRatio    1500 : 0.00300994
Precalculation time: 9
+----+---------+---------+
|  N |    HR   |    FA   |
+----+---------+---------+
|   1|        1|        1|
+----+---------+---------+
|   2|        1|        1|
+----+---------+---------+
|   3|        1|        1|
+----+---------+---------+
|   4|    0.996| 0.666667|
+----+---------+---------+
|   5|    0.996| 0.666667|
+----+---------+---------+
|   6|    0.997|     0.61|
+----+---------+---------+
|   7|        1|    0.614|
+----+---------+---------+
|   8|    0.998| 0.444667|
+----+---------+---------+
END>
Training until now has taken 0 days 0 hours 35 minutes 12 seconds.

===== TRAINING 9-stage =====
<BEGIN
POS count : consumed   1000 : 1029
NEG count : acceptanceRatio    1500 : 0.00238494
Precalculation time: 10
+----+---------+---------+
|  N |    HR   |    FA   |
+----+---------+---------+
|   1|        1|        1|
+----+---------+---------+
|   2|        1|        1|
+----+---------+---------+
|   3|        1|        1|
+----+---------+---------+
|   4|        1|        1|
+----+---------+---------+
|   5|        1|        1|
+----+---------+---------+
|   6|        1|        1|
+----+---------+---------+
|   7|    0.999| 0.617333|
+----+---------+---------+
|   8|    0.998|    0.548|
+----+---------+---------+
|   9|    0.998| 0.434667|
+----+---------+---------+
END>
Training until now has taken 0 days 0 hours 39 minutes 26 seconds.


