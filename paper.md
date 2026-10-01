---
title: "ALTER-EGO: A Mobile Robot With a Functionally Anthropomorphic Upper Body Designed for Physical Interaction"
title_zh: "ALTER-EGO：一种为物理交互设计、具有功能性拟人上身的移动机器人"
authors: "Gianluca Lentini, Alessandro Settimi, Danilo Caporale, Manolo Garabini, Giorgio Grioli, Lucia Pallottino, Manuel G. Catalano, and Antonio Bicchi"
venue: "IEEE Robotics & Automation Magazine, December 2019, vol. 26, no. 4"
doi: "10.1109/MRA.2019.2943846"
source_type: "pdf-text"
source_path: "Reference/Magazine/1. Alter-Ego_A_Mobile_Robot_With_a_Functionally_Anthropomorphic_Upper_Body_Designed_for_Physical_Interaction.pdf"
reader_status: "complete bilingual draft; source figures and table crops included"
---

# ALTER-EGO

## A Mobile Robot With a Functionally Anthropomorphic Upper Body Designed for Physical Interaction

## 具有功能性拟人上身、为物理交互而设计的移动机器人

**Authors / 作者:** Gianluca Lentini, Alessandro Settimi, Danilo Caporale, Manolo Garabini, Giorgio Grioli, Lucia Pallottino, Manuel G. Catalano, and Antonio Bicchi

**Source:** local PDF, 14 pages; magazine pages 94-107. DOI: 10.1109/MRA.2019.2943846. The article has selectable English text; the rotated Table 1 was visually checked against the rendered pages.

## 阅读导航

- p.1: 背景与研究动机；ALTER-EGO 的问题定位
- p.2: Requirements Analysis；Manipulation；Locomotion；Fig. 1
- p.3-4: Table 1；Intelligence；Sensing；Pilot Station；ALTER-EGO 概览
- p.5-6: 机械结构、移动底座、Manipulation；Fig. 2；Eq. (1)-(4)
- p.7-8: Control；Eq. (5)-(6)；Fig. 3；Sensing；Fig. 4
- p.9-10: 机电、软件与通信架构；Operating Modes；Fig. 5-6
- p.11-12: Teleoperation Mode；Pilot Interface；Eq. (7)；Fig. 7-8
- p.13-14: Experiments and Discussion；Conclusions；Acknowledgments；References；作者信息

## 公式索引

- [E001 · Eq. (1)](#E001) - p.6，关节动力学与末端力项
- [E002 · Eq. (2)](#E002) - p.6，双电机弹性模型
- [E003 · Eq. (3)](#E003) - p.6，对称双电机模型
- [E004 · Eq. (4)](#E004) - p.6，挠度、刚度调节角与平衡角
- [E005 · Eq. (5)](#E005) - p.7，准速度误差动力学
- [E006 · Eq. (6)](#E006) - p.8，广义力矩控制律
- [E007 · Eq. (7)](#E007) - p.11，从肩部到手部的齐次变换

## 术语表 / Terminology Ledger

| Canonical term | 中文译名与首次定义 | Source variants / decision |
|---|---|---|
| ALTER-EGO | 机器人平台名称，保留原文 | 统一使用大写 ALTER-EGO |
| soft robotics | 软体机器人技术 | 与 soft robotic technologies 统一 |
| variable-stiffness actuator (VSA) | 可变刚度执行器；刚度可主动调节 | 首次写全称，后用 VSA |
| series-elastic actuation | 串联弹性驱动 | 不译成“串联柔性驱动” |
| teleoperation | 远程操作 | teleoperated mode 译为远程操作模式 |
| teleimpedance | 远程阻抗控制 | 保留 teleimpedance 作为专门术语 |
| shared autonomy | 共享自主性 | 指自主控制与人类操作共同承担任务 |
| underactuated | 欠驱动 | 保留与机构自由度相关的原义 |
| SoftHand (SH) | SoftHand 软手；SH | 产品/机构名保留 SoftHand |
| end effector | 末端执行器 | 统一为“末端执行器” |
| degrees of freedom (DoF) | 自由度；DoF | 首次写全称，后用 DoF |
| impedance control | 阻抗控制 | 与 position/stiffness control 区分 |
| inverse kinematics (IK) | 逆运动学；IK | 统一使用 IK |
| linear quadratic regulator (LQR) | 线性二次型调节器；LQR | 统一使用 LQR |
| center of mass (CoM) | 质心；CoM | 不与 geometric center 混用 |
| inertial measurement unit (IMU) | 惯性测量单元；IMU | 统一使用 IMU |
| RGB-D | 红绿蓝-深度 | 保留 RGB-D 拼写 |
| simultaneous localization and mapping (SLAM) | 同时定位与建图；SLAM | 首次写全称，后用 SLAM |
| RTAB-MAP | Real-Time Appearance-Based Mapping | 算法名称保留原文 |
| Robot Operating System (ROS) | 机器人操作系统；ROS | 软件框架名保留 ROS |
| haptic feedback | 触觉反馈 | 不泛化为“力反馈” |
| physical interaction | 物理交互 | 统一用“物理交互” |
| pilot station | 操作员站 / 操作站 | 在远程操作语境中译为操作员站 |
| quasi-velocity | 准速度 | 与普通速度 vector 区分 |
| wrench | 力-力矩合量 | end-effector wrench 译为末端执行器力-力矩合量 |
| VSA-CUBE | VSA-CUBE 模块化执行器设计 | 专名不翻译 |

> **术语一致性说明：** 原文在不同位置使用 robot/pilot、teleoperation/teleoperated、stiffness/impedance 等相近表达。本 reader 保留原文中的概念边界；中文译名采用上表的固定形式，不用同义词轮换。

## 正文 / Bilingual Reader

### p.1 - Background and motivation

<a id="S001"></a>
**Source:** p.1 S001

**Original:** Historically, robots first found application in factories and plants. Until recently, the most noticeable examples of robot systems directly sold to the consumer were limited to edutainment systems (e.g., NAO [1]), automated chore robots [26], and social telepresence platforms [27]. Initially, telepresence robots consisted of a mobile base with an interactive screen. Today, following a trend of anthropomorphization of technology, human-like upper bodies have begun to replace those simple screens (e.g., Pepper [2] and R1 [3]) and share the same social communication modalities of humans, e.g., body posture, gestures, gaze direction, and facial expressions. Unfortunately, social robots are mostly designed to speak and make gestures and have limited capabilities when it comes to physically interacting with people and their surrounding environments.

**中文:** 从历史上看，机器人最早应用于工厂和工业设施。直到最近，直接面向消费者销售的机器人系统中，最显眼的例子仍主要局限于教育娱乐系统（例如 NAO [1]）、自动化家务机器人 [26] 和社交远程呈现平台 [27]。早期的远程呈现机器人由移动底座和交互式屏幕组成。如今，随着技术拟人化趋势的发展，类人上身开始取代这些简单屏幕（例如 Pepper [2] 和 R1 [3]），并共享人类的社会沟通方式，例如身体姿态、手势、注视方向和面部表情。然而，社交机器人通常主要被设计用于说话和做手势；当任务涉及与人及周围环境进行物理交互时，它们的能力仍然有限。

<a id="S002"></a>
**Source:** p.1 S002

**Original:** On the other hand, looking at the state of the art, there are promising examples (e.g., WALK-MAN [4], Atlas [5], and TORO [6]) of humanoid robots that have been developed to operate in unstructured environments and perform challenging interaction tasks, e.g., walking on rough terrains, moving heavy objects, and solving complex bimanual manipulation tasks. Specific enabling technologies have improved the effectiveness of these robots and facilitate their interactions with the surrounding world, e.g., active impedance control in TORO and series-elastic actuation in WALK-MAN. Indeed, these same technologies permit robot arms to cross the borders of industrial work cells and become the type of collaborative robots that can work in close contact with people and share the same operating space.

**中文:** 另一方面，从当前技术水平来看，已有一些很有前景的类人机器人（例如 WALK-MAN [4]、Atlas [5] 和 TORO [6]），它们被开发用于非结构化环境，并执行具有挑战性的交互任务，例如在崎岖地形上行走、搬运重物，以及完成复杂的双臂操作任务。一些关键使能技术提高了这些机器人的有效性，并促进了它们与周围世界的交互，例如 TORO 中的主动阻抗控制，以及 WALK-MAN 中的串联弹性驱动。事实上，这些技术使机器人手臂能够走出工业工作单元的边界，成为可以与人近距离接触、共享工作空间的协作机器人。

<a id="S003"></a>
**Source:** p.1 S003

**Original:** Although both humanoid robotics and teleoperation have a long history, we believe that three concurrent factors are accelerating the diffusion of robots in real environments.

**中文:** 尽管类人机器人技术和远程操作都有着悠久的历史，我们认为，三个同时发生的因素正在加速机器人在真实环境中的普及。

<a id="S004"></a>
**Source:** p.2 S004

**Original:** The first factor is the success of Soft Robotics. Technologies such as series-elastic actuation, variable impedance, and teleimpedance controllers allow machines to interact safely and effectively with humans and the environment. The second factor is the commoditization of hardware and software technologies that, until recently, were relegated to very specialized engineering fields, e.g., nuclear, military, and aerospace. Examples of these technologies include virtual-reality (VR) headsets, integrated inertial navigation units, high-bandwidth and low-latency networking, and, in general, affordable computational power and reliable sensing. The third factor is the growing interest of large companies and funding agencies, which is fostering novel humanoid robotics and teleoperation developments through science competitions and the awarding of prizes. Two popular examples are the 2015 DARPA Robotics Challenge (US$8 million prize) [28] and the recent All Nippon Airways Avatar XPRIZE (XP) (US$10 million prize) [29], “a four-year global competition focused on accelerating the integration of several emerging and exponential technologies into a multipurpose avatar system that will enable us to see, hear, touch, and interact with physical environments and other people through an integrated robotic device” [30]. The focus of the latter includes the domains of health care, services, inspection, and maintenance and demonstrates the importance of physical-interaction capabilities, sensing integration, and user friendliness.

**中文:** 第一个因素是软体机器人技术的成功。串联弹性驱动、可变阻抗和远程阻抗控制器等技术，使机器能够安全而有效地与人及环境交互。第二个因素是硬件和软件技术的商品化；这些技术直到最近还主要属于核工程、军事和航空航天等高度专业化领域。相关例子包括虚拟现实（VR）头戴设备、集成式惯性导航单元、高带宽低时延网络，以及总体上更易获得的计算能力和更可靠的传感。第三个因素是大型企业和资助机构日益增长的兴趣；它们通过科技竞赛和奖金机制推动了新型类人机器人与远程操作的发展。两个广为人知的例子是 2015 年的 DARPA Robotics Challenge（奖金 800 万美元）[28]，以及近期的 All Nippon Airways Avatar XPRIZE（XP，奖金 1000 万美元）[29]。后者是一项“为期四年的全球竞赛，旨在加速多种新兴及指数型技术整合到多用途化身系统中，使人们能够借助集成式机器人设备看见、听见、触摸并与物理环境及其他人交互”[30]。该竞赛关注医疗保健、服务、检查和维护等领域，体现了物理交互能力、传感整合和易用性的重要性。

<a id="S005"></a>
**Source:** p.2 S005

**Original:** Inspired by these challenges and perspectives, and leveraging our previous experiences and contributions [4], [7], in this article, we present ALTER-EGO. As shown in Figure 1, the robot is a robust and versatile mobile system with a functional anthropomorphic upper body. To operate in different working scenarios and safely perform physical human-robot interactions, ALTER-EGO is powered by variable-stiffness actuators (VSAs), which exhibit a stiffness behavior similar to that of human muscles [8]. Each arm mounts an anthropomorphic, synergistic artificial hand inspired by human motor synergies [7]. The upper body is mounted on a two-wheel, self-balancing mobile base that minimizes the robot's footprint and increases agility. The system is equipped with sensors and computational systems that allow the robot to work autonomously. Moreover, ALTER-EGO can also be used in teleoperation mode from a pilot station mainly composed of lightweight and wearable interfaces. Featuring an immersive control mode, the system can use teleimpedance control [9] to pair the pilot's actions with the robot's mechanical behavior, not only in terms of movements but also in terms of intended interactions behavior.

**中文:** 受这些挑战和发展前景启发，并基于我们此前的经验与贡献 [4]、[7]，本文提出 ALTER-EGO。如图 1 所示，该机器人是一个坚固而多用途的移动系统，具有功能性拟人上身。为了在不同工作场景中运行并安全完成物理人机交互，ALTER-EGO 采用可变刚度执行器（VSA）；其刚度行为类似于人类肌肉 [8]。每条手臂都安装了一只受人类运动协同启发、具有人体形态的协同式人工手 [7]。上身安装在双轮自平衡移动底座上，从而减小机器人占地面积并提高灵活性。系统配备了传感器和计算系统，可以自主工作。此外，ALTER-EGO 还可以通过操作员站进行远程操作，操作员站主要由轻量、可穿戴接口组成。在沉浸式控制模式下，系统可以使用远程阻抗控制 [9]，把操作员的动作与机器人的机械行为联系起来；这种联系不仅体现在运动层面，也体现在期望的交互行为层面。

<a id="F001"></a>
### Fig. 1. ALTER-EGO 的双臂移动平台

**Placed near:** p.2 S005
**Source:** p.2 C002

![Fig. 1](assets/figures/fig1.png)

<a id="C002"></a>
**Original caption:** Figure 1. ALTER-EGO: a soft, dual-arm mobile platform equipped with variable-stiffness actuation units and soft, underactuated hands.

**中文图注:** 图 1。ALTER-EGO：一种配备可变刚度驱动单元和柔性欠驱动手的双臂软体移动平台。

**Reading note:** The figure introduces the central design claim: a small mobile base is combined with a functionally anthropomorphic upper body and compliant hands. / 该图呈现论文的核心设计主张：小型移动底座与功能性拟人上身及柔顺手相结合。

<a id="S006"></a>
**Source:** p.2 S006

**Original:** Most of the hardware and software technologies adopted, developed, and explicitly designed for ALTER-EGO are distributed under an open source framework and are available on the Natural Machine Motion Initiative (NMMI) website [31]. To the best of our knowledge, this is the first time that variable-stiffness technology has been built into an anthropomorphic platform with mobility capabilities and different control modalities ranging from autonomous to teleoperation.

**中文:** 为 ALTER-EGO 采用、开发并专门设计的大部分硬件和软件技术，都在开源框架下发布，并可从 Natural Machine Motion Initiative（NMMI）网站获取 [31]。据作者所知，这是可变刚度技术首次被集成到同时具有拟人结构、移动能力以及从自主控制到远程操作等多种控制模式的平台中。

<a id="F000"></a>
### Unnumbered page-1 illustration / 第 1 页未编号插图

**Source:** p.1, unnumbered magazine illustration

![Unnumbered ALTER-EGO illustration](assets/other/cover_illustration.png)

**Reading note:** This is an editorial/introductory illustration on the magazine page, not a numbered research figure. / 这是杂志版式中的导入性插图，并非论文编号图。

### Requirements Analysis / 需求分析

<a id="S007"></a>
**Source:** p.2 S007

**Original:** The design requirements of a robot used for assisting with the general activities of daily living differ substantially from those employed for industrial or specialized machines. The tasks required by the XP competition (see Table 1) can be used to distill a set of functional specifications [32] to motivate and guide the design of ALTER-EGO. Note that it is outside the scope of this article to propose a deterministic approach to the definition of robot requirements and specifications or to propose a robot that perfectly fits all these requirements.

**中文:** 用于协助一般日常生活活动的机器人，其设计要求与工业机器人或专用机器人的设计要求有显著差异。XP 竞赛要求完成的任务（见 Table 1）可用于提炼一组功能性规格 [32]，从而为 ALTER-EGO 的设计提供动机和指导。需要说明的是，本文不试图提出一种确定性的机器人需求与规格定义方法，也不试图提出一个能够完美满足全部要求的机器人。

<a id="S008"></a>
**Source:** p.2 S008

**Original:** Half of all the 28 tasks require manipulation and nearly all require physical interaction. Furthermore, the simultaneous presence of tasks 1) where the robot must push large, heavy objects, 2) where finesse and precision are important, and 3) where interaction force control is mandatory (e.g., because of safety) suggests impedance control in the robot arms.

**中文:** 28 项任务中有一半要求操作，几乎所有任务都要求物理交互。此外，任务同时包含以下三类要求：1）机器人必须推动大型重物；2）动作的灵巧性和精确性很重要；3）交互力控制是必需的（例如出于安全原因）。这说明机器人手臂需要采用阻抗控制。

<a id="S009"></a>
**Source:** p.2 S009

**Original:** Only three locomotion tasks strictly require the use of legs, making wheels a feasible, yet suboptimal, choice. Nonetheless, it is important to note these requirements in terms of agility (thus, its small footprint).

**中文:** 只有三项移动任务严格要求使用腿，因此使用轮子是可行的选择，尽管并非最优。尽管如此，仍应从灵活性的角度理解这些要求，也就是要保持较小的占地面积。

<a id="T001"></a>
### Table 1. XP 竞赛的任务与子任务

**Placed near:** p.2 S009
**Source:** p.3-p.4 T001; original table is rotated and continues across two magazine pages.

![Table 1, p.3](assets/tables/table1_p3.png)

![Table 1, p.4 continuation](assets/tables/table1_p4.png)

<a id="C001"></a>
**Original caption:** Table 1. The tasks and subtasks of the XP competition. (Source: [30]; used with permission.)

**中文表题:** 表 1。XP 竞赛中的任务与子任务。（来源：[30]；经许可使用。）

**Table reading note / 表格阅读说明:** The table records task numbers X1-X28, scenarios 1-3, required sensing and action capabilities, and operation modes. The check marks and totals are preserved in the original crops above. / 表格记录了 X1-X28 号任务、场景 1-3、所需的感知与动作能力以及操作模式；原表中的勾选项和合计数均保留在上方裁剪图中。

**Task translations / 任务中文释义:**

| ID | English task | 中文释义 |
|---|---|---|
| X1 | Greet your relative in an assisted living facility. | 在辅助生活设施中向亲属问候。 |
| X2 | Administer morning medications (pills and liquid). | 给药早晨的药物（药片和液体药物）。 |
| X3 | Push a wheelchair 5 m up a ramp to a room. | 将轮椅沿坡道向上推 5 m 到房间。 |
| X4 | Discuss with the staff the daily activities available. | 与工作人员讨论可参加的日常活动。 |
| X5 | Identify a board game such as chess, or retrieve it from a box on a shelf. Then, pick it up, carry it to a table, and set it up for play. | 识别诸如国际象棋之类的棋盘游戏，或从架子上的盒子中取出；随后拿起它，搬到桌边并摆好以便玩耍。 |
| X6 | Listen to a visiting doctor's announcement about checkups. | 听取来访医生关于检查的通知。 |
| X7 | Push your relative 5 m to the doctor's station. | 将亲属推行 5 m 到医生工作站。 |
| X8 | Read the written checkup report aloud and sign it. | 大声读出书面检查报告并签名。 |
| X9 | Push the relative back down the ramp to his or her original location. | 将亲属沿坡道推回原来的位置。 |
| X10 | Take a blanket from a wheelchair, fold it, and put it on a shelf. | 从轮椅上取下毯子，将其折叠并放到架子上。 |
| X11 | Use a shovel to load 20 kg of debris into a wheelbarrow. | 用铲子把 20 kg 碎屑装入手推车。 |
| X12 | Push the wheelbarrow 10 m to a loading area. | 将手推车推行 10 m 到装载区域。 |
| X13 | Use the shovel to unload the wheelbarrow. | 用铲子卸下手推车中的物料。 |
| X14 | Return the wheelbarrow to its original location, and listen for a call for help. | 将手推车推回原位置，并听候求助呼叫。 |
| X15 | Locate the source of the call for help. | 定位求助呼叫的来源。 |
| X16 | Walk forward on a rough dirt surface toward that location. | 在崎岖的土路上向该位置前进。 |
| X17 | Pick up a coiled rope with a weighted end. | 拿起一端带配重的盘绕绳索。 |
| X18 | Throw the weighted end of the rope toward the sound of the call for help. | 将绳索的配重端投向求助呼叫的声音方向。 |
| X19 | Turn your head and call loudly for assistance. | 转头并大声呼叫援助。 |
| X20 | Hand the unweighted end of the rope to an assistant. | 将绳索无配重的一端递给助手。 |
| X21 | Locate a set of instructions and read them aloud. | 找到一组说明并大声读出。 |
| X22 | Pour a specified quantity of fluid from one beaker to another. | 将指定量的液体从一个烧杯倒入另一个烧杯。 |
| X23 | Use a scoop to collect a specified sample of powder. | 用勺取出指定量的粉末样品。 |
| X24 | Unroll a plan on a flat table and place weights on its corners. | 在平桌上展开图纸，并在四角放置配重。 |
| X25 | Using a protractor, straightedge, and mechanical pencil, draw two lines on the plan that intersect at 45°. | 使用量角器、直尺和自动铅笔，在图纸上画出相交角为 45° 的两条线。 |
| X26 | Identify the broken plug-in components on an electrical panel. | 识别电气面板上损坏的插接式部件。 |
| X27 | Walk 6 m to a workbench and solder a wire onto it. | 走 6 m 到工作台，并在其上焊接一根导线。 |
| X28 | Return to the control panel and replace the component. | 返回控制面板并更换部件。 |

### Intelligence / 智能性

<a id="S010"></a>
**Source:** p.4 S010

**Original:** The combined requirements of all the tasks in terms of intelligence concede the unfeasibility of either a fully autonomous or fully teleoperated solution and favor a shared-autonomy approach. Indeed, although the performance of some tasks could benefit from an immersive teleoperation that enhances the pilot's sense of presence, other tasks may prefer console-based teleoperation, which minimizes fatigue, while still others favor autonomous operation.

**中文:** 从智能性角度综合考虑所有任务的要求，可以看出，完全自主或完全远程操作的方案都不现实，更合理的是共享自主性方案。确实，有些任务可以从增强操作员临场感的沉浸式远程操作中受益；另一些任务则更适合基于控制台的远程操作，以减轻疲劳；还有一些任务更适合自主运行。

### Sensing / 感知

<a id="S011"></a>
**Source:** p.4 S011

**Original:** Vision is the most important sensory system and is required for nearly every task. Nevertheless, the possibility to abstract from the subjective viewpoint (the “eyes” of the robot) a third-person point of view can benefit the operator's scene awareness in 13 of 28 tasks. Hearing (five/28 tasks) and speaking (6/28) capabilities play a fundamental role in inspection and social-interaction activities. All the tasks that involve physical interaction require touch sensing (13/28) or force sensing (17/28). Accordingly, this also raises the issue of delivering touch and force feedback to the operator's senses. It is outside the scope of this article to discuss all of these technologies in detail. The reader is encouraged to refer to [11] for a review of the technologies and to the “Pilot Interface” section for a description of the solutions integrated into the proposed system.

**中文:** 视觉是最重要的感知系统，几乎每项任务都需要视觉。不过，如果能够把主观视角（机器人的“眼睛”）抽象为第三人称视角，那么在 28 项任务中的 13 项里，操作员的场景感知会得到改善。听觉（28 项中有 5 项）和语音（6/28）能力在检查和社会交互活动中发挥基础作用。所有涉及物理交互的任务都需要触觉感知（13/28）或力感知（17/28）。因此，还需要考虑如何把触觉和力反馈传递给操作员。本文不展开讨论这些技术的全部细节；读者可参考 [11] 的技术综述，并参阅“Pilot Interface”部分，了解集成到所提系统中的解决方案。

### Pilot Station / 操作员站

<a id="S012"></a>
**Source:** p.4 S012

**Original:** The XP competition also explicitly addresses the fundamental aspects of the usability and intuitiveness of control interfaces for nontrained users. These requirements should reflect several aspects of the robot's design, thus paving the way to another relevant consideration, i.e., that the robotic system is not constituted solely by the robot itself; rather, it is combined and integrated with the infrastructure that must be used to effectively operate it - the pilot station. This underlines the relevance of aspects such as the graphical user interface and its software capabilities, the ergonomics of the input devices, the time needed to set up the system, and the overall weight of the wearable devices used by the operator (especially in immersive teleoperated modalities).

**中文:** XP 竞赛还明确关注非训练用户所使用控制接口的可用性和直观性等基本问题。这些要求应反映机器人的若干设计方面，并引出另一个重要认识：机器人系统并不只由机器人本体构成；它还必须与用于有效操作机器人的基础设施结合和集成，即操作员站。这凸显了图形用户界面及其软件能力、输入设备的人机工效学、系统设置所需时间，以及操作员使用的可穿戴设备总重量等因素的重要性，尤其是在沉浸式远程操作模式中。

### ALTER-EGO overview / ALTER-EGO 概览

<a id="S013"></a>
**Source:** p.4 S013

**Original:** Figure 2(a) presents a few kinematic and mechatronic details of ALTER-EGO. The mobile platform has two independent wheels actuated by two dc motors. The upper body has 5 degrees of freedom (DoF) for each of the two arms and integrates a robotic head mounted on a 2-DoF neck, which allows the head to pan and tilt, as shown in Figure 2(a) and (b). The neck is mounted on the trunk. All of the upper body's DOF are actuated by VSA units that enable safe, physical interaction with the environment as well as people. The presence of VSA units also increases the robustness of the system both in terms of control (because the soft behavior mitigates passively external disturbances, e.g., from balance control) and mechanical failures (e.g., during a fall). Moreover, the adoption of the same actuation units in all of the robot's joints yields a simple modular architecture (i.e., all of the joints are assembled with the same interconnection flanges), which facilitates reconfiguration and parts substitution (e.g., in the event of a failure).

**中文:** 图 2(a) 展示了 ALTER-EGO 的一些运动学和机电细节。移动平台有两个彼此独立的轮子，分别由两个直流电机驱动。上身的两条手臂各有 5 个自由度，并集成了一个安装在 2 自由度颈部上的机器人头部；如图 2(a)、(b) 所示，该颈部使头部能够左右转动和俯仰。颈部安装在躯干上。上身所有自由度都由 VSA 单元驱动，从而能够与环境及人安全地进行物理交互。采用 VSA 单元还提高了系统的鲁棒性：在控制方面，柔顺行为可以被动缓解外部扰动（例如平衡控制引起的扰动）；在机械方面，也有助于减轻故障影响（例如跌倒时）。此外，机器人所有关节采用相同的驱动单元，形成了简单的模块化架构，即所有关节都使用相同的互连法兰装配，从而便于重新配置和替换部件（例如发生故障时）。

<a id="F002"></a>
### Fig. 2. ALTER-EGO 的机电结构、DH 参数与软件架构

**Placed near:** p.5 S015
**Source:** p.5 C003

![Fig. 2](assets/figures/fig2.png)

<a id="C003"></a>
**Original caption:** Figure 2. (a) and (b) The mechatronic architecture of ALTER-EGO. (c) and (d) The Denavit-Hartenberg parameters of the arms and the overall software architecture. $l_i$ represents the length of ith link, and $a_i$, $\alpha_i$, $d_i$, and $\theta_i$ are the Denavit-Hartenberg parameters of the ith link [10]. IMU: inertial measurement unit; ROS: Robot Operating System; API: application programming interface; IK: inverse kinematics. (Source: [30]; used with permission.)

**中文图注:** 图 2。(a)、(b) ALTER-EGO 的机电结构；(c)、(d) 手臂的 Denavit-Hartenberg 参数和总体软件架构。$l_i$ 表示第 $i$ 条连杆的长度，$a_i$、$\alpha_i$、$d_i$ 和 $\theta_i$ 是第 $i$ 条连杆的 Denavit-Hartenberg 参数 [10]。IMU：惯性测量单元；ROS：机器人操作系统；API：应用程序编程接口；IK：逆运动学。（来源：[30]；经许可使用。）

**Reading note:** Panel (c) preserves the right-arm parameter table, while panel (d) shows the stack from motors and firmware through the ROS modules to the operator control unit. / (c) 保留了右臂参数表，(d) 显示从电机、固件到 ROS 模块及操作员控制单元的软件层级。

<a id="S014"></a>
**Source:** p.5 S014

**Original:** Two soft, anthropomorphic hands complete the robot's upper body design.

**中文:** 两只柔性拟人手完善了机器人的上身设计。

### Locomotion and physical specifications / 移动与物理规格

<a id="S015"></a>
**Source:** p.5 S015

**Original:** The robot's footprint clearance is 500-mm wide and 260-mm deep, while the robot's height is 1,000 mm. The robot weighs approximately 21 kg, and its two-handed payload is 3 Kg, yielding a 0.143 weight-to-payload ratio. Its average speed is 0.25 m/s. The autonomy of the robot, in combined usage condition, ranges between 4 and 6 h. The following subsections briefly describe the manipulation, locomotion, and sensing subsystems composing ALTER-EGO. Note that 1) all details about the building blocks forming ALTER-EGO and 2) all instruction on how to assemble, run, and operate the system can be downloaded from the NMMI website and GitHub webpage [32] (see also [7]).

**中文:** 机器人的占地空间宽 500 mm、深 260 mm，高度为 1,000 mm。机器人重量约为 21 kg，双手有效负载为 3 kg，因此重量与负载之比为 0.143。平均速度为 0.25 m/s。在综合使用条件下，机器人的续航时间为 4-6 h。下文各小节将简要介绍构成 ALTER-EGO 的操作、移动和感知子系统。需要注意的是：1）构成 ALTER-EGO 的各个构建模块的全部细节，以及 2）系统的装配、运行和操作说明，均可从 NMMI 网站和 GitHub 页面下载 [32]（另见 [7]）。

<a id="S016"></a>
**Source:** p.5 S016

**Original:** The robot's lower body is composed of a rigid frame connecting the upper body to a two-wheeled mobile base, as displayed in Figure 2(a) and (b). Although most of the robots used in structured scenarios have at least three wheels to help avoid stability problems, this often leads to the introduction of tradeoffs between mobility and agility, i.e., the adoption of small wheels to minimize their footprint, which eliminates the system's ability to deal with obstacles. For this reason, we chose to equip ALTER-EGO with only two wheels to avoid the tradeoffs discussed in [12] and [13]. Each wheel has a diameter of 260 mm; is equipped with a low-profile, off-road tire; and is powered by a 12-V Maxon dc motor (DCX 22L) in combination with a Harmonic Drive gearbox (160:1). The lower body of the robot [see Figure 2(b)] includes a nine-axis inertial measurement unit (IMU) (MPU-9250 TDK InvenSense) between the two wheels, to estimate the pitch angle, and two magnetic encoders (AS5045 Austrian Microsystems), to measure wheel rotation. Additionally, two Sharp infrared GP2Y0A02YK0F sensors are integrated into the base to prevent collision with low-clearance obstacles.

**中文:** 机器人的下身由刚性框架构成，该框架把上身连接到双轮移动底座，如图 2(a)、(b) 所示。尽管结构化场景中使用的大多数机器人至少有三个轮子，以帮助避免稳定性问题，但这通常会引入移动性与灵活性之间的折中：为了减小占地面积而采用小轮子，却会削弱系统处理障碍物的能力。因此，为避免 [12]、[13] 中讨论的折中，我们选择只为 ALTER-EGO 配置两个轮子。每个轮子的直径为 260 mm，装有低断面越野轮胎，并由 12 V Maxon 直流电机（DCX 22L）和 Harmonic Drive 减速箱（160:1）组合驱动。机器人下身（见图 2(b)）在两个轮子之间安装了九轴惯性测量单元（IMU）（MPU-9250 TDK InvenSense），用于估计俯仰角；同时装有两个磁编码器（AS5045 Austrian Microsystems），用于测量轮子的转动。此外，底座集成了两个 Sharp GP2Y0A02YK0F 红外传感器，用于防止与低净空障碍物碰撞。

<a id="S017"></a>
**Source:** p.6 S017

**Original:** Independently controlling the two wheels allows the system to move forward and backward and to turn in place. Furthermore, the possibility of the robot adapting its pitch angle to the dynamical conditions improves its execution of push/pull tasks as well as its tackling of slopes (see the “Experiments and Discussion” section for more details).

**中文:** 对两个轮子进行独立控制，使系统能够前进、后退并原地转向。此外，使机器人能够根据动力学条件调整俯仰角，有助于完成推/拉任务以及应对斜坡（详见“Experiments and Discussion”部分）。

<a id="S018"></a>
**Source:** p.6 S018

**Original:** Note that this solution is not devoid of drawbacks; indeed, the platform requires active balance stabilization, which may incur instability issues and increase its energy consumption. Additionally, balance control may also have consequences on the manipulation capabilities of the system. Accordingly, changes to the robot's center of mass (CoM) can affect the Cartesian position and orientation of the head and end effectors. These effects can have negative consequences (e.g., in a teleoperation setting; see also the “Operating Modes” section) and make manipulation more difficult unless 1) careful control ensures that the end effectors are not affected by these oscillations or 2) the pilot actively manages such changes. See the “Experiments and Discussions” section for more details.

**中文:** 需要注意的是，这种方案并非没有缺点；事实上，该平台需要主动平衡稳定，这可能引发不稳定问题并增加能耗。此外，平衡控制也可能影响系统的操作能力。因此，机器人质心（CoM）的变化会影响头部和末端执行器的笛卡尔位置与姿态。这些影响可能带来负面后果（例如在远程操作场景中；另见“Operating Modes”部分），并使操作更加困难，除非满足以下至少一种条件：1）通过精细控制确保末端执行器不受这些振荡影响；或 2）由操作员主动管理这些变化。更多细节见“Experiments and Discussions”部分。

### Manipulation / 操作

<a id="S019"></a>
**Source:** p.6 S019

**Original:** A revised release of the University of Pisa/Italian Institute of Technology's SoftHand (SH) [7] was specifically designed for ALTER-EGO. SH's purpose is to match the robot's payload and dimensions (i.e., a weight of 0.29 kg and a length of 130 mm). The SH is a heavily underactuated anthropomorphic hand (19 DoF actuated by a single motor), capable of self-adapting its grasp to objects of different shape, size, and weight and interacting with people and their environment safely and effectively.

**中文:** 比萨大学/意大利理工学院的 SoftHand（SH）修订版 [7] 是专门为 ALTER-EGO 设计的。SH 的目标是匹配机器人的有效负载和尺寸（重量 0.29 kg、长度 130 mm）。SH 是一只高度欠驱动的拟人手（19 个自由度由一个电机驱动），能够针对不同形状、尺寸和重量的物体自适应调整抓握，并安全、有效地与人和环境交互。

<a id="S020"></a>
**Source:** p.6 S020

**Original:** The main actuators of ALTER-EGO's arms and neck are 12-qb move units, which are modular VSAs derived from the VSA-CUBE design [7], that implement an agonistic-antagonistic principle using two motors connected to the output shaft through a nonlinear elastic transmission. Each module can mechanically change its output shaft position and is mechanically set a given output shaft-stiffness profile.

**中文:** ALTER-EGO 手臂和颈部的主要执行器是 12-qb move 单元。这些单元是源自 VSA-CUBE 设计 [7] 的模块化 VSA，通过两个电机和非线性弹性传动连接到输出轴，实现协同-拮抗驱动原理。每个模块都可以机械地改变输出轴位置，并可机械设定输出轴的刚度曲线。

<a id="S021"></a>
**Source:** p.6 S021

**Original:** The anthropomorphic structure of the upper body is achieved by connecting both arms to a frame, which, in turn, is mounted on the mobile base [Figure 2(a) and (b)]. Each arm presents a relative angle with respect to the frame so as to maximize the common manipulation in the workspace, a solution commonly used in other bimanual systems (e.g., [4]). Each arm has 5 DoF; for this reason, the robot may incur unreachable configurations and singularities, especially when teleoperated. Such kinematics are the result of a tradeoff between weight, complexity, arm length, and the actuators' maximum payload. Note that different, more anthropomorphic shoulder configurations that include increased payload capabilities are currently under investigation (refer to [15] for more details).

**中文:** 将两条手臂连接到一个框架，再把框架安装在移动底座上，实现了上身的拟人结构[图 2(a)、(b)]。每条手臂相对于框架都有一个相对角度，以最大化工作空间中共同操作的区域；其他双臂系统也常采用这种方案（例如 [4]）。每条手臂有 5 个 DoF；因此，机器人可能出现不可达构型和奇异位形，尤其是在远程操作时。这种运动学结构是在重量、复杂度、手臂长度和执行器最大负载之间进行折中的结果。需要注意的是，作者正在研究包含更大负载能力、更加拟人化的肩部构型，详见 [15]。

<a id="S022"></a>
**Source:** p.6 S022

**Original:** Assuming the preferred end-effector pose (position and orientation), the required joint positions of each arm are computed via a closed-loop, inverse-kinematics (IK) algorithm with damped pseudoinverse [10]. The orientation of the pilot's head is mapped directly to the corresponding Euler angles (pitch and yaw) of the robot's neck, as depicted in Figure 3(a). For each qb move of the upper body, a position/stiffness control is used. Given the elastic nature of VSA, to control the position of the robot arms in feedforward mode without a steady-state error, it is necessary to compute both the desired actuator position and the expected load torque, τ, to compensate for the expected elastic deflection, δ. The vector τ can be easily extracted by the robot dynamics as

**中文:** 在给定期望末端执行器位姿（位置和姿态）的情况下，每条手臂所需的关节位置通过带阻尼伪逆的闭环逆运动学（IK）算法计算 [10]。操作员头部的姿态直接映射到机器人颈部相应的欧拉角（俯仰和偏航），如图 3(a) 所示。对于上身的每个 qb move 单元，采用位置/刚度控制。由于 VSA 具有弹性，如果要在前馈模式下控制机器人手臂位置且不产生稳态误差，就必须同时计算期望执行器位置和预期负载力矩 $	au$，以补偿预期的弹性挠度 $delta$。根据机器人动力学，可以容易地得到向量 $	au$：

<a id="E001"></a>
**Source:** p.6 E001 · Eq. (1)

$$
\tau = B(q)\ddot{q} + C(q,\dot{q})\dot{q} + G(q) - J_e^{T} f_e,
$$

**中文说明:** 该式给出机器人动力学中的负载力矩。$B(q)$ 表示与构型相关的惯性项，$C(q,\dot{q})\dot{q}$ 表示速度相关项，$G(q)$ 表示重力项，$J_e^{T}f_e$ 表示末端执行器外力通过雅可比转置映射到关节空间的项。符号按原文保留。

<a id="S023"></a>
**Source:** p.6 S023

**Original:** while the expected deflection can be reconstructed by inverting the elastic model of the qb move,

**中文:** 而预期挠度可以通过对 qb move 的弹性模型求逆来重建：

<a id="E002"></a>
**Source:** p.6 E002 · Eq. (2)

$$
\tau = k_1\sinh\left(a_1(q-\theta_1)\right) + k_2\sinh\left(a_2(q-\theta_2)\right),
$$

**中文说明:** 这里 $k_1,k_2,a_1,a_2$ 是数据表中给出的模型参数，$q$ 是连杆位置，$	heta_1$ 和 $	heta_2$ 是两个电机的位置。该式描述两个电机通过非线性弹性传动共同产生输出力矩。

<a id="S024"></a>
**Source:** p.6 S024

**Original:** Because k1 ≃ k2 = k and a1 ≃ a2 = a, it is possible to write τ as

**中文:** 由于 $k_1 \simeq k_2 = k$ 且 $a_1 \simeq a_2 = a$，可以将 $	au$ 写成：

<a id="E003"></a>
**Source:** p.6 E003 · Eq. (3)

$$
\tau = 2k\cosh(a\theta_{\mathrm{pre}})\sinh\left(a(q-\theta_{\mathrm{eq}})\right),
$$

**中文说明:** 该对称化形式将双电机参数压缩为共同刚度尺度 $k$ 和共同弹性尺度 $a$，并引入预紧角与平衡角。

<a id="E004"></a>
**Source:** p.6 E004 · Eq. (4)

$$
\delta = q-\theta_{\mathrm{eq}},\qquad
\theta_{\mathrm{pre}} = \frac{\theta_1-\theta_2}{2},\qquad
\theta_{\mathrm{eq}} = \frac{\theta_1+\theta_2}{2}.
$$

**中文说明:** $\delta$ 是挠度，$\theta_{\mathrm{pre}}$ 是刚度调节角，$\theta_{\mathrm{eq}}$ 是平衡角。给定期望的 $\theta_{\mathrm{pre}}$ 和 $q$，可由式 (3) 重建预期挠度 $\delta=\delta(q,\theta_{\mathrm{pre}})$；进而得到预期电机轨迹 $\theta_{\mathrm{eq}}=q+\delta(q,\theta_{\mathrm{pre}})$。图 3(b) 展示了这种补偿方案；为简化起见，文中取 $\tau \simeq G(q)$。

## Control / 控制

<a id="S025"></a>
**Source:** p.7 S025

**Original:** In a simplified model, the state-space of the lower body subsystem has three generalized coordinates $(\theta, \psi, \phi)$, which describe the semisum of the wheel angles and the robot's yaw and tilt angles, respectively. Figure 3(a) expresses the balance control scheme, with $u=[u_1\ u_2]$ representing the torque control for the wheels, and $e=r-y$ being the error between the current $y$ and required $r$ robot states. The anticipated state can also be modified by the operator using the available teleoperation devices (see the “Operating Modes” section). A classical LQR method can be applied to stabilize the wheel base (as in [16] and [17]), which can be simply designed but does not take advantage of the arms' fast-balancing motions. This method is suitable when arms are not available to balance (e.g., because they are used in other tasks) and provides good balancing performance, as presented in the “Experiments and Discussion” section.

**中文:** 在一个简化模型中，下身子系统的状态空间具有三个广义坐标 $(\theta, \psi, \phi)$，分别描述轮子角度的半和、机器人的偏航角以及倾斜角。图 3(a) 表示平衡控制方案，其中 $u=[u_1\ u_2]$ 表示轮子的力矩控制，$e=r-y$ 表示当前机器人状态 $y$ 与期望状态 $r$ 之间的误差。操作员也可以通过可用的远程操作设备修改预期状态（见“Operating Modes”部分）。可以使用经典 LQR 方法稳定轮式底座（如 [16]、[17]），这种方法容易设计，但没有利用手臂的快速平衡运动。当手臂无法参与平衡（例如正在执行其他任务）时，该方法仍然适用，并能提供良好的平衡性能，正如“Experiments and Discussion”部分所示。

<a id="S026"></a>
**Source:** p.7 S026

**Original:** To improve independent LQR control performance, in [14], we developed a new whole-body dynamic control system that computes the joint actuation torques $\tau$, given a preferred joint-space motion to track. To achieve this, a computed torque-control law in the quasi-velocity vector was developed, starting from the underactuated and kinematically constrained model of ALTER-EGO. Note that the model discussed in [14] does not take into account the variable stiffness of the robot's upper body explicitly, which remains an open subject of research.

**中文:** 为了提高独立 LQR 控制的性能，我们在 [14] 中开发了一种新的全身动力学控制系统：给定需要跟踪的期望关节空间运动，系统计算关节驱动力矩 $\tau$。为此，作者从 ALTER-EGO 的欠驱动且受运动学约束的模型出发，在准速度向量上构造了计算力矩控制律。需要注意的是，[14] 讨论的模型没有显式考虑机器人上身的可变刚度，这仍是一个开放的研究问题。

<a id="S027"></a>
**Source:** p.7 S027

**Original:** The idea of [14] follows in brief. Let $q$ be the generalized coordinates of the robot, $n$ the number of DoF, $n_{fb}$ the number of independent variables needed to describe the floating base motion, and $n_c$ the number of constraints acting on the robot, e.g., due to base kinematics. Then, let $\nu\in\mathbb{R}^{n+n_{fb}-n_c}$ be the quasi-velocity vector so that $\dot{q}=S(q)\nu$. Consider the error dynamics

**中文:** [14] 的基本思路如下。令 $q$ 为机器人的广义坐标，$n$ 为 DoF 数，$n_{fb}$ 为描述浮动基座运动所需的独立变量数，$n_c$ 为作用于机器人的约束数，例如由底座运动学引起的约束。再令 $\nu\in\mathbb{R}^{n+n_{fb}-n_c}$ 为准速度向量，使得 $\dot{q}=S(q)\nu$。考虑如下误差动力学：

<a id="E005"></a>
**Source:** p.7 E005 · Eq. (5)

$$
\dot{\nu}^{d}-\dot{\nu}+K_d(\nu^{d}-\nu)+K_p\int_{0}^{t}(\nu^{d}-\nu)=0.
$$

**中文说明:** $K_p$ 和 $K_d$ 是正定增益矩阵，$\nu^d$ 是期望准速度。该式把准速度误差、误差变化率和积分误差结合起来，形成用于跟踪的误差动力学。

<a id="S028"></a>
**Source:** p.8 S028

**Original:** The resulting generalized torques are computed as a function of the quasi-velocities vector:

**中文:** 得到的广义力矩作为准速度向量的函数计算如下：

<a id="E006"></a>
**Source:** p.8 E006 · Eq. (6)

$$
\tilde{\tau}=\tilde{M}\left(\dot{\nu}^{d}+K_d(\nu^{d}-\nu)+K_p\int_{0}^{t}(\nu^{d}-\nu)\right)+\tilde{c}.
$$

**中文说明:** 原文进一步定义 $\tilde{c}=S^{T}(q)(M(q)\dot{S}(q,\nu)\nu+C(q,\dot{q})S(q)\nu+G(q))$，以及 $\tilde{M}=S^{T}(q)M(q)S(q)$。这样得到的广义力矩与设计施加的约束相容。作者在 [14] 中说明，实际关节力矩 $\tau$ 可以由式 (6) 获得，从而实现全身控制。

<a id="S029"></a>
**Source:** p.8 S029

**Original:** The method was tested in several experiments to stabilize the robot around an equilibrium position in the presence of static and dynamic disturbances [see Figure 4(c) and (d)] as well as in tracking some required motions during the execution of a task that included physical interaction with the environment.

**中文:** 作者通过多项实验测试了该方法：一方面，在静态和动态扰动存在时，将机器人稳定在平衡位置附近[见图 4(c)、(d)]；另一方面，在包含环境物理交互的任务执行过程中，跟踪若干指定运动。

<a id="F003"></a>
### Fig. 3. ALTER-EGO 控制框图

**Placed near:** p.7 S026
**Source:** p.7 C004

![Fig. 3](assets/figures/fig3.png)

<a id="C004"></a>
**Original caption:** Figure 3. The ALTER-EGO control schema. (a) The full-state feedback control system obtained with LQR. (b) The whole-body control schema. FK: forward kinematics.

**中文图注:** 图 3。ALTER-EGO 控制方案。(a) 使用 LQR 得到的全状态反馈控制系统；(b) 全身控制方案。FK：正向运动学。

**Reading note:** Panel (a) separates arm/head kinematic compensation from mobile-body LQR balance control; panel (b) shows dynamic control and quasi-velocity computation. / (a) 将手臂/头部运动学补偿与移动下身的 LQR 平衡控制分开；(b) 展示动力学控制与准速度计算。

## Sensing / 感知

<a id="S030"></a>
**Source:** p.8 S030

**Original:** The head is equipped with a Stereolabs Zed Camera [33]. This is a passive red-green-blue-depth (RGB-D) camera that can acquire images, videos, and a depth point cloud of the scene. Images can be streamed to either the pilot station monitor or to the VR headset when the robot is used in teleoperation mode (see the “Operating Modes” section). ALTER-EGO is equipped with a set of basic vision tools that enable it to recognize objects and markers. A wrapper is available, making the Zed stereo camera usable in the Robot Operating System (ROS) environment by providing access to stereo images, the depth map, the 3D point cloud, and 6-DoF tracking. Currently, several software systems exploit state-of-the-art object-detection algorithms. For this purpose, Detectron [34] has been used on ALTER-EGO. The head architecture is completed by a 10-W speaker and a multidirectional, six-channel microphone.

**中文:** 机器人头部配备 Stereolabs Zed Camera [33]。这是一款被动式红绿蓝-深度（RGB-D）相机，可以获取场景图像、视频和深度点云。机器人处于远程操作模式时，图像可以传输到操作员站显示器或 VR 头戴设备（见“Operating Modes”部分）。ALTER-EGO 配备了一组基础视觉工具，用于识别物体和标记。通过一个封装器，Zed 双目相机可以在机器人操作系统（ROS）环境中使用，并提供对双目图像、深度图、三维点云和 6-DoF 跟踪的访问。目前，许多软件系统都利用先进的目标检测算法；ALTER-EGO 使用 Detectron [34] 完成这一任务。头部架构还包括一个 10 W 扬声器和一个多方向六通道麦克风。

<a id="S031"></a>
**Source:** p.9 S031

**Original:** Both hands are equipped with position and current sensors on their motors to reconstruct the applied grasp force. Additionally, the hands' fingertips can be conveniently equipped with IMUs to allow for the estimation of contact events and surface roughness, as described in [18]. Each actuation module is equipped with three position sensors (on the two prime movers and on the output shaft) to measure the spring deflection. This measurement can be used to estimate the torque applied by each motor and, in turn, to estimate the external wrenches applied to the end effectors, using the least-square approach explained in [19].

**中文:** 两只手的电机上都装有位置传感器和电流传感器，用于重建施加的抓握力。此外，手指尖可以方便地安装 IMU，以估计接触事件和表面粗糙度，如 [18] 所述。每个驱动模块都配有三个位置传感器（分别位于两个原动件和输出轴上），用于测量弹簧挠度。该测量值可用于估计每个电机施加的力矩，进而采用 [19] 介绍的最小二乘方法，估计作用在末端执行器上的外部力-力矩合量。

## Mechatronics, Software, and Communication Architecture / 机电、软件与通信架构

<a id="S032"></a>
**Source:** p.9 S032

**Original:** ALTER-EGO is equipped with a computational unit (NUC i5 compact computer) for managing the control architecture, vision streaming, and compression algorithms. The low-level communication layer between the actuation units, wheels, sensors, and end effectors is based on an RS485 protocol (2 Mb/s).

**中文:** ALTER-EGO 配备了一个计算单元（NUC i5 紧凑型计算机），用于管理控制架构、视觉流传输和压缩算法。驱动单元、轮子、传感器和末端执行器之间的低层通信基于 RS485 协议，速率为 2 Mb/s。

<a id="S033"></a>
**Source:** p.9 S033

**Original:** The robot is equipped with two 24-V batteries that have a total capacity of 48,000 mAh and a peak current of 100 A. A dedicated 12-V battery with a total capacity of 30,000 mAh is used to supply the computational units.

**中文:** 机器人配有两个 24 V 电池，总容量为 48,000 mAh，峰值电流为 100 A。另有一块专用的 12 V 电池，总容量为 30,000 mAh，用于为计算单元供电。

<a id="S034"></a>
**Source:** p.9 S034

**Original:** The ALTER-EGO software architecture is organized into four layers, as displayed in Figure 2(d). The first layer is constituted by the firmware running in each board used to control the joints, end effectors, motor wheels, and sensors. A second layer, also embedded in the electronic boards, manages the communication bus among the different devices that constitute the robot's hardware. A third software layer (i.e., an application programming interface) supports the communication between the second layer and the ROS modules. Each ROS module manages the nodes used for the base motion, balancing, arms-IK, feedforward gravity compensation, end-effector wrench estimation, localization, mapping, navigation, and vision. Finally, a fourth layer is used to communicate with the pilot station and manages the robot in both autonomous and teleoperated modes.

**中文:** 如图 2(d) 所示，ALTER-EGO 的软件架构分为四层。第一层是运行在各个电路板上的固件，用于控制关节、末端执行器、驱动轮和传感器。第二层同样嵌入电子电路板中，管理构成机器人硬件的不同设备之间的通信总线。第三层软件（即应用程序编程接口）支持第二层与 ROS 模块之间的通信。每个 ROS 模块管理用于底座运动、平衡、手臂 IK、重力前馈补偿、末端执行器力-力矩合量估计、定位、建图、导航和视觉的节点。最后，第四层用于与操作员站通信，并管理机器人的自主模式和远程操作模式。

<a id="F004"></a>
### Fig. 4. 平衡与扰动实验

**Placed near:** p.8 S029
**Source:** p.8 C005

![Fig. 4](assets/figures/fig4.png)

<a id="C005"></a>
**Original caption:** Figure 4. (a) The robot balancing at different slope angles. (b) The robot balancing in the presence of static disturbances. (c) The LQR control algorithm; the robot balancing in the presence of external impulsive disturbances. (d) The whole-body control algorithm; the robot balancing in the presence of dynamic disturbances.

**中文图注:** 图 4。(a) 机器人在不同坡度角下保持平衡；(b) 机器人在静态扰动存在时保持平衡；(c) LQR 控制算法，机器人在外部冲击扰动存在时保持平衡；(d) 全身控制算法，机器人在动态扰动存在时保持平衡。

**Reading note:** The panels move from slope adaptation to static loads, impulsive disturbances, and dynamic disturbances. / 各分图依次展示坡度适应、静态负载、冲击扰动和动态扰动。

<a id="F005"></a>
### Fig. 5. ALTER-EGO 的输入/输出接口与操作员站

**Placed near:** p.9 S034
**Source:** p.9 C006

![Fig. 5](assets/figures/fig5.png)

<a id="C006"></a>
**Original caption:** Figure 5. (a) ALTER-EGO's input and output interfaces. (b) The pilot station used for autonomous and teleoperation mode and (c) the pilot station used for immersive teleoperation mode.

**中文图注:** 图 5。(a) ALTER-EGO 的输入和输出接口；(b) 用于自主模式和远程操作模式的操作员站；(c) 用于沉浸式远程操作模式的操作员站。

**Reading note:** The figure maps robot-side outputs and operator-side devices, including stereo vision, head orientation, arm positions, hand closure, stiffness, touch feedback, velocity reference, VR, Myo, IMU, haptic feedback, and Wii balance input. / 该图对应机器人端输出与操作员端设备，包括双目视觉、头部姿态、手臂位置、手部闭合、刚度、触觉反馈、速度参考，以及 VR、Myo、IMU、触觉反馈和 Wii 平衡板输入。

<a id="S035"></a>
**Source:** p.10 S035

**Original:** A dedicated communication framework enables the exchange of data between the robot and pilot station. A 5-GHz wireless connection allows for bilateral communication with the pilot station for the streaming of control (e.g., sensors measurements and references positions) and vision data. An ROS communication framework is used to send commands to the robot and receive data from it. A dedicated User Datagram Protocol connection was developed to foster video data exchanges between the robot and pilot station (see the “Operating Modes” section). At a frequency of 100 Hz, the pilot station sends the robot references of head orientation, arm joint position and stiffness, hands closure, and velocity vector for the mobile base (Figure 5). The robot sends back a stream of images at a frequency of nearly 25 Hz; they are, however, limited by capturing and processing delays. The measured average ping time between the pilot station and the robot is 15 ms, while the average bandwidth used for both motion commands and image streaming was measured; accordingly, bandwidths of 1 Mb/s and 18 Mb/s, respectively, were used. In some experiments, Internet infrastructures were employed to connect the pilot station to the robot operation site, where it is completed by 5-GHz Wi-Fi.

**中文:** 专用通信框架支持机器人与操作员站之间的数据交换。5 GHz 无线连接使操作员站能够与机器人进行双向通信，用于传输控制数据（例如传感器测量值和参考位置）以及视觉数据。ROS 通信框架用于向机器人发送指令并接收数据。作者还开发了专用的用户数据报协议（UDP）连接，以促进机器人和操作员站之间的视频数据交换（见“Operating Modes”部分）。操作员站以 100 Hz 的频率向机器人发送头部姿态、手臂关节位置和刚度、手部闭合状态，以及移动底座速度向量的参考值（图 5）。机器人以接近 25 Hz 的频率回传图像流，但受到采集和处理延迟的限制。操作员站与机器人之间测得的平均 ping 时间为 15 ms；对运动指令和图像流所使用的平均带宽进行测量后，分别采用了 1 Mb/s 和 18 Mb/s 的带宽。在部分实验中，作者使用互联网基础设施连接操作员站和机器人工作现场，并在现场通过 5 GHz Wi-Fi 完成连接。

## Operating Modes / 操作模式

### Autonomous Mode / 自主模式

<a id="S036"></a>
**Source:** p.10 S036

**Original:** ALTER-EGO has two main operation modalities. In autonomous mode, ALTER-EGO can be used in a completely independent fashion, leveraging core functionalities embedded in its local computational unit. For autonomous navigation, simultaneous localization and mapping (SLAM) algorithms are used. More specifically, an RGB-D graph SLAM approach based on a global Bayesian loop-closure detector is employed, i.e., Real-Time Appearance-Based Mapping (RTAB-MAP) [20]. Although the use of RTAB-MAP allows ALTER-EGO to be localized accurately, camera occlusion and slow update rate (10 Hz) impede robot localization in some cases. To solve this problem, a particle filter [21] is integrated into the system. Ultimately, the wheel velocity (measured by encoders) and visual odometry (obtained by RTAB-MAP) were used for prediction and correction phases, respectively. Particle filters are employed to ascertain the robot's current position and orientation. This information is used as feedback for waypoint-based navigation. For this purpose, the pure pursuit method [22] was applied to ALTER-EGO. ALTER-EGO is also equipped with autonomous grasping and manipulation capabilities, which make it capable of grasping objects with two hands, using both vision and end-effector wrench estimation. An Aruco [35] ROS package was utilized to determine an object's position.

**中文:** ALTER-EGO 有两种主要操作模式。在自主模式下，ALTER-EGO 可以完全独立运行，利用其本地计算单元中嵌入的核心功能。自主导航使用同时定位与建图（SLAM）算法。更具体地说，系统采用基于全局贝叶斯闭环检测器的 RGB-D 图 SLAM 方法，即 Real-Time Appearance-Based Mapping（RTAB-MAP）[20]。尽管 RTAB-MAP 能够实现准确定位，但相机遮挡和较慢的更新速率（10 Hz）在某些情况下会妨碍机器人定位。为解决这一问题，系统集成了粒子滤波器 [21]。最终，轮速（由编码器测量）和视觉里程计（由 RTAB-MAP 获得）分别用于预测阶段和校正阶段。粒子滤波器用于确定机器人的当前位置和姿态，该信息作为基于航点导航的反馈。为此，作者将纯跟踪方法 [22] 应用于 ALTER-EGO。ALTER-EGO 还具备自主抓取和操作能力，可以结合视觉与末端执行器力-力矩合量估计，使用双手抓取物体。系统使用 Aruco [35] ROS 软件包确定物体位置。

<a id="S037"></a>
**Source:** p.11 S037

**Original:** ALTER-EGO embeds an autonomous modality that enables the execution of collaborative tasks together with humans. In this operational mode, ALTER-EGO executes cooperative manipulation tasks, e.g., handling an object in cooperation with humans or walking hand in hand (Figure 6). To execute these kinds of tasks, an end-effector wrench estimation is used. In particular, the force in $y$ direction and the torque around $z$ direction are used as the desired linear and angular velocity, respectively, to follow the direction imposed by the human [see Figure 6(b) and (c)].

**中文:** ALTER-EGO 内置了一种自主模式，可以与人一起执行协作任务。在该操作模式下，ALTER-EGO 执行协作操作任务，例如与人共同搬运物体或手拉手行走（图 6）。执行这类任务时，系统使用末端执行器力-力矩合量估计。具体而言，$y$ 方向的力和绕 $z$ 方向的力矩分别被用作期望线速度和角速度，使机器人跟随人所施加的方向[见图 6(b)、(c)]。

<a id="F006"></a>
### Fig. 6. ALTER-EGO 的自主动作

**Placed near:** p.10 S036
**Source:** p.10 C007

![Fig. 6](assets/figures/fig6.png)

<a id="C007"></a>
**Original caption:** Figure 6. ALTER-EGO's autonomous actions. ALTER-EGO (a) pushing a heavy box (10 kg), (b) carrying a heavy box in collaboration mode with a human, and (c) following a human operator.

**中文图注:** 图 6。ALTER-EGO 的自主动作。ALTER-EGO (a) 推动重箱子（10 kg）；(b) 在与人协作的模式下搬运重箱子；(c) 跟随人类操作员。

**Reading note:** The figure covers autonomous pushing, human-robot collaborative carrying, and human following. / 该图涵盖自主推箱、人与机器人协作搬运，以及跟随人类。

### Teleoperation Mode / 远程操作模式

<a id="S038"></a>
**Source:** p.11 S038

**Original:** ALTER-EGO can be teleoperated from a console or through an immersive VR setup. In the latter case, a motion-capture system is needed to map the pilot's body movements to the robot's kinematics. A key feature of the proposed teleoperation framework is its lightweight, reduced encumbrance and ease of wear. In the standard setup, two Myo armbands per arm (one placed on the forearm and one on the upper arm) plus an additional IMU placed on the pilot's hand permit the reconstruction of the Cartesian position and orientation of the pilot's limbs. Let ${}^{i}T_{j}\in\mathbb{R}^{4\times4}$ be the homogeneous transformation from joint $i$ to joint $j$; the homogeneous transformation ${}^{S}T_{H}$ from the shoulder to the hand is given as

**中文:** ALTER-EGO 可以通过控制台进行远程操作，也可以通过沉浸式 VR 设置进行远程操作。在后者中，需要使用运动捕捉系统，将操作员的身体运动映射到机器人的运动学结构。所提出远程操作框架的一个关键特点是重量轻、负担小且易于穿戴。在标准设置中，每条手臂使用两个 Myo 臂带（一个放在前臂，另一个放在上臂），并在操作员手上额外放置一个 IMU，从而可以重建操作员肢体的笛卡尔位置和姿态。令 ${}^{i}T_{j}\in\mathbb{R}^{4\times4}$ 表示从关节 $i$ 到关节 $j$ 的齐次变换，则从肩部到手部的齐次变换 ${}^{S}T_{H}$ 为：

<a id="E007"></a>
**Source:** p.11 E007 · Eq. (7) · medium confidence; original crop retained

![Original equation E007](assets/equations/E007.png)

**低置信度转写 / Low-confidence transcription:**

$$
{}^{S}T_{H} = {}^{S}T_{E}\,{}^{E}T_{W}\,{}^{W}T_{H}.
$$

**中文说明:** 原式用肩部 $S$、肘部 $E$、腕部 $W$ 和手部 $H$ 的齐次变换相乘，得到从肩部到手部的变换。公式裁剪图保留了原文的上标/下标格式；请以原图为准。

<a id="S039"></a>
**Source:** p.11 S039

**Original:** where subscripts $S$, $E$, $W$, and $H$ indicate shoulder, elbow, wrist, and hand, respectively. The translation part of every homogeneous transformation is known a priori (i.e., length of the arm and forearm, and the distance between the wrist and palm), whereas it is possible to compute ${}^{i}R_{j}\in\mathbb{R}^{3\times3}$ (rotation part of the homogeneous transformation ${}^{i}T_{j}$) by applying a Madgwick filter [23] on the data coming from the IMU placed on the arm and on the hand. The result of (7) is properly scaled to match with the length of the robot's arms and then used as a Cartesian reference for the IK algorithm. This setup allows for controlling the stiffness of the robot arms using the electromyographic data given by the Myo armbands placed on the pilot's upper arm, thus implementing teleimpedance control [4]. Hand closure is controlled by a linear combination of electromyographic signals from the Myo armbands placed on the pilot's forearms [7]. In this configuration, a Wii Balance Board [36] is used to control the robot's mobile base by sending velocity references. More specifically, an operator can use his or her own CoM to move the robot forward and back and turn left and right. This configuration is preferable when haptic feedback devices must be used, mainly because it leaves free the operator's hands. In some circumstances, a simplified version of the capture system can be used simply by relying on the sensors provided by the VR system adopted (e.g., Oculus Rift).

**中文:** 其中，下标 $S$、$E$、$W$ 和 $H$ 分别表示肩部、肘部、腕部和手部。每个齐次变换的平移部分是先验已知的（即手臂和前臂的长度，以及腕部与手掌之间的距离）；另一方面，可以对安装在手臂和手部的 IMU 所提供的数据应用 Madgwick 滤波器 [23]，从而计算 ${}^{i}R_{j}\in\mathbb{R}^{3\times3}$，即齐次变换 ${}^{i}T_{j}$ 的旋转部分。式 (7) 的结果经过适当缩放，以匹配机器人手臂长度，然后作为 IK 算法的笛卡尔参考。通过这种设置，可以利用安装在操作员上臂上的 Myo 臂带提供的肌电数据控制机器人手臂的刚度，从而实现远程阻抗控制 [4]。手部闭合由安装在操作员前臂上的 Myo 臂带的肌电信号线性组合控制 [7]。在这一配置中，Wii Balance Board [36] 通过发送速度参考值控制机器人的移动底座。更具体地说，操作员可以利用自己的 CoM 使机器人前进、后退并左右转弯。当必须使用触觉反馈设备时，这种配置尤其合适，因为它可以解放操作员的双手。在某些情况下，也可以使用简化的捕捉系统，只依赖所采用 VR 系统（例如 Oculus Rift）提供的传感器。

### Pilot Interface / 操作员接口

<a id="S040"></a>
**Source:** p.11 S040

**Original:** ALTER-EGO has a modular pilot interface that can be shaped according to different purposes and operation modalities. The key elements are input, visual, and haptic feedback interfaces. All of these elements can be selected and switched during a session. A description of each subsystem of the pilot interface is reported in the following sections.

**中文:** ALTER-EGO 具有模块化操作员接口，可以根据不同目的和操作模式进行配置。其关键元素是输入接口、视觉接口和触觉反馈接口。所有这些元素都可以在一次操作过程中选择和切换。下面各节将介绍操作员接口的每个子系统。

### Computational and Communication Console / 计算与通信控制台

<a id="S041"></a>
**Source:** p.12 S041

**Original:** ALTER-EGO's pilot station comprises one laptop used to manage, monitor, and command the robot together with the different interfaces. The same laptop is operated to handle the vision workload to manage 3D and 2D visualization, the VR framework, and vision algorithms. The pilot console is also equipped with a dedicated wireless router.

**中文:** ALTER-EGO 的操作员站由一台笔记本电脑组成，用于结合不同接口管理、监控和指挥机器人。同一台笔记本还承担视觉计算负载，用于管理三维和二维可视化、VR 框架以及视觉算法。操作员控制台还配有专用无线路由器。

### Visual Interfaces / 视觉接口

<a id="S042"></a>
**Source:** p.12 S042

**Original:** ALTER-EGO has two main visual interfaces: a standard screen visualization and immersive, first-person VR visualization. With the first option, it is possible to visualize all of the robot's parameters on a screen together with the visual streaming coming from RGB cameras. Likewise, using the support of ROS 3D visualizers (see the “ALTER-EGO” section), it is possible to produce a 3D reconstruction of the environment together with the 3D pose reconstruction of the robot. As a second option, ALTER-EGO also integrates the use of a VR headset, such as those used for Oculus Rift. In this configuration, an immersive visual representation of the world is possible.

**中文:** ALTER-EGO 有两种主要视觉接口：标准屏幕可视化，以及沉浸式第一人称 VR 可视化。使用第一种方式时，可以在屏幕上显示机器人的全部参数，并同时显示来自 RGB 相机的视觉流。同样，借助 ROS 三维可视化器（见“ALTER-EGO”部分），可以生成环境的三维重建以及机器人的三维姿态重建。第二种方式是集成 VR 头戴设备，例如 Oculus Rift 所使用的设备；在这一配置中，可以对世界进行沉浸式视觉呈现。

### Input Interfaces / 输入接口

<a id="S043"></a>
**Source:** p.12 S043

**Original:** Several input devices can be used to acquire or compute references for the robot, for both the locomotion and manipulation subsystems. Common joystick/joypad, keyboards, and mouses move the robot's mobile base and arms and buttons activate hands or start predefined functions. Currently, a balance board (WII) is employed to control the forward/backward and turning movements of the mobile base. Wearable devices such as the Myo armband (a nine-axis IMU, plus eight-channel surface electromyography sensors) are used to control activation of the robot's hands, manage the impedance of the actuation units, and perform motion capture of the pilot's movements in teleoperation mode (see the “Operating Modes” section). If a VR headset is present, its motion-capture system can be used to control the robot's movements.

**中文:** 对于移动和操作子系统，可以使用多种输入设备获取或计算机器人的参考值。普通操纵杆/游戏手柄、键盘和鼠标可以移动机器人的移动底座和手臂，按钮可以激活手部或启动预定义功能。目前，系统使用平衡板（WII）控制移动底座的前进、后退和转向。Myo 臂带等可穿戴设备（一个九轴 IMU 加八通道表面肌电传感器）用于控制机器人手部的激活、管理驱动单元的阻抗，并在远程操作模式下捕捉操作员运动（见“Operating Modes”部分）。如果配有 VR 头戴设备，也可以使用其运动捕捉系统控制机器人的运动。

### Haptic Feedback Interfaces / 触觉反馈接口

<a id="S044"></a>
**Source:** p.12 S044

**Original:** The ALTER-EGO pilot station was conceived to allow the pilot to use different haptic feedback devices for delivering different haptic stimuli, which can be conveyed on the hands of the pilot or on other parts of his or her body (e.g., the arms). To avoid typical issues related to instability as a result of the adoption of closed-loop controls, ALTER-EGO uses noncollocated feedback systems. Moreover, in most cases, a modality-matching approach is followed [11]. Examples of feedback stimuli developed under the same NMMI framework that can be used in the platform are hand grasp force [24], impacts and surface roughness [18], and hand proprioception [25].

**中文:** ALTER-EGO 操作员站的设计允许操作员使用不同的触觉反馈设备，传递不同的触觉刺激；刺激可以施加在操作员手部，也可以施加在身体其他部位（例如手臂）。为避免采用闭环控制而产生的典型不稳定问题，ALTER-EGO 使用非共位反馈系统。此外，大多数情况下遵循模态匹配方法 [11]。在同一 NMMI 框架下开发、并可用于该平台的反馈刺激例子包括手部抓握力 [24]、冲击和表面粗糙度 [18]，以及手部本体感觉 [25]。

<a id="F007"></a>
### Fig. 7. 开门、抓取与儿童物理交互

**Placed near:** p.11 S037
**Source:** p.11 C008

![Fig. 7](assets/figures/fig7.png)

<a id="C008"></a>
**Original caption:** Figure 7. (a) ALTER-EGO opens a door and grasps an object. (b) ALTER-EGO physically interacts with children. (Source: MakerFair; used with permission.)

**中文图注:** 图 7。(a) ALTER-EGO 打开一扇门并抓取一个物体；(b) ALTER-EGO 与儿童进行物理交互。（来源：MakerFair；经许可使用。）

**Reading note:** Panel (a) demonstrates immersive teleoperation for a door-and-grasp task; panel (b) illustrates social and physical interaction in a public exposition. / (a) 展示沉浸式远程操作下的开门与抓取任务；(b) 展示公开展览场景中的社会与物理交互。

## Experiments and Discussion / 实验与讨论

<a id="S045"></a>
**Source:** p.12 S045

**Original:** This section reports on experimental examples to demonstrate the effectiveness of the system's basic capabilities and describe application examples where ALTER-EGO is used in physically simulated and realistic contexts. The pictures and photo sequences referenced in this section are extracted from the video footage linked to this article.

**中文:** 本节报告若干实验示例，以展示系统基本能力的有效性，并描述 ALTER-EGO 在物理仿真和真实场景中的应用实例。本节引用的图片和照片序列取自与本文关联的视频资料。

<a id="S046"></a>
**Source:** p.12-p.13 S046

**Original:** Figure 7 shows the robot executing different tasks in different contexts. In Figure 7(a), ALTER-EGO is used in immersive teleoperation modality to open a door, grasp an object, and provide it to a third user. The movements of the robot and the human operator are visible. Figure 7(b) shows ALTER-EGO interacting with children during an exposition (MakerFair in Rome, Italy).

**中文:** 图 7 展示了机器人在不同情境下执行不同任务。图 7(a) 中，ALTER-EGO 使用沉浸式远程操作模式打开一扇门、抓取一个物体，并将其交给第三方；图中可以看到机器人和人类操作员的运动。图 7(b) 展示了 ALTER-EGO 在一次展览活动中与儿童交互的场景，该活动在意大利罗马的 MakerFair 举行。

<a id="S047"></a>
**Source:** p.12-p.13 S047

**Original:** Figure 8 depicts ALTER-EGO operating in a domestic use-case scenario. The actions shown are mostly executed in the immersive teleoperation operating mode and envision a hypothetical user jumping inside the robot at his or her work location and teleporting him or herself home to perform domestic tasks. In Figure 8(a) and (b), the pilot uses the robot to prepare food for a pet and to retrieve a package from a mail carrier, pay for the item, and return to the house. In Figure 8(c), the pilot remotely simulates ALTER-EGO assisting a relative.

**中文:** 图 8 描绘了 ALTER-EGO 在家庭使用场景中的运行。图中动作大多在沉浸式远程操作模式下执行，设想一名用户在工作地点“进入”机器人，再将自己远程传送回家中完成家务。在图 8(a)、(b) 中，操作员使用机器人为宠物准备食物，从邮递员处取回包裹、支付物品费用并返回家中。在图 8(c) 中，操作员远程模拟 ALTER-EGO 协助一名亲属。

<a id="F008"></a>
### Fig. 8. 家庭场景、亲属协助与户外地形

**Placed near:** p.12 S047
**Source:** p.12 C009

![Fig. 8](assets/figures/fig8.png)

<a id="C009"></a>
**Original caption:** Figure 8. (a) and (b) The robot is teleoperated to prepare food for pets and retrieve a package from a mail carrier. (c) ALTER-EGO assists a pilot's relative. (d) The robot is operated in an outdoor terrain with small rocks, grass roots, and a slight descent.

**中文图注:** 图 8。(a)、(b) 机器人被远程操作来为宠物准备食物，并从邮递员处取回包裹；(c) ALTER-EGO 协助操作员的亲属；(d) 机器人在具有小石块、草根和轻微下坡的户外地形中运行。

**Reading note:** The four panels connect the proposed teleoperation framework to domestic assistance, caregiving, and uneven outdoor terrain. / 四个分图把所提远程操作框架与家庭协助、照护和不平整户外地形联系起来。

<a id="S048"></a>
**Source:** p.13 S048

**Original:** In this scenario, ALTER-EGO provided a thermometer and pills to the relative, checked the relative's temperature, offered a blanket, checked the cardiac frequency, and presented food. The experimental activity was performed at two different locations positioned at a distance of 5 km (the pilot station was placed in the engineering building on the campus of the University of Pisa), and the telecommunication framework used an Internet connection with a bandwidth of 48 and 80 Mb/s in download and 48.3 and 18 Mb/s in upload for the pilot station and domestic environment, respectively. The ping was 17 ms. Although not exhaustive, such an experience demonstrates the potential effectiveness of the approach. Finally, Figure 8(d) shows ALTER-EGO moving on an outdoor, uneven terrain characterized by the presence of small rocks, grass roots, and a slight descent.

**中文:** 在这一场景中，ALTER-EGO 为亲属提供体温计和药片，检查亲属体温，递上毯子，检查心率，并递送食物。实验活动在相距 5 km 的两个地点进行（操作员站位于比萨大学校园内的工程楼），通信框架使用互联网连接；对于操作员站和家庭环境，下载带宽分别为 48 和 80 Mb/s，上传带宽分别为 48.3 和 18 Mb/s。ping 时间为 17 ms。虽然这一实验并不全面，但它展示了该方法的潜在有效性。最后，图 8(d) 展示了 ALTER-EGO 在户外不平整地形上移动，该地形包含小石块、草根和轻微下坡。

<a id="S049"></a>
**Source:** p.13 S049

**Original:** We would like to point out and discuss a few of the drawbacks experienced while using the proposed platform. The advantages of using an agile, two-wheeled mobile base can be counterbalanced by the instability of the platform. Indeed, this can have critical, even catastrophic effects, e.g., in the case of impacts with the environment during a manipulation task. The CoM variation (e.g., movements of the arms or variation of payload) is used to update the feedforward action (preferred pitch angle) to stabilize the robot. With the LQR control approach, the perturbation on the end effector's desired pose (due to the stabilizing controller) can be corrected and compensated for only by the pilot, who must close the external control loop through the vision feedback provided by the VR headset. We acknowledge that this approach is a rather simplistic solution to the problem, and better solutions could certainly be devised.

**中文:** 我们还希望指出并讨论使用该平台时遇到的一些缺点。灵活的双轮移动底座带来的优势，可能被平台本身的不稳定性抵消。事实上，在操作任务中与环境发生碰撞时，这种不稳定可能产生严重、甚至灾难性的后果。系统利用 CoM 变化（例如手臂运动或负载变化）更新前馈动作（期望俯仰角），以稳定机器人。在 LQR 控制方案下，末端执行器期望位姿受到稳定控制器扰动后，只能由操作员进行校正和补偿；操作员必须通过 VR 头戴设备提供的视觉反馈闭合外部控制回路。作者承认，这是一种相当简单的解决方案，当然还可以设计更好的方法。

<a id="S050"></a>
**Source:** p.13 S050

**Original:** Nevertheless, in the videos, the pilot accomplishes the tasks notwithstanding the disturbances. In our experience, such phenomena are well addressed when the robot is teleoperated in an immersive mode because the pilot-robot interaction is intuitive and the pilot has an idea of what is happening in the scene. Although we have only episodic data, one could venture to say that human pilots exploit their own instinctive ability to compensate for stabilization and manipulation interactions. For this reason, we also introduced the whole-body balancing control method described in the “Control” section. Using this controller, balancing performance improves; however, a more in-depth investigation is needed to better evaluate its performance during manipulation tasks. Note that other possible approaches to the autonomous decoupling of manipulation and stabilization include the introduction of active counterbalance mass, as seen, e.g., in recent Boston Dynamics footage [37]. Such solutions do not fit well with the size and purpose of the ALTER-EGO platform, where the introduction of heavy counterweights could bring about safety concerns.

**中文:** 尽管如此，在视频中，操作员仍然能够在存在扰动的情况下完成任务。根据作者的经验，当机器人处于沉浸式远程操作模式时，这些现象能够得到较好处理，因为操作员与机器人的交互是直观的，操作员也能理解场景中发生的事情。虽然作者只有偶发性数据，但可以推测，人类操作员会利用自身的本能能力，补偿稳定和平衡与操作交互之间的耦合。基于这一原因，作者还引入了“Control”部分所述的全身平衡控制方法。使用该控制器后，平衡性能得到改善；不过，还需要更深入的研究来更好地评价它在操作任务中的表现。需要注意的是，另一种把操作与稳定解耦的自主方案，是引入主动配重，例如近期 Boston Dynamics 视频中所展示的方案 [37]。但这种方案并不适合 ALTER-EGO 的尺寸和用途，因为加入沉重配重可能带来安全问题。

<a id="S051"></a>
**Source:** p.13 S051

**Original:** Some consideration can also be given with regard to the design of the neck/head subsystem. The current solution does not ensure the following of the pilot's head trajectory perfectly (see the “Operating Modes” section). At the moment, however, this does not prevent the pilot from operating the robot in a satisfactory way. We believe that a more anthropomorphic design of the kinematic structure (i.e., at least 3 DoF configured as a spherical joint [15]) could enable a better performance in terms of both vision capabilities and user experience (by reducing the typical motion sickness that can occur after intense use of a VR system).

**中文:** 颈部/头部子系统的设计也值得考虑。目前的方案不能完美跟随操作员的头部轨迹（见“Operating Modes”部分）。不过在现阶段，这并不妨碍操作员以令人满意的方式操纵机器人。作者认为，如果运动学结构更加拟人化（即至少配置 3 个 DoF，形成球面关节 [15]），则可能在视觉能力和用户体验方面带来更好的性能，并减少长时间使用 VR 系统后可能出现的典型晕动症。

## Conclusions / 结论

<a id="S052"></a>
**Source:** p.13 S052

**Original:** In this article, we presented ALTER-EGO, a dual-arm mobile platform developed using soft robotic technologies for the actuation and manipulation layers. Features resulting from this kind of technology, such as flexibility, adaptivity, and robustness, allow ALTER-EGO to interact with the environment and objects and provide improved safety when the robot is in proximity to humans. An overview of ALTER-EGO's mechatronic design, pilot interface, and core and high-level functions was presented. Most of the hardware and software technologies adopted, developed, and explicitly designed for ALTER-EGO are distributed under an open source framework and available on the NMMI website. The platform validation was performed both inside and outside the lab and involved several tasks. In particular, the house-simulation scenario demonstrated the potential of ALTER-EGO in a real-life situation. Future work will be devoted to investigating the role of haptic feedback interfaces as well as studying the platform's extensive use in different fields.

**中文:** 本文介绍了 ALTER-EGO：一个在驱动层和操作层采用软体机器人技术开发的双臂移动平台。这类技术带来的柔性、适应性和鲁棒性，使 ALTER-EGO 能够与环境和物体交互，并在机器人接近人时提供更好的安全性。本文概述了 ALTER-EGO 的机电设计、操作员接口，以及核心功能和高层功能。为 ALTER-EGO 采用、开发并专门设计的大部分硬件和软件技术，都在开源框架下发布，并可从 NMMI 网站获得。该平台在实验室内外进行了验证，涉及多项任务。尤其是家庭仿真场景展示了 ALTER-EGO 在真实生活情境中的潜力。未来工作将研究触觉反馈接口的作用，并探索该平台在不同领域中的广泛应用。

## Acknowledgments / 致谢

<a id="S053"></a>
**Source:** p.13 S053

**Original:** We thank Cristiano Petrocelli, Gaspare Santaera, Mattia Poggiani, Michele Maimeri, Manuel Barbarossa, Vinicio Tincani, and Ashwin Vasudevan for their work on the design and implementation of the ALTER-EGO robot. We also thank Grazia Zambella, Alessandro Palleschi, and Luca Bonamini for their help with the experimental activities.

**中文:** 感谢 Cristiano Petrocelli、Gaspare Santaera、Mattia Poggiani、Michele Maimeri、Manuel Barbarossa、Vinicio Tincani 和 Ashwin Vasudevan 在 ALTER-EGO 机器人设计与实现方面所做的工作。也感谢 Grazia Zambella、Alessandro Palleschi 和 Luca Bonamini 对实验活动的帮助。

## References / 参考文献

> Bibliographic fields, numbering, venues, page ranges, DOI and URLs are retained from the source. The Chinese line gives a meaning-oriented title/description and is not a replacement for the English citation. / 以下保留原文的文献字段、编号、期刊/会议、页码、DOI 和 URL；中文行仅提供标题或内容的释义，不替代英文引文。

<a id="R001"></a>
**[1] Original:** D. Gouaillier et al., “Mechatronic design of NAO humanoid,” in *Proc. IEEE Int. Conf. Robotics and Automation (ICRA)*, 2010, pp. 3304-3309.

**中文:** “NAO 类人机器人的机电设计”，IEEE 国际机器人与自动化会议论文集，2010，3304-3309 页。

<a id="R002"></a>
**[2] Original:** E. Guizzo, “A robot in the family,” *IEEE Spectr.*, vol. 52, no. 1, pp. 28-58, 2014. doi: 10.1109/MSPEC.2015.6995630.

**中文:** “家庭中的机器人”，*IEEE Spectrum*，第 52 卷第 1 期，2014，28-58 页。

<a id="R003"></a>
**[3] Original:** A. Parmiggiani et al., “The design and validation of the R1 personal humanoid,” in *Proc. IEEE/RSJ Int. Conf. Intelligent Robots and Systems (IROS)*, 2017, pp. 674-680.

**中文:** “R1 个人类人机器人的设计与验证”，IEEE/RSJ 智能机器人与系统国际会议论文集，2017，674-680 页。

<a id="R004"></a>
**[4] Original:** F. Negrello et al., “Humanoids at work: The WALK-MAN robot in a postearthquake scenario,” *IEEE Robot. Autom. Mag.*, vol. 25, no. 3, pp. 8-22, 2018.

**中文:** “工作中的类人机器人：震后场景中的 WALK-MAN 机器人”，*IEEE Robotics & Automation Magazine*，第 25 卷第 3 期，8-22 页，2018。

<a id="R005"></a>
**[5] Original:** G. Nelson et al., “PETMAN: A humanoid robot for testing chemical protective clothing,” *J. Robot. Soc. Jpn.*, vol. 30, no. 4, pp. 372-377, 2012.

**中文:** “PETMAN：用于测试化学防护服的类人机器人”，*Journal of the Robotics Society of Japan*，第 30 卷第 4 期，372-377 页，2012。

<a id="R006"></a>
**[6] Original:** J. Englsberger et al., “Overview of the torque-controlled humanoid robot TORO,” in *Proc. IEEE-RAS Int. Conf. Humanoid Robots*, 2014, pp. 916-923.

**中文:** “力矩控制类人机器人 TORO 概览”，IEEE-RAS 类人机器人国际会议论文集，2014，916-923 页。

<a id="R007"></a>
**[7] Original:** C. Della Santina et al., “The quest for natural machine motion: An open platform to fast-prototyping articulated soft robots,” *IEEE Robot. Autom. Mag.*, vol. 24, no. 1, pp. 48-56, 2017.

**中文:** “探索自然机器运动：用于快速原型化关节式软体机器人的开放平台”，*IEEE Robotics & Automation Magazine*，第 24 卷第 1 期，48-56 页，2017。

<a id="R008"></a>
**[8] Original:** M. Garabini, C. D. Santina, M. Bianchi, M. Catalano, G. Grioli, and A. Bicchi, “Soft robots that mimic the neuromusculoskeletal system,” in *Converging Clinical and Engineering Research on Neurorehabilitation II*. J. Ibáñez, J. González-Vargas, J. Azorín, M. Akay, and J. Pons, Eds. New York: Springer-Verlag, 2017, pp. 259-263.

**中文:** “模拟神经肌肉骨骼系统的软体机器人”，载于 *Converging Clinical and Engineering Research on Neurorehabilitation II*，Springer-Verlag，纽约，2017，259-263 页。

<a id="R009"></a>
**[9] Original:** A. Ajoudani, N. Tsagarakis, and A. Bicchi, “Tele-impedance: Teleoperation with impedance regulation using a body-machine interface,” *Int. J. Robot. Res.*, vol. 31, no. 13, pp. 1642-1656, 2012.

**中文:** “远程阻抗：使用身体-机器接口进行阻抗调节的远程操作”，*International Journal of Robotics Research*，第 31 卷第 13 期，1642-1656 页，2012。

<a id="R010"></a>
**[10] Original:** B. Siciliano, L. Sciavicco, L. Villani, and G. Oriolo, *Robotics: Modelling, Planning and Control*. London: Springer-Verlag, 2010.

**中文:** *Robotics: Modelling, Planning and Control*（机器人学：建模、规划与控制），Springer-Verlag，伦敦，2010。

<a id="R011"></a>
**[11] Original:** H. Culbertson, S. B. Schorr, and A. M. Okamura, “Haptics: The present and future of artificial touch sensation,” *Annu. Rev. Control, Robot., Auton. Syst.*, vol. 1, no. 1, pp. 385-409, 2018.

**中文:** “触觉：人工触觉感知的现在与未来”，*Annual Review of Control, Robotics, and Autonomous Systems*，第 1 卷第 1 期，385-409 页，2018。

<a id="R012"></a>
**[12] Original:** M. Stilman, J. Olson, and W. Gloss, “Golem Krang: Dynamically stable humanoid robot for mobile manipulation,” in *Proc. IEEE Int. Conf. Robotics and Automation (ICRA)*, 2010, pp. 3304-3309.

**中文:** “Golem Krang：用于移动操作的动态稳定类人机器人”，IEEE 国际机器人与自动化会议论文集，2010，3304-3309 页。

<a id="R013"></a>
**[13] Original:** S. R. Kuindersma, E. Hannigan, D. Ruiken, and R. A. Grupen, “Dexterous mobility with the ubot-5 mobile manipulator,” in *Proc. IEEE Int. Conf. Advanced Robotics*, 2009, pp. 1-7.

**中文:** “使用 ubot-5 移动操作机器人实现灵巧移动”，IEEE 高级机器人国际会议论文集，2009，1-7 页。

<a id="R014"></a>
**[14] Original:** G. Zambella et al., “Dynamic whole-body control of unstable wheeled humanoid robots,” *IEEE Robot. Autom. Lett.*, vol. 4, no. 4, pp. 3489-3496, 2019.

**中文:** “不稳定轮式类人机器人的动态全身控制”，*IEEE Robotics and Automation Letters*，第 4 卷第 4 期，3489-3496 页，2019。

<a id="R015"></a>
**[15] Original:** S. Mghames, M. G. Catalano, A. Bicchi, and G. Grioli, “A spherical active joint for humanoids and humans,” *IEEE Robot. Autom. Lett.*, vol. 4, no. 2, pp. 838-845, 2019.

**中文:** “用于类人机器人和人类的球面主动关节”，*IEEE Robotics and Automation Letters*，第 4 卷第 2 期，838-845 页，2019。

<a id="R016"></a>
**[16] Original:** W. An and Y. Li, “Simulation and control of a two-wheeled self-balancing robot,” in *Proc. IEEE Int. Conf. Robotics and Biomimetics (ROBIO)*, 2013, pp. 456-461.

**中文:** “双轮自平衡机器人的仿真与控制”，IEEE 机器人与仿生学国际会议论文集，2013，456-461 页。

<a id="R017"></a>
**[17] Original:** C. Xu, M. Li, and F. Pan, “The system design and LQR control of a two-wheels self-balancing mobile robot,” in *Proc. Int. Conf. Electrical and Control Engineering*, 2011, pp. 2786-2789.

**中文:** “双轮自平衡移动机器人的系统设计与 LQR 控制”，电气与控制工程国际会议论文集，2011，2786-2789 页。

<a id="R018"></a>
**[18] Original:** S. Fani, K. D. Blasio, M. Bianchi, M. G. Catalano, G. Grioli, and A. Bicchi, “Relaying the high frequency contents of tactile feedback to robotic prosthesis users: Design, filtering, implementation and validation,” *IEEE Robot. Autom. Lett.*, vol. 4, no. 2, pp. 926-933, 2019.

**中文:** “向机器人假肢使用者传递触觉反馈中的高频内容：设计、滤波、实现与验证”，*IEEE Robotics and Automation Letters*，第 4 卷第 2 期，926-933 页，2019。

<a id="R019"></a>
**[19] Original:** M. V. Damme et al., “Estimating robot end-effector force from noisy actuator torque measurements,” in *Proc. IEEE Int. Conf. Robotics and Automation (ICRA)*, 2011, pp. 1108-1113.

**中文:** “从含噪执行器力矩测量估计机器人末端执行器力”，IEEE 国际机器人与自动化会议论文集，2011，1108-1113 页。

<a id="R020"></a>
**[20] Original:** M. Labbe and F. Michaud, “Online global loop closure detection for large-scale multi-session graph-based SLAM,” in *Proc. IEEE/RSJ Int. Conf. Intelligent Robots and Systems*, 2014, pp. 2661-2666.

**中文:** “面向大规模多会话图 SLAM 的在线全局闭环检测”，IEEE/RSJ 智能机器人与系统国际会议论文集，2014，2661-2666 页。

<a id="R021"></a>
**[21] Original:** M. S. Arulampalam, S. Maskell, N. Gordon, and T. Clapp, “A tutorial on particle filters for online nonlinear/non-Gaussian Bayesian tracking,” *IEEE Trans. Signal Process.*, vol. 50, no. 2, pp. 174-188, 2002.

**中文:** “在线非线性/非高斯贝叶斯跟踪的粒子滤波器教程”，*IEEE Transactions on Signal Processing*，第 50 卷第 2 期，174-188 页，2002。

<a id="R022"></a>
**[22] Original:** R. Coulter, “Implementation of the pure pursuit path tracking algorithm,” Carnegie Mellon Univ., Pittsburgh, PA, Rep. CMU-RI-TR-92-01, 1992.

**中文:** “纯跟踪路径跟踪算法的实现”，卡内基梅隆大学报告 CMU-RI-TR-92-01，匹兹堡，1992。

<a id="R023"></a>
**[23] Original:** S. O. Madgwick, A. J. Harrison, and R. Vaidyanathan, “Estimation of IMU and MARG orientation using a gradient descent algorithm,” in *Proc. IEEE Int. Conf. Rehabilitation Robotics (ICORR)*, 2011, pp. 1-7.

**中文:** “使用梯度下降算法估计 IMU 和 MARG 姿态”，IEEE 康复机器人国际会议论文集，2011，1-7 页。

<a id="R024"></a>
**[24] Original:** S. Fani et al., “Simplifying telerobotics: Wearability and teleimpedance improves human-robot interactions in teleoperation,” *IEEE Robot. Autom. Mag.*, vol. 25, no. 1, pp. 77-88, 2018.

**中文:** “简化远程机器人：可穿戴性和远程阻抗改善远程操作中的人机交互”，*IEEE Robotics & Automation Magazine*，第 25 卷第 1 期，77-88 页，2018。

<a id="R025"></a>
**[25] Original:** N. Colella, M. Bianchi, G. Grioli, A. Bicchi, and M. G. Catalano, “A novel skin-stretch haptic device for intuitive control of robotic prostheses and avatars,” *IEEE Robot. Autom. Lett.*, vol. 4, no. 2, 2019.

**中文:** “用于直观控制机器人假肢和化身的新型皮肤牵伸触觉设备”，*IEEE Robotics and Automation Letters*，第 4 卷第 2 期，2019。

<a id="R026"></a>
**[26] Original:** iRobot, “If it is not iRobot, it is not a Roomba.” Accessed on: Nov. 5, 2019. [Online]. Available: https://www.irobot.it/roomba

**中文:** iRobot 网站，“如果不是 iRobot，就不是 Roomba”。访问日期：2019 年 11 月 5 日。

<a id="R027"></a>
**[27] Original:** Fernarbeiter. Accessed on: Nov. 5, 2019. [Online]. Available: http://www.fernarbeiter.de/en/

**中文:** Fernarbeiter 网站。访问日期：2019 年 11 月 5 日。

<a id="R028"></a>
**[28] Original:** DARPA, “Our research.” Accessed on: Nov. 5, 2019. [Online]. Available: https://www.darpa.mil/program

**中文:** DARPA，“我们的研究”。访问日期：2019 年 11 月 5 日。

<a id="R029"></a>
**[29] Original:** XPRIZE, “Anywhere is possible.” Accessed on: Nov. 5, 2019. [Online]. Available: https://avatar.xprize.org/prizes/avatar

**中文:** XPRIZE，“任何地方皆有可能”。访问日期：2019 年 11 月 5 日。

<a id="R030"></a>
**[30] Original:** XPRIZE, “Guidelines.” Accessed on: Nov. 5, 2019. [Online]. Available: https://avatar.xprize.org/prizes/avatar/guidelines

**中文:** XPRIZE，“竞赛指南”。访问日期：2019 年 11 月 5 日。

<a id="R031"></a>
**[31] Original:** NMMI. Accessed on: Nov. 5, 2019. [Online]. Available: www.naturalmachinemotioninitiative.com

**中文:** NMMI 网站。访问日期：2019 年 11 月 5 日。

<a id="R032"></a>
**[32] Original:** GitHub, “NMMI/EGO.” Accessed on: Nov. 5, 2019. [Online]. Available: https://github.com/NMMI/EGO

**中文:** GitHub 项目 “NMMI/EGO”。访问日期：2019 年 11 月 5 日。

<a id="R033"></a>
**[33] Original:** Stereo Labs. Accessed on: Nov. 5, 2019. [Online]. Available: https://www.stereolabs.com/

**中文:** Stereo Labs 网站。访问日期：2019 年 11 月 5 日。

<a id="R034"></a>
**[34] Original:** GitHub, “Facebook research/detectron.” Accessed on: Nov. 5, 2019. [Online]. Available: https://github.com/facebookresearch/detectron

**中文:** GitHub 项目 “Facebook research/detectron”。访问日期：2019 年 11 月 5 日。

<a id="R035"></a>
**[35] Original:** ROS.org, “Aruco.” Accessed on: Nov. 5, 2019. [Online]. Available: http://wiki.ros.org/aruco

**中文:** ROS.org 软件包 “Aruco”。访问日期：2019 年 11 月 5 日。

<a id="R036"></a>
**[36] Original:** Nintendo, “Wii.” Accessed on: Nov. 5, 2019. [Online]. Available: https://www.nintendo.it/Wii/Wii-94559.html

**中文:** Nintendo，“Wii”。访问日期：2019 年 11 月 5 日。

<a id="R037"></a>
**[37] Original:** Boston Dynamics, “Handle.” Accessed on: Nov. 5, 2019. [Online]. Available: www.bostondynamics.com/handle

**中文:** Boston Dynamics，“Handle”。访问日期：2019 年 11 月 5 日。

## Author information / 作者信息

<a id="A001"></a>
**Source:** p.14 A001

**Original:** Gianluca Lentini, Istituto Italiano di Tecnologia, Genoa, Italy, and Department of Information Engineering, Research Center Enrico Piaggio, University of Pisa, Italy. Email: gianluca.lentini@iit.it.

**中文:** Gianluca Lentini，意大利热那亚意大利理工学院；比萨大学 Enrico Piaggio 研究中心信息工程系，意大利。邮箱：gianluca.lentini@iit.it。

<a id="A002"></a>
**Source:** p.14 A002

**Original:** Alessandro Settimi, Department of Information Engineering, Research Center Enrico Piaggio, University of Pisa, Italy. Email: alessandro.settimi@for.unipi.it.

**中文:** Alessandro Settimi，比萨大学 Enrico Piaggio 研究中心信息工程系，意大利。邮箱：alessandro.settimi@for.unipi.it。

<a id="A003"></a>
**Source:** p.14 A003

**Original:** Danilo Caporale, Department of Information Engineering, Research Center Enrico Piaggio, University of Pisa, Italy. Email: d.caporale@centropiaggio.unipi.it.

**中文:** Danilo Caporale，比萨大学 Enrico Piaggio 研究中心信息工程系，意大利。邮箱：d.caporale@centropiaggio.unipi.it。

<a id="A004"></a>
**Source:** p.14 A004

**Original:** Manolo Garabini, Department of Information Engineering, Research Center Enrico Piaggio, University of Pisa, Italy. Email: manolo.garabini@gmail.com.

**中文:** Manolo Garabini，比萨大学 Enrico Piaggio 研究中心信息工程系，意大利。邮箱：manolo.garabini@gmail.com。

<a id="A005"></a>
**Source:** p.14 A005

**Original:** Giorgio Grioli, Istituto Italiano di Tecnologia, Genoa, Italy. Email: giorgio.grioli@iit.it.

**中文:** Giorgio Grioli，意大利热那亚意大利理工学院。邮箱：giorgio.grioli@iit.it。

<a id="A006"></a>
**Source:** p.14 A006

**Original:** Lucia Pallottino, Department of Information Engineering, Research Center Enrico Piaggio, University of Pisa, Italy. Email: lucia.pallottino@unipi.it.

**中文:** Lucia Pallottino，比萨大学 Enrico Piaggio 研究中心信息工程系，意大利。邮箱：lucia.pallottino@unipi.it。

<a id="A007"></a>
**Source:** p.14 A007

**Original:** Manuel G. Catalano, Istituto Italiano di Tecnologia, Genoa, Italy. Email: manuel.catalano@iit.it.

**中文:** Manuel G. Catalano，意大利热那亚意大利理工学院。邮箱：manuel.catalano@iit.it。

<a id="A008"></a>
**Source:** p.14 A008

**Original:** Antonio Bicchi, Istituto Italiano di Tecnologia, Genoa, and Department of Information Engineering, Research Center Enrico Piaggio, University of Pisa, Italy. Email: antonio.bicchi@iit.it.

**中文:** Antonio Bicchi，意大利热那亚意大利理工学院；比萨大学 Enrico Piaggio 研究中心信息工程系，意大利。邮箱：antonio.bicchi@iit.it。

## 阅读提示 / Critical reading notes

1. **系统定位：** 论文的主要贡献不是提出单一新算法，而是把 VSA、欠驱动拟人手、双轮自平衡底座、视觉/触觉接口和多种操作模式组合为一个可移动的物理交互平台。
2. **控制与机构的耦合：** 双轮底座提高了灵活性并减小占地，但带来主动平衡和能耗问题；质心变化会反过来影响头部和末端执行器的位姿，因此移动、平衡和操作不能完全独立处理。
3. **自主性边界：** 作者明确倾向共享自主性，而非完全自主或完全远程操作；这与任务同时包含导航、精细操作、力控制、语音/听觉和社会交互要求相一致。
4. **实验性证据：** 实验主要是能力演示和场景验证，作者也承认数据具有偶发性，尚不足以全面量化沉浸式远程操作、全身控制和触觉接口的长期性能。

## 提取与不确定性说明 / Translation Notes

- **Source format:** `pdf-text`。14 页均有可选文本层；未使用 OCR。
- **版面：** 原文为 IEEE Robotics & Automation Magazine 双栏版式。本文按自然阅读顺序重排正文，保留原页码和源块编号。
- **Table 1：** 原表在第 3 页横向旋转，并在第 4 页继续。两页分别裁剪为 `assets/tables/table1_p3.png` 与 `assets/tables/table1_p4.png`；表中勾选矩阵以原图为准，中文任务释义按可读文本逐行转写。
- **公式：** Eq. (1)-(6) 根据文本层和页面视觉核对重建，置信度为 medium；符号、上下标和点号应优先以 PDF 页面为准。Eq. (7) 的上标/下标在文本层中被打散，保留了原始公式裁剪 `assets/equations/E007.png`，Markdown 转写标记为 low-confidence transcription。
- **原文 glyph 不清：** “qb move”/“12-qb move units”在 PDF 文本层中出现了字形编码异常，本文不擅自推断其产品名或符号，按可读层保留并在此标记。
- **未编号插图：** 第 1 页的 ALTER-EGO 插图不是论文编号图，作为 `F000` 单独保留，避免与 Fig. 1 混淆。
- **数值与单位：** 原文中的 kg、mm、m/s、h、V、mAh、Mb/s、ms 等单位和数值均按原文保留；个别原文写作 “3 Kg”，中文正文统一按数值含义写作 3 kg。
- **版权范围：** 本 reader 用于用户提供的本地 PDF；聊天回复仅指向本地生成文件，不在聊天中复现全文。
