# R3-Driving-Dataset


**R3 Driving Dataset** is the dataset of the following paper:

**Towards Defensive Autonomous Driving: Collecting and Probing Driving Demonstration of Mixed Qualities.** 

*Jeongwoo Oh*<sup>1</sup>\*, *Gunmin Lee*<sup>1</sup>\*, *Jeongeun Park<sup>2</sup>, Wooseok Oh<sup>1</sup>, Jaeseok Heo<sup>1</sup>, Hojun Chung<sup>3</sup>, Do Hyung Kim<sup>4</sup>, Byungkyu Park<sup>4</sup>, Chang-Gun Lee<sup>4</sup>, Sungjoon Choi<sup>2</sup>, Songhwai Oh<sup>1</sup>*

RLLAB, Seoul National Univ.<sup>1</sup>  
RiLAB, Korea Univ. <sup>2</sup>   
Department of Mechnical Engineering, Seoul National Univ. <sup>3</sup>   
RUBIS, Seoul National Univ. <sup>4</sup>  

![demo_video](./figure/demo_video.gif)


## Download

you can only download data files of **R3 Driving Dataset** from this repository.  
If you want to download full version of the dataset, please contact to the following e-mail address with some information.  
The information must be contained ***name, organization, purpose of use***.  
e-mail: ***jeongwoo.oh@rllab.snu.ac.kr***

## Data Structure

The following image denotes the data structure of **R3 Driving Dataset**.  

![data_structure](./figure/data_structure.png)  

The summary files contain the following attributes:  
- **data_type**: this attribute denotes the type of scenario, all of scenarios are categorized expert or abnormal.  
- **location**: Only expert scenarios contain this attribute. We divide location type into 3 categories in all of expert scenarios: highway, urban_road, and FMTC.  
- **road**: Only abnormal scenarios contain this attribute. We divide road type into 2 categories in all of abnormal scenarios: straight road, and crossroad.  
- **hazard**: only abnormal scenarios contain this attribute. This attribute denotes what hazard types are included in this scenario. We divide hazard type into 5 categories: unstable_driving, failing_lane_keeping, dangerous_lane_changing. dangerous_overtaking, and near_collision.  
- **data_name, date, author, email, copy_right**: basic information for description of the scenarios.  

All of data files format 000000.json. Each data file contains ego vehicle state, lane state, and other objects state.  
Ego vehicle state contains the following attributes:  
- **x**: the latitude of the ego vehicle.  
- **y**: the longitude of the ego vehicle.  
- **theta**: the angle from the magnetic north.  
- **v**: the velocity of the ego vehicle.  
- **ax**: the heading direction acceleration of the ego vehicle.  
- **ay**: the lateral direction acceleration of the ego vehicle.  
- **omega**: the angular velocity of the ego vehicle.  
- **deviation**: the deviation of the ego vehicle from the center line.  
- **decision**: the decretized decision of the ego vehicle. This attribute is categorized into four. 0, 1, 2, 3 means 'KEEPING LANE', 'CHANGING LEFT', 'CHANGING RIGHT', 'STOP', respectively.
  
Lane state is the array of lanes. Each lane has four coefficients for representing lane.  
Each lane is represented by cubic function with four coefficients: Z = C3*X^3 + C2*X^2 + C1*X + C0.  
Z is the lateral displacement from the point which is placed in front of the ego vehicle by a distance of X.  

Objects state is the array of surrounding objects from the ego vehicle. Each Object contains the following attributes. The location of object is represented in the ego vehicle frame which has a heading direction of the ego vehicle for x-axis, and lateral direction of the ego vehicle for y-axis.   
- **x**: x-value of the center of the object in the ego vehicle frame.  
- **y**: y-value of the center of the object in the ego vehicle frame.  
- **theta**: the heading direction of the object in the ego vehicle frame.  
- **v**: the velocity of the object.  
- **ax**: the acceleration magnitude of the object heading direction.  
- **omega**: the angular velocity of the object.  
- **l**: the length of the object.  
- **w**: the width of the object.  
- **age**: the number of frames that the object appears near the ego vehicle.  
- **id**: the unique id for the object.  



## Abstract
Designing or learning an autonomous driving policy is undoubtedly a challenging task as the policy has to maintain its safety in all corner cases. In order to secure safety in autonomous driving, the ability to detect hazardous situations, which can be seen as an out-of-distribution (OOD) detection problem, becomes crucial. However, most conventional datasets only provide expert driving demonstrations, although some non-expert or uncommon driving behavior data are needed to implement a safety guaranteed autonomous driving platform. To this end, we present a novel dataset called the *R3 Driving Dataset*, composed of driving data with different qualities. The dataset categorizes abnormal driving behaviors into eight categories and 369 different detailed situations. The situations include dangerous lane changes and near-collision situations. To further enlighten how these abnormal driving behaviors can be detected, we utilize different uncertainty estimation and anomaly detection methods to the proposed dataset. From the results of the proposed experiment, it can be inferred that by using both uncertainty estimation and anomaly detection, most of the abnormal cases in the proposed dataset can be discriminated. The dataset of this paper can be downloaded from https://rllab-snu.github.io/projects/R3-Driving-Dataset/doc.html.