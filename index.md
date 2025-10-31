My name is Liqun Li [李立群](index_cn.md). I'm currently a Principal Researcher in the DKI (Data, Knowledge, and Intelligence) group at Microsoft. I'm currently focused on building autonomous agents based on LLMs for data analytics and workflow automation. 
Check my [TaskWeaver](https://github.com/microsoft/TaskWeaver) project and here is the video for technique [deepdive](https://www.youtube.com/watch?v=7Q7rSSfFPLE).

I received my Ph.D. from the Institute of Software Chinese Academy of Sciences (ISCAS) in 2012, and my B.E. from the Department of Computer Science and Technology at Tsinghua University in 2006. I visited Michigan State University as a visiting scholar in 2009.

I have broad interests in various areas such as IoT, Mobile, Big Data, Machine Learning, and Cloud. I have published papers in top-tier conferences and journals including Mobisys, Mobicom, NSDI, ATC, ICSE, ESEC/FSE, ICDCS, RTSS, TPDS, TOSN, etc.

*I'm always open to new opportunities and collaborations* [中文简历](index_cn.md). Feel free to drop me an email at liqul@outlook.com or liliqun.2002@tsinghua.org.cn.



## Work Experience

* **2019.06  - now** *Principal Researcher* in DKI (Data, Knowledge, and Intelligence) group at Microsoft.
* **2016.11 - 2019.6** *Architect* at [K2Data](http://k2data.com.cn), a startup company on industrial IoT big data analytics in China.
* **2016.05  - 2016.11** *Engineer* at [高德地图](https://www.amap.com/), a leading map service provider in China.
* **2014.11 - 2016.02** *Engineer* at [PP租车](http://www.ppzuche.com), a startup company on peer-to-peer car rental service in China.
* **2012.08  - 2014.11** *Researcher* in Mobile Sensing and Systems group (MASS) at Microsoft Research Asia (MSRA).

## Selected Projects

### LLM-powered Agent

Large Language Models (LLMs) excel in natural language tasks but struggle with domain-specific data analytics and diverse user requirements. [TaskWeaver](https://github.com/microsoft/TaskWeaver/), a code-first framework, addresses these limitations by transforming user requests into executable code and treating plugins as callable functions. Supporting rich data structures, flexible plugin usage, dynamic plugin selection, and complex logic, TaskWeaver incorporates domain knowledge and ensures secure code execution. This powerful, adaptable framework enables intelligent conversational agents to manage intricate tasks and domain-specific scenarios. 

<img src="https://github.com/liqul/liqul.github.io/assets/7489260/144d9c68-139a-4cbc-93f4-598723c731ac" width = "80%" align=center />

[StepFly](https://arxiv.org/pdf/2510.10074v1) is an agentic automation framework that can execute natural language based workflow documentation. A concrete example is automating troubleshooting guide execution for service incident management. StepFly's execution follows a pre-extracted lightweighted DAG of the target workflow, achieving high efficiency and reliablity. Moreover, StepFly can assign multiple executors for parallable steps on the DAG, further accelerating the process.

<img width="80%" alt="stepfly" src="https://github.com/user-attachments/assets/c5b11107-64d6-4c7c-9647-278fbe3c1618" />


### Intelligent Incident Management

Outages result in significant financial and customer satisfaction losses. My work focuses on incident detection and diagnosis for Azure and Office 365, including the development of [Warden](https://www.usenix.org/conference/atc21/presentation/li-liqun), an ML-based framework for detecting potential outages using monitor-generated alerts. Upon detection, Warden notifies on-call engineers and incident managers. Successfully integrated into Azure's incident management platform, Warden has been operational for over a year. 

<img src="/assets/warden.png" width = "80%" align=center />

Another project is called [CONAN](https://conf.researchr.org/details/icse-2023/icse-2023-SEIP/6/CONAN-Diagnosing-Batch-Failures-for-Cloud-Systems), for automated diagnosis for large-scale online services. Though practical diagnosis scenarios vary from one to another, they share one common principle -- the process of finding the root cause usually manifests as comparing two groups of data, such as failed instances versus succeeded instances, instances with long latency versus those with normal latency, instances during an anomalous period versus those before that period. The differences between the two groups are usually indicative of the root cause. CONAN is a flexible framework that can be customized for different scenarios, which has now been adopted for over 10 scenarios in Azure and Office 365.  

<img src="/assets/Conan.png" width = "80%" align=center />

### Data Management for Industrial IoT

<img src="/assets/tsdw.png" width = "80%" align=center />

Time series is the first-class citizen in industrial scenarios. Machines with hundreds of sensors generate tons of time series data that need to be stored and analyzed, demanding a scalable and reliable storage service. However, existing solutions (e.g., OpenTSDB, Influxdb, and Timescaledb) either adopt a single-node deployment or lack an appropriate data model. Therefore, we developed a new time series storage service, leveraging existing open-source projects such as Hadoop, Kafka, Zookeeper, and Parquet. We built key building blocks to enable atomic data ingestion, partitioning, and compaction. Time series data can be directly read, processed, and analyzed by parallel computing frameworks such as Hadoop Map-reduce or Spark.

<img src="/assets/obj.png" width = "60%" align=center />

Machines not only generate time series but also a huge number of objects. Storing those files sounds trivial, but analyzing them incurs challenges, especially on a huge number of files. Our goal is to build an object storage service that is capable of holding a huge number of files, as well as offering easy interfaces for data analysis. For this purpose, we adopt the data model of **object = metadata + file**. The metadata is indexed by Elasticsearch, and we implement atomic CURD. We keep the file in HDFS, where Map-reduce or Spark programs can directly read the files. To prevent the "small-file-problem", a background housekeeper process continuously compacts small files. 

### Transportation Activity Recognition on Smartphones

<img src="/assets/architecture.jpg" width = "30%" align=center />

In  data crowdsourcing, it is useful to know your user's transportation status. For instance, for a map maintainer, knowing the transportation status helps to distinguish if the data is collected on a road, sidewalk, or in a building. However, it is nontrivial to approach high accuracy. Practical challenges include unknown phone gestures, random noises, and achieving high energy efficiency. I designed a framework combining both inputs from the inertial sensors (accelerometer and gyroscope) and various contextual information. Extraneous events incurred by user random activities are filtered with intuitive rules discovered through our training data from tens of people. We finally achieved a significantly better accuracy compared with existing frameworks from Google and Samsung.


### Indoor localization

Localization in indoor areas is nontrivial because GPS signals cannot penetrate walls. To tackle this challenge, we leverage various signals, e.g., Wi-Fi, Bluetooth, Geomagnetic field, IMU sensors, and even visible light, which are commonly found in indoor environments. 

![Localization](/assets/localization.jpg)

Specifically, we proposed a Wi-Fi based positioning system called [*Modellet*](http://research.microsoft.com/jump/221298). Modellet takes advantage of both fingerprint-based and model-based approaches and can adapt to environmental locality and training data density. We evaluate Modellet with data collected from venues (offices, airports, and shopping malls) across China, Germany, and the U.S. We show that Modellet outperforms Radar and EZPerfect. Secondly, we build a system called [*Magicol*](https://kabru.eecs.umich.edu/yuanchao/paper/jsac15magicol.pdf) adding more modalities, i.e., Geomagnetic field and IMU sensors, to the system to improve localization accuracy. We leverage the particle filter framework to fuse the signals. Evaluation results show that Magicol achieves around 2-meter accuracy in office and shopping mall areas. Finally, we explore the possibility of positioning with visible light emitted from LEDs. LED bulbs are modified to blink in unique patterns (invisible to human eyes). Any device with a light sensor can decode and estimate its own position based on the light energy propagation model. The system is called [*Epsilon*](http://research.microsoft.com/pubs/209511/epsilon-cameraready.pdf) which achieves submeter-level accuracy. 

### Wireless Sensor Network

![Sensor Networking](/assets/sensor.jpg)

Wireless sensor network (WSN) typically refers to a large number of networked embedded devices, called sensor nodes. In WSNs, data is transmitted from one node to another in a multi-hop minor. WSNs are usually deployed in harsh environments like in forests or around volcanoes, and therefore the nodes face frequent failures. I studied several issues raised from WSNs. Specifically, I develop voice-streaming systems (namely [QVS](http://www.cse.msu.edu/~glxing/docs/voice_icdcs09.pdf) and [ASM](http://www.cse.msu.edu/~glxing/docs/asm_rtss10.pdf)) which are aware of the voice quality. These systems prevent the problem of network congestion with an admission control protocol. I also investigate the [time synchronization](http://www.cse.msu.edu/~glxing/docs/rds-li.pdf) problem where we need to maintain accurate relative time between sensor nodes. I exploit the regular pattern of the RDS data carried by the FM radio signal for energy-efficient millisecond-level time synchronization in city-scale sensor networks. 

## Selected Publications ([Google Scholar](https://scholar.google.com/citations?user=icgetesAAAAJ&hl=en))

**LLM**
+ Bo Qiao, **Liqun Li**, Xu Zhang, Shilin He, ..., [TaskWeaver: A Code-First Agent Framework](https://arxiv.org/pdf/2311.17541.pdf),  *arXiv:2311.17541* (2023).
+ Zhang, Chaoyun, **Liqun Li**, Shilin He, Xu Zhang, Bo Qiao, Si Qin, Minghua Ma et al. [UFO: A UI-Focused Agent for Windows OS Interaction](https://arxiv.org/pdf/2402.07939.pdf) *arXiv:2402.07939* (2024).
+ Chaoyun Zhang, Shilin He, Jiaxu Qian, Bowen Li, **Liqun Li** et al. [Large Language Model-Brained GUI Agents: A Survey](https://arxiv.org/abs/2411.18279) *arXiv:2411.18279* (2024).
+ Chaoyun Zhang, ..., **Liqun Li**, et al. [UFO2: The Desktop AgentOS](https://arxiv.org/abs/2504.14603) *arXiv:2504.14603* (2025).

**AIOps**

+ **Liqun Li**, Xu Zhang, Xin Zhao, Hongyu Zhang, Yu Kang, ..., [Fighting the Fog of War: Automated Incident Detection for Cloud Systems](https://www.usenix.org/conference/atc21/presentation/li-liqun), *ATC*'21
+ Xuheng Wang, Xu Zhang, **Liqun Li**, Shilin He, ..., [SPINE: A Scalable Log Parser with Feedback Guidance](https://dl.acm.org/doi/10.1145/3540250.3549176), *FSE*'22, selected as the **SIGSOFT Distinguished Paper**
+ Y. Chen, **Liqun Li**, Y. Kang, ..., [NetPanel: Traffic Measurement of Exchange Online Service](https://www.usenix.org/conference/nsdi23/presentation/chen-2), *NSDI*'23
+ **Liqun Li**, Xu Zhang, Shilin He, Yu Kang, Hongyu Zhang, ..., [CONAN: Diagnosing Batch Failures for Cloud Systems](https://conf.researchr.org/details/icse-2023/icse-2023-SEIP/6/CONAN-Diagnosing-Batch-Failures-for-Cloud-Systems), *ICSE (SEIP)*'23
+ An, Kaikai, Fangkai Yang, **Liqun Li**, Zhixing Ren, Hao Huang, Lu Wang, Pu Zhao et al. [Nissist: An Incident Mitigation Copilot based on Troubleshooting Guides](https://arxiv.org/pdf/2402.17531.pdf)  *arXiv:2402.17531* (2024).

**Indoor Localization**

+ **Li, Liqun**; Hu, Pan; Shen, Guobin; Peng, Chunyi; Zhao, Feng; [Epsilon: Visible Light Based Positioning System](http://research.microsoft.com/pubs/209511/epsilon-cameraready.pdf), *NSDI*'13
+ **Li, Liqun**; Shen, Guobin; Zhao, Chunshui; Moscibroda, Thomas; Lin, Jyh-Han; Zhao, Feng; [Experiencing and Handling the Diversity in Data Density and Environmental Locality in an Indoor Positioning Service](http://research.microsoft.com/jump/221298), *Mobicom*'14
+ Yuanchao Shu, Cheng Bo, Guobin Shen, Chunshui Zhao, **Liqun Li** and Feng Zhao; [Magicol: Indoor Localization Using Pervasive Magnetic Field and Opportunistic WiFi Sensing](https://kabru.eecs.umich.edu/yuanchao/paper/jsac15magicol.pdf) IEEE Journal of Selected Areas in Communications, vol.33, no.7, pp.1443-1457, July 2015

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
+ Excellent Ph.D. thesis award by the Chinese Academy of Sciences in 2013.


