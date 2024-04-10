## Paper Presentation

- Title：APTGen: An Approach towards Generating Practical Dataset Labelled with Targeted Attack Sequences

- From：CSET 2020

## Attendees

- Jiahui Wang

## Insights


`Q1`: *What problem does the paper attempt to solve?*

`A1`: This article attempts to solve the problem of limited log datasets with groundtruth annotations. Therefore, an attack generation technology is proposed. By simulating attacks in an experimental environment, while collecting logs, it can be combined with accurate attack groundtruth annotations.

`Q2` *Is this a new problem?*

`A2`: Building datasets by generating attacks is a new issue, The closest works to this paper are the researches of automatically generating attack trees, automation of penetration and red team [[15](#15--andy-applebaum-doug-miller-blake-strom-chris-korban-and-ross-wolf-intelligent-automated-red-team-emulation-in-proceedings-of-the-32nd-annual-conference-on-computer-security-applications-acsac-16-pages-363–373-acm-2016),[22](#22--g-falco-a-viswanathan-c-caldera-and-h-shrobe-a-master-attack-methodology-for-an-ai-based-automated-attack-planner-for-smart-cities-ieee-access-648360–48373-2018),[27](#27--joerg-hoffmann-simulated-penetration-testing-from-dijkstra-to-turing-test-in-twenty-fifth-international-conference-on-automated-planning-and-scheduling-2015),[32](#32--suneel-randhawa-benjamin-turnbull-joseph-yuen-and-jonathan-dean-mission-centric-automated-cyber-red-teaming-in-proceedings-of-the-13th-international-conference-on-availability-reliability-and-security-ares-2018-pages-1–11-association-for-computing-machinery-august-2018),[36](#36--joseph-yuen-automated-cyber-red-teaming-technical-report-dsto-tn-1420-defence-science-and-technology-organisation-edinburgh-australia-cyber-and-electronic-warfare-div-2015)]. Falco et al. proposed a method of automatically generating attack trees for smart cities [[22](#22--g-falco-a-viswanathan-c-caldera-and-h-shrobe-a-master-attack-methodology-for-an-ai-based-automated-attack-planner-for-smart-cities-ieee-access-648360–48373-2018)]. Automation techniques of red team were proposed by [[15](#15--andy-applebaum-doug-miller-blake-strom-chris-korban-and-ross-wolf-intelligent-automated-red-team-emulation-in-proceedings-of-the-32nd-annual-conference-on-computer-security-applications-acsac-16-pages-363–373-acm-2016),[32](#32--suneel-randhawa-benjamin-turnbull-joseph-yuen-and-jonathan-dean-mission-centric-automated-cyber-red-teaming-in-proceedings-of-the-13th-international-conference-on-availability-reliability-and-security-ares-2018-pages-1–11-association-for-computing-machinery-august-2018)]. 


`Q5` *What is key to the solution proposed in the paper?*

`A5`: The key to the solution is to construct a state machine with restrictive conditions. Through the continuous construction of the state machine, multiple attack sequences can be obtained from one attack report, and the goals behind these attack sequences are the same. This strategy and construction The objectives of the data set are fully consistent.


## References

#### [ 15 ] Andy Applebaum, Doug Miller, Blake Strom, Chris Korban, and Ross Wolf. Intelligent, Automated Red Team Emulation. In Proceedings of the 32Nd Annual Conference on Computer Security Applications, ACSAC ’16, pages 363–373. ACM, 2016.

#### [ 22 ] G. Falco, A. Viswanathan, C. Caldera, and H. Shrobe. A Master Attack Methodology for an AI-Based Automated Attack Planner for Smart Cities. IEEE Access, 6:48360–48373, 2018.

#### [ 27 ] Joerg Hoffmann. Simulated Penetration Testing: From "Dijkstra" to "Turing Test++". In Twenty-Fifth International Conference on Automated Planning and Scheduling, 2015.

#### [ 32 ] Suneel Randhawa, Benjamin Turnbull, Joseph Yuen, and Jonathan Dean. Mission-Centric Automated Cyber Red Teaming. In Proceedings of the 13th International Conference on Availability, Reliability and Security, ARES 2018, pages 1–11. Association for Computing Machinery, August 2018.

#### [ 36 ] Joseph Yuen. Automated Cyber Red Teaming. Technical Report DSTO-TN-1420, DEFENCE SCIENCE AND TECHNOLOGY ORGANISATION EDINBURGH (AUSTRALIA) CYBER AND ELECTRONIC WARFARE DIV, 2015.