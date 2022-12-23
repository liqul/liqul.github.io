My name is Liqun Li. I am a system engineer & researcher with interests in IoT, Mobile, Big Data, and Cloud. I am currently focused on optimizing reliability and resource provisioning efficiency for cloud systems. 

I received my Ph.D. degree in CS from the Institute of Software Chinese Academy of Sciences (ISCAS) in 2012, and my B.E. degree from the Department of Computer Science and Technology at Tsinghua University in 2006. I visited Michigan State University as a visiting scholar in 2009. 

Feel free to reach me at liqul (at) outlook.com, though I may not be very responsive. 


## Work Experience

* **2019.6  - now** Principal Researcher in Data. Knowledge. Intelligence (DKI) group at Microsoft Research Asia (MSRA).
* **2016.11 - 2019.6** Architect at [K2Data](http://k2data.com.cn). 
* **2016.5  - 2016.11** Engineer at [高德地图](https://www.amap.com/).
* **2014.11 - 2016.2** Engineer at [PP租车](http://www.ppzuche.com).
* **2012.8  - 2014.11** Researcher in Mobile Sensing and Systems group (MASS) at Microsoft Research Asia (MSRA).

## Selected Projects

### Intelligent Incident Management

Outages cause huge loss in terms of money and customer satisfactory. I'm working on various projects about incident detection, diagnosis, and mitigation in large-scale cloud systems. For example, we developed a framework, namely [Warden](https://www.usenix.org/conference/atc21/presentation/li-liqun), based on a ML model to detect potential outages with monitor-generated alerts. Once a potential outage is detected, Warden fires a report to the on-call engineer and incident manager. Warden has been running in the incident management platform of Azure for over one year. 

Another project is about automated diagnosis for cloud systems. More details TBD. 

### Data Management for Industrial IoT

<img src="/assets/tsdw.png" width = "80%" align=center />

Time series is the first class citizen in industrial scenarios. Machines with hundreds of sensors generate tons of time series data that need to be stored and analyzed, demanding for a scalable and reliable storage service. However, existing solutions (e.g., OpenTSDB, Influxdb, and Timescaledb) either adopt a single node deployment, or lack of an aproperiate data model. Therefore, we developed a new time series storage service, leveraging existing open sourced projects such as Hadoop, Kafka, Zookeeper, and Parquet. We built key building blocks to enable atomic data ingestion, partitioning, and compaction. Time series data can be directly read, processed, and analyzed by parallel computing frameworks such as Hadoop Map-reduce or Spark.

<img src="/assets/obj.png" width = "60%" align=center />

Machines not only generate time series, but also a huge number of objects. Storing those files sounds trivial, while analyzing them incurs challenges, especially on a huge number of files. Our goal is to build an object storage service which is capable of holding a huge number of files, as well as offering easy interfaces for data analysis. For this purpose, we adopt the data model of **object = metadata + file**. The metadata is indexed by Elasticsearch, and we implement atomic CURD. We keep the file in HDFS, where Map-reduce or Spark programs can directly read the files. To prevent from the "small-file-problem", a background housekeeper process continuously compacts small files. 

### Transportation Activity Recognition on Smartphones

<img src="/assets/architecture.jpg" width = "30%" align=center />

In  data crowdsourcing, it is useful to know your user's transportation status. For instance, for a map maintainer, knowing the transportation status helps to distinguish if the data is collected on road, sidewalk, or in building. However, it is nontrivial to approach high accuracy. Practical challenges include unknown phone gesture, random noises, and achieving high energy efficiency. I designed a framework combining both inputs from the inertial sensors (accelerometer and gyroscope) and various contextual informations. Extraneous events incurred by user random activities are filtered with intuitive rules discovered through our training data from tens of people. We finally achieved a significantly better accuracy compared with existing frameworks from Google and Samsung.


### Indoor localization

Localization in indoor areas is nontrivial due to the fact that GPS signals cannot penetrate walls. To tackle this challenge, we leverage various signals, e.g., Wi-Fi, Bluetooth, Geomagnetic field, IMU sensors, and even visible light, which are commonly found in indoor environment. 

![Localization](/assets/localization.jpg)

Specifically, we proposed a Wi-Fi based positioning system called [*Modellet*](http://research.microsoft.com/jump/221298). Modellet takes advantage of both fingerprint-based and model-based approaches, and is able to adapt to environmental locality and training data density. We evaluate Modellet with data collected from venues (office, airport, and shopping mall) across China, Germany, and the U.S. We show that Modellet outperforms Radar and EZPerfect. Secondly, we build a system called [*Magicol*](https://kabru.eecs.umich.edu/yuanchao/paper/jsac15magicol.pdf) adding more modalities, i.e., Geomagnetic field and IMU sensors, to the system to improve localization accuracy. We leverage the particle filter framework to fuse the signals. Evaluation results show that Magicol achieves around 2-meter accuracy in office and shopping mall areas. Finally, we explore the possibility of positioning with visible light emitted from LEDs. LED bulbs are modified to blink in unique patterns (invisible to human eyes). Any device with a light sensor can decode and estimate its own postion based on the light energy propagation model. The system is called [*Epsilon*](http://research.microsoft.com/pubs/209511/epsilon-cameraready.pdf) which achieves submeter-level accuracy. 

### Wireless Sensor Network

![Sensor Networking](/assets/sensor.jpg)

Wireless sensor network (WSN) typically refers to a large number of networked embedded devices, called sensor nodes. In WSNs, data is transmitted from one node to another in a multi-hop minor. WSNs are usually deployed in harsh environments like in forest or around volcano, and therefore the nodes face frequent failures. I studied several issues raised from WSNs. Specifically, I develop voice-streaming systems (namely [QVS](http://www.cse.msu.edu/~glxing/docs/voice_icdcs09.pdf) and [ASM](http://www.cse.msu.edu/~glxing/docs/asm_rtss10.pdf)) which are aware of the voice quality. These systems prevent the problem of network congestion with an admission control protocol. I also investigate the [time synchronization](http://www.cse.msu.edu/~glxing/docs/rds-li.pdf) problem where we need to maintain accurate relative time between sensor nodes. I exploit the regular pattern of the RDS data carried by the FM radio signal for energy efficient millisecond-level time synchronization in city-scale sensor networks. 

## Selected Publications ([Google Scholar](https://scholar.google.com/citations?user=icgetesAAAAJ&hl=en))

**AIOps**

+ **Liqun Li**, Xu Zhang, Xin Zhao, Hongyu Zhang, Yu Kang, Pu Zhao, Bo Qiao, Shilin He, Pochian Lee, Jeffrey Sun, Feng Gao, Li 
Yang, Qingwei Lin, Saravanakumar Rajmohan, Zhangwei Xu, and Dongmei Zhang, [Fighting the Fog of War: Automated Incident Detection for Cloud Systems](https://www.usenix.org/conference/atc21/presentation/li-liqun), *ATC*'21
+ Xuheng Wang, Xu Zhang, **Liqun Li**, Shilin He, Hongyu Zhang, Yudong Liu, Lingling Zheng, Yu Kang, Qingwei Lin, Yingnong Dang, Saravan Rajmohan, Dongmei Zhang, [SPINE: A Scalable Log Parser with Feedback Guidance](https://dl.acm.org/doi/10.1145/3540250.3549176), *FSE*'22, selected as the **SIGSOFT Distinguished Paper**
+ Y. Chen, **Liqun Li**, Y. Kang, B. Zheng, Y. Wang, M. Zhou, Y. Dai, Z. Yang, B. Rutkowski, J. Mealiffe, Q. Lin, [NetPanel: Traffic Measurement of Exchange Online Service](https://www.usenix.org/conference/nsdi23/presentation/chen-2), *NSDI*'23
+ **Liqun Li**, Xu Zhang, Shilin He, Yu Kang, Hongyu Zhang, Minghua Ma, Yingnong Dang, Zhangwei Xu, Saravan Rajmohan, Qingwei Lin, Dongmei Zhang, CONAN: Diagnosing Batch Failures for Cloud Systems, *ICSE (SEIP)*'23

**Indoor Localization**

+ **Li, Liqun**; Hu, Pan; Shen, Guobin; Peng, Chunyi; Zhao, Feng; [Epsilon: Visible Light Based Positioning System](http://research.microsoft.com/pubs/209511/epsilon-cameraready.pdf), *NSDI*'13
+ **Li, Liqun**; Shen, Guobin; Zhao, Chunshui; Moscibroda, Thomas; Lin, Jyh-Han; Zhao, Feng; [Experiencing and Handling the Diversity in Data Density and Environmental Locality in an Indoor Positioning Service](http://research.microsoft.com/jump/221298), *Mobicom*'14
+ Yuanchao Shu, Cheng Bo, Guobin Shen, Chunshui Zhao, **Liqun Li** and Feng Zhao; [Magicol: Indoor Localization Using Pervasive Magnetic Field and Opportunistic WiFi Sensing](https://kabru.eecs.umich.edu/yuanchao/paper/jsac15magicol.pdf) IEEE Journal of Selected Areas in Communications, vol.33, no.7, pp.1443-1457, July, 2015

**Wireless Sensor Networking**

+ **Li, Liqun**; Xing, Guoliang; Sun, Limin; Liu, Yan; [QVS: quality-aware voice streaming for wireless sensor networks](http://www.cse.msu.edu/~glxing/docs/voice_icdcs09.pdf), *ICDCS*'09
+ **Li, Liqun**; Xing, Guoliang; Han, Qi; Sun, Limin; [Adaptive voice stream multicast over low-power wireless networks](http://www.cse.msu.edu/~glxing/docs/asm_rtss10.pdf), *RTSS*'10
+ **Li, Liqun**; Xing, Guoliang; Sun, Limin; Huangfu, Wei; Zhou, Ruogu; Zhu, Hongsong; [Exploiting fm radio data system for adaptive clock calibration in sensor networks](http://www.cse.msu.edu/~glxing/docs/rds-li.pdf), *Mobisys*'11

**Misc**

+ **Li, Liqun**; Sun, Limin; [Seer: trend-prediction-based geographic message forwarding in sparse vehicular networks](http://ieeexplore.ieee.org/xpls/abs_all.jsp?arnumber=5502675), *ICC*'10
+ Hu, Pan; Shen, Guobin; **Li, Liqun**; Lu, Donghuan; [ViRi: view it right](http://panhu.me/pdf/ViRi.pdf), *Mobisys*'13
+ Jiangtao Li, Angli Liu, Guobin Shen, **Liqun Li**, Chao Sun, and Feng Zhao. 2015. Retro-VLC: Enabling Battery-free Duplex Visible Light Communication for Mobile and IoT Applications, *HotMobile* '15


### Awards

+ 2nd place in [IPSN Indoor Localization](http://research.microsoft.com/en-us/events/ipsn2014indoorlocalizatinocompetition/) Competition in 2014 held in Berlin, Germany.
+ Excellent Ph.D. thesis award by Chinese Academy of Sciences in 2013.



