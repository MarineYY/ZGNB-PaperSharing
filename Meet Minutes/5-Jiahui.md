## Paper Presentation

- Title：Looking Beyond IoCs: Automatically Extracting Attack Patterns from External CTI

- From：RAID 2023

## Attendees

- Jiahui Wang

## Insights


`Q1`: *What problem does the paper attempt to solve?*

`A1`: This paper attempts to extract more robust attack information called attack patterns (TTPs, etc.) from CTI reports. The knowledge graph constructed from the obtained information can empower downstream applications, such as link queries.

`Q2` *Is this a new problem?*

`A2`: Extracting attack patterns from CTI is not a new issue, as *[TTPDrill](#1--ghaith-husari-ehab-al-shaer-mohiuddin-ahmed-bill-chu-and-xi-niu-2017-ttpdrill-automatic-and-accurate-extraction-of-threat-actions-from-unstructured-text-of-cti-sources-in-proceedings-of-the-33rd-annual-computer-security-applications-conference-103–115)* and *[AttacKG](#2--zhenyuan-li-jun-zeng-yan-chen-and-zhenkai-liang-2022-attackg-constructing-technique-knowledge-graph-from-cyber-threat-intelligence-reports-in-computer-security---esorics-2022---27th-european-symposium-on-research-in-computer-security-copenhagen-denmark-september-26-30-2022-proceedings-part-i-lecture-notes-in-computer-science-vol-13554-springer-589–609-httpsdoiorg101007978--3--031--17140--6_29)* have already proposed methods for this purpose.* have focused on extracting TTPs.

`Q4` *What are the related studies? How can they be categorized? Who are the noteworthy researchers in this field?*

`A4`: Related Research:
1. **TTP Extraction:**
   - *[Paragraph-based Estimation of Cyber Kill Chain Phase from Threat Intelligence Reports](#3--thin-tharaphe-thein-yuki-ezawa-shunta-nakagawa-keisuke-furumoto-yoshiaki-shiraishi-masami-mohri-yasuhiro-takano-and-masakatu-morii-2020-paragraph-based-estimation-of-cyber-kill-chain-phase-from-threat-intelligence-reports-journal-of-information-processing-28-2020-1025–1029)*, proposes a neural network to classify the statements into the five stages of the cyber kill chain, representing broad categories for all phases of a cyberattack.
   - *[TTPDrill: Automatic and Accurate Extraction of Threat Actions from Unstructured Text of CTI Sources](#1--ghaith-husari-ehab-al-shaer-mohiuddin-ahmed-bill-chu-and-xi-niu-2017-ttpdrill-automatic-and-accurate-extraction-of-threat-actions-from-unstructured-text-of-cti-sources-in-proceedings-of-the-33rd-annual-computer-security-applications-conference-103–115),* combines dependency parsers and heuristic rules to extract attaack patterns and maps them to kill chain phases.
   - *[AttacKG: Constructing Technique Knowledge Graph from Cyber Threat Intelligence Reports](#2--zhenyuan-li-jun-zeng-yan-chen-and-zhenkai-liang-2022-attackg-constructing-technique-knowledge-graph-from-cyber-threat-intelligence-reports-in-computer-security---esorics-2022---27th-european-symposium-on-research-in-computer-security-copenhagen-denmark-september-26-30-2022-proceedings-part-i-lecture-notes-in-computer-science-vol-13554-springer-589–609-httpsdoiorg101007978--3--031--17140--6_29),* designs graph-structured technique templates for each attack pattern and maps them to individual MITRE ATT&CK IDs using a graph alignment algorithm.
2. **Named Entity Recognition:**
   - *[RelExt: Relation Extraction using Deep Learning approaches for Cybersecurity Knowledge Graph Improvement](#4--aditya-pingle-aritran-piplai-sudip-mittal-anupam-joshi-james-holt-and-richard-zak-2019-relext-relation-extraction-using-deep-learning-approaches-for-cybersecurity-knowledge-graph-improvement-in-proceedings-of-the-2019-ieeeacm-international-conference-on-advances-in-social-networks-analysis-and-mining-879–886),* provides a dataset for cybersecurity named entity recognition.
   - *[Open-CyKG: An Open Cyber Threat Intelligence Knowledge Graph](#5--injy-sarhan-and-marco-rené-spruit-2021-open-cykg-an-open-cyber-threat-intelligence-knowledge-graph-knowledge-based-system-233-2021-107524),* uses Transformer-based models for named entity recognition.
   - *[Creating Cybersecurity Knowledge Graphs From Malware After Action Reports](#6--aritran-piplai-sudip-mittal-anupam-joshi-tim-finin-james-holt-and-richard-zak-2020-creating-cybersecurity-knowledge-graphs-from-malware-after-action-reports-ieee-access-8-2020-211691–211703),* extracts entities from malware after-action reports (AAR).
   - *[A comparative study of deep learning-based named entity recognition algorithms for cybersecurity](#7--soham-dasgupta-aritran-piplai-anantaa-kotal-and-anupam-joshi-2020-a-comparative-study-of-deep-learning-based-named-entity-recognition-algorithms-for-cybersecurity-in-2020-ieee-international-conference-on-big-data-big-data-ieee-2596–2604),* compares different neural network models, including CNN, LSTM, BERT, and CRF, for cybersecurity NER.
3. **Relation Extraction:**
   - *[RelExt: Relation Extraction using Deep Learning approaches for Cybersecurity Knowledge Graph Improvement](#4--aditya-pingle-aritran-piplai-sudip-mittal-anupam-joshi-james-holt-and-richard-zak-2019-relext-relation-extraction-using-deep-learning-approaches-for-cybersecurity-knowledge-graph-improvement-in-proceedings-of-the-2019-ieeeacm-international-conference-on-advances-in-social-networks-analysis-and-mining-879–886),* designs word embedding methods for extracting relations where the relation type is predetermined.
   - *[Open-CyKG: An Open Cyber Threat Intelligence Knowledge Graph](#5--injy-sarhan-and-marco-rené-spruit-2021-open-cykg-an-open-cyber-threat-intelligence-knowledge-graph-knowledge-based-system-233-2021-107524),* extracts relations that are not predetermined.
4. **Cyber Threat Intelligence Knowledge Graphs:**
   - *[Creating Cybersecurity Knowledge Graphs From Malware After Action Reports](#6--aritran-piplai-sudip-mittal-anupam-joshi-tim-finin-james-holt-and-richard-zak-2020-creating-cybersecurity-knowledge-graphs-from-malware-after-action-reports-ieee-access-8-2020-211691–211703),* generates knowledge graphs from CTI reports.
   - *[EXTRACTOR: Extracting attack behavior from threat reports](#8--kiavash-satvat-rigel-gjomemo-and-vn-venkatakrishnan-2021-extractor-extracting-attack-behavior-from-threat-reports-in-2021-ieee-european-symposium-on-security-and-privacy-eurosp-ieee-598–615),* uses IoCs as nodes in the attack graph.

`Q5` *What is key to the solution proposed in the paper?*

`A5`: The key to the solution is to extract attack patterns, as the attack pattern is a piece of text, not a token, which is supposed to include other types of entities. This paper uses TTPClassifier, a three-step method for extracting attack patterns. Firstly, the sentence is binary classified to determine whether it contains an attack pattern, then each token is binary classified to determine whether it belongs to an attack pattern, finally mapped to MITRE ATT&CK IDs.

`Q6` *How is the experiment in the paper designed?*

`A6`: This paper involves multiple stages that require NLP models to extract information. Therefore, the experiment trains many Transformer-based models for each stage. After comparing their effects, selects the model with the best performance.

`Q7` *What dataset is used for quantitative evaluation? Is the code open-sourced?*

`A7`: The [code](https://github.com/aiforsec/LADDER) is open-source on github, and ths datasets are described below: 
1. **Datasets for training NLP models:**
-  Datasets are collected from open-source datasets, including Cerberus, Rotexy, Judy, Google, and SpyNote RAT, representing Android malware from 2015 to 2022; These reports were written by security analysts from well-known organizations such as McAfee, Symantec, and Kaspersky, providing natural language descriptions of the emergence, spread, attack patterns, and IoCs of malware.

2. **Dataset for knowledge graph KG2:** 
- Datasets are crawled on the Internet using a web crawler program.

3. **Dataset for TTP classification comparation:**
-  Datasets are those CTI files manually annotated from MITRE ATT&CK.


## References

#### [ 1 ] Ghaith Husari, Ehab Al-Shaer, Mohiuddin Ahmed, Bill Chu, and Xi Niu. 2017. TTPDrill: Automatic and Accurate Extraction of Threat Actions from Unstructured Text of CTI Sources. In Proceedings of the 33rd annual computer security applications conference. 103–115.

#### [ 2 ] Zhenyuan Li, Jun Zeng, Yan Chen, and Zhenkai Liang. 2022. AttacKG: Constructing Technique Knowledge Graph from Cyber Threat Intelligence Reports. In Computer Security - ESORICS 2022 - 27th European Symposium on Research in Computer Security, Copenhagen, Denmark, September 26-30, 2022, Proceedings, Part I (Lecture Notes in Computer Science, Vol. 13554). Springer, 589–609. https://doi.org/10.1007/978- 3- 031- 17140- 6_29

#### [ 3 ] Thin Tharaphe Thein, Yuki Ezawa, Shunta Nakagawa, Keisuke Furumoto, Yoshiaki Shiraishi, Masami Mohri, Yasuhiro Takano, and Masakatu Morii. 2020. Paragraph-based Estimation of Cyber Kill Chain Phase from Threat Intelligence Reports. Journal of Information Processing 28 (2020), 1025–1029.

#### [ 4 ] Aditya Pingle, Aritran Piplai, Sudip Mittal, Anupam Joshi, James Holt, and Richard Zak. 2019. RelExt: Relation Extraction using Deep Learning approaches for Cybersecurity Knowledge Graph Improvement. In Proceedings of the 2019 IEEE/ACM International Conference on Advances in Social Networks Analysis and Mining. 879–886

#### [ 5 ] Injy Sarhan and Marco René Spruit. 2021. Open-CyKG: An Open Cyber Threat Intelligence Knowledge Graph. Knowledge Based System 233 (2021), 107524.

#### [ 6 ] Aritran Piplai, Sudip Mittal, Anupam Joshi, Tim Finin, James Holt, and Richard Zak. 2020. Creating Cybersecurity Knowledge Graphs From Malware After Action Reports. IEEE Access 8 (2020), 211691–211703.

#### [ 7 ] Soham Dasgupta, Aritran Piplai, Anantaa Kotal, and Anupam Joshi. 2020. A comparative study of deep learning based named entity recognition algorithms for cybersecurity. In 2020 IEEE International Conference on Big Data (Big Data). IEEE, 2596–2604.

#### [ 8 ] Kiavash Satvat, Rigel Gjomemo, and VN Venkatakrishnan. 2021. EXTRACTOR: Extracting attack behavior from threat reports. In 2021 IEEE European Symposium on Security and Privacy (EuroS&P). IEEE, 598–615.