# secure_inference_edge

## Progression-1:

![image](https://user-images.githubusercontent.com/47445756/233863861-60146086-d3eb-4e6d-ad2b-44d39658ac67.png)

### References
[1] Lee, Taegyeong, et al. "Occlumency: Privacy-preserving remote deep-learning inference using SGX." The 25th Annual International Conference on Mobile Computing and Networking. 2019.

[2] Götzfried, Johannes, et al. "Cache attacks on Intel SGX." Proceedings of the 10th European Workshop on Systems Security. 2017.

[3] Murdock, Kit, et al. "Plundervolt: Software-based fault injection attacks against Intel SGX." 2020 IEEE Symposium on Security and Privacy (SP). IEEE, 2020.

[4] Sun, Zhichuang, et al. "ShadowNet: A Secure and Efficient On-device Model Inference System for Convolutional Neural Networks." 2023 IEEE Symposium on Security and Privacy (SP). IEEE Computer Society, 2022.

[5] Shen, Tianxiang, et al. "{SOTER}: Guarding Black-box Inference for General Neural Networks at the Edge." 2022 USENIX Annual Technical Conference (USENIX ATC 22). 2022.

[6] Khandaker, Mustakimur Rahman, et al. "COIN attacks: On insecurity of enclave untrusted interfaces in SGX." Proceedings of the Twenty-Fifth International Conference on Architectural Support for Programming Languages and Operating Systems. 2020.

[7] Tramer, Florian, and Dan Boneh. "Slalom: Fast, verifiable and private execution of neural networks in trusted hardware." arXiv preprint arXiv:1806.03287 (2018).

[8] Asvadishirehjini, Aref, Murat Kantarcioglu, and Bradley Malin. "Goat: Gpu outsourcing of deep learning training with asynchronous probabilistic integrity verification inside trusted execution environment." arXiv preprint arXiv:2010.08855 (2020).

[9] Cai, Yi, et al. "Enabling Secure in-Memory Neural Network Computing by Sparse Fast Gradient Encryption." ICCAD. 2019.

[10] Lin, Ning, et al. "Chaotic weights: A novel approach to protect intellectual property of deep neural networks." IEEE Transactions on Computer-Aided Design of Integrated Circuits and Systems 40.7 (2020): 1327-1339.

[11] Juvekar, Chiraag, Vinod Vaikuntanathan, and Anantha Chandrakasan. "{GAZELLE}: A low latency framework for secure neural network inference." 27th USENIX Security Symposium (USENIX Security 18). 2018.

[12] Jie, Yixin, et al. "Multi-Party Secure Computation with Intel SGX for Graph Neural Networks." ICC 2022-IEEE International Conference on Communications. IEEE, 2022.

[13] Leyton-Brown, Kevin, and Yoav Shoham. "Essentials of game theory: A concise multidisciplinary introduction." Synthesis lectures on artificial intelligence and machine learning 2.1 (2008): 1-88.


## Progression-2:


| Work            | Platform                       | Computation Overhead | Attacks on Edge Device                                                                                                                       | Model Confidentiality | Data Confidentiality | Integrity Check | Reduction in Accuracy | Model Modification | Utility of Edge Accelerators | Physical Attack Consideration | Black Box Privacy Attacks Possibility |
| --------------- | ------------------------------ | -------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- | --------------------- | -------------------- | --------------- | --------------------- | ------------------ | ---------------------------- | ----------------------------- | ------------------------------------- |
| CryptoNets [3]  | MLaaS                          | high                 | Leakage of Architecture Information.                                                                                                         | Negative              | High                 | False           | Small                 | Significant        | None                         | None                          | Yes                                   |
| AutoPrivacy [4] | MLaaS                          | high                 | Leakage of Architecture Information.                                                                                                         | Negative              | High                 | False           | Small                 | Significant        | None                         | None                          | Yes                                   |
| MiniONN [5]     | MLaaS                          | high                 | Leakage of Architecture Information.                                                                                                         | Negative              | High                 | False           | Small                 | Significant        | None                         | None                          | Yes                                   |
| GAZELLE [6]     | MLaaS                          | high                 | Leakage of Architecture Information.                                                                                                         | Negative              | High                 | False           | Small                 | Significant        | None                         | None                          | Yes                                   |
| DELPHI [7]      | MLaaS                          | high                 | Leakage of Architecture Information.                                                                                                         | Negative              | High                 | False           | Small                 | Significant        | None                         | None                          | Yes                                   |
| SecDeep [8]     | ARM Trustzone                  | medium               | Network Completion[1,2] and Cold Boot Attack. Model Architecture is leaked through Side-channel attack. Side-channel attack [9], bus probing | Partial               | High                 | True            | None                  | None               | Yes                          | No                            | Yes                                   |
| GaurdiaNN [10]  | Edge Devices with TEE and SRAM | medium               | Model architecture leakage through bus probing (CPU-DRAM), SRAM compromise [13]                                                              | Full                  | High                 | False           | None                  | None               | Yes (Cryptographic)          | Yes                           | Yes                                   |
| DarkneTZ [11]   | Edge Devices with TEE          | low                  | Physical Attacks (bus probing), Network Completion [1,2]. TEE compromise                                                                     | Partial               | High                 | False           | None                  | None               | No                           | No                            | Partially Yes                         |
| PUF-PIM [12]    | Edge Devices with SRAM         | medium               | SRAM compromise [13]                                                                                                                         | Full                  | None                 | False           | None                  | none               | Yes                          | No                            | Yes                                   |
| Occlumency [14] | MLaaS (Cloud Intel SGX)        | medium               | SGX vulnerabilities (like side channel, roll back and DoS)                                                                                   | Partial               | High                 | Yes             | None                  | None               | No                           | No                            | No                                    |
| ShadowNet [15]  | Edge Device with TEE           | medium               | SGX side channel attacks                                                                                                                     | Partial               | No                   | No              | None                  | Small              | Yes                          | Yes                           | No                                    |
| SOTER [16] | Edge Devices with TEE | medium | SGX Vulnerabilities                                                  | Partial | Yes | Yes | Small | Small | Yes | Yes | Yes |
| ---------- | --------------------- | ------ | -------------------------------------------------------------------- | ------- | --- | --- | ----- | ----- | --- | --- | --- |
| SFGE [17]  | Edge devices NVM      | low    | Network Completion [1,2], Prone to Side Channel and Physical attacks | Full    | No  | No  | None  | Small | Yes | No  | Yes |

### References
[1] Tran, Cong, et al. "${\sf DeepNC} $ DeepNC: Deep Generative Network Completion." IEEE transactions on pattern analysis and machine intelligence 44.4 (2020): 1837-1852.

[2] Kim, Myunghwan, and Jure Leskovec. "The network completion problem: Inferring missing nodes and edges in networks." Proceedings of the 2011 SIAM international conference on data mining. Society for Industrial and Applied Mathematics, 2011.

[3] Gilad-Bachrach, Ran, et al. "Cryptonets: Applying neural networks to encrypted data with high throughput and accuracy." International conference on machine learning. PMLR, 2016.

[4] Lou, Qian, Song Bian, and Lei Jiang. "Autoprivacy: Automated layer-wise parameter selection for secure neural network inference." Advances in Neural Information Processing Systems 33 (2020): 8638-8647.

[5] Liu, Jian, et al. "Oblivious neural network predictions via minionn transformations." Proceedings of the 2017 ACM SIGSAC conference on computer and communications security. 2017.

[6] Juvekar, Chiraag, Vinod Vaikuntanathan, and Anantha Chandrakasan. "{GAZELLE}: A low latency framework for secure neural network inference." 27th {USENIX} Security Symposium ({USENIX} Security 18). 2018.

[7] Srinivasan, Wenting Zheng, P. M. R. L. Akshayaram, and Popa Raluca Ada. "DELPHI: A cryptographic inference service for neural networks." Proc. 29th USENIX Secur. Symp. 2019.

[8] Liu, Renju, et al. "Secdeep: Secure and performant on-device deep learning inference framework for mobile and iot devices." Proceedings of the International Conference on Internet-of-Things Design and Implementation. 2021.

[9] Hua, Weizhe, Zhiru Zhang, and G. Edward Suh. "Reverse engineering convolutional neural networks through side-channel information leaks." Proceedings of the 55th Annual Design Automation Conference. 2018.

[10] Choi, Jinwoo, et al. "GuardiaNN: Fast and Secure On-Device Inference in TrustZone Using Embedded SRAM and Cryptographic Hardware." Proceedings of the 23rd conference on 23rd ACM/IFIP International Middleware Conference. 2022.

[11] Mo, Fan, et al. "Darknetz: towards model privacy at the edge using trusted execution environments." Proceedings of the 18th International Conference on Mobile Systems, Applications, and Services. 2020.

[12] Li, Wen, et al. "Leveraging Memory PUFs and PIM-based encryption to secure edge deep learning systems." 2019 IEEE 37th VLSI Test Symposium (VTS). IEEE, 2019.

[13] Mahmod, Jubayer, and Matthew Hicks. "SRAM has no chill: exploiting power domain separation to steal on-chip secrets." Proceedings of the 27th ACM International Conference on Architectural Support for Programming Languages and Operating Systems. 2022.

[14] Lee, Taegyeong, et al. "Occlumency: Privacy-preserving remote deep-learning inference using sgx." The 25th Annual International Conference on Mobile Computing and Networking. 2019.

[15] Sun, Zhichuang, et al. "ShadowNet: A Secure and Efficient On-device Model Inference System for Convolutional Neural Networks." 2023 IEEE Symposium on Security and Privacy (SP). IEEE Computer Society, 2022.

[16] Shen, Tianxiang, et al. "{SOTER}: Guarding Black-box Inference for General Neural Networks at the Edge." 2022 USENIX Annual Technical Conference (USENIX ATC 22). 2022.

[17] Cai, Yi, et al. "Enabling secure in-memory neural network computing by sparse fast gradient encryption." 2019 IEEE/ACM International Conference on Computer-Aided Design (ICCAD). IEEE, 2019.

[18] Salehi, Mohsen, and Karthik Pattabiraman. "Poster AutoPatch: Automatic Hotpatching of Real-Time Embedded Devices." Proceedings of the 2022 ACM SIGSAC Conference on Computer and Communications Security. 2022.





## Progression-3: 

![image](https://user-images.githubusercontent.com/47445756/233863410-e4f69772-9080-4a62-a79e-9c2677ce7a9e.png)


![image](https://user-images.githubusercontent.com/47445756/233863421-8edf9a0c-2b01-490c-97db-72b86f428cc0.png)


### References
[1]
Rakin , Adnan Siraj, et al. Deepsteal : Advanced model extractions leveraging efficient weight stealing in 2022 IEEE Symposium on Security and Privacy (SP) SP). IEEE, 2022

[2]
Zhu, Yuankun , et al. "Hermes Attack: Steal DNN Models with Lossless Inference USENIX Security Symposium .

[3]
Yan, Mengjia , Christopher Fletcher, and Josep Torrellas . "Cache telepathy: Leveraging shared resource attacks to learn DNN USENIX Security Symposium .

[4] Shan, Shawn, et al. "Post
breach recovery: Protection against white box adversarial examples for leaked DNN models." Proceedings of the 2022 ACM SIGSAC Conference on Computer
and Communications Security .

[5]
Mo, Fan, et al. " Darknetz : towards model privacy at the edge using trusted execution Proceedings of the 18th International Conference on Mobile Systems, Applications, and
Services .

[6]
Hashemi, Hanieh , Yongqin Wang, and Murali Annavaram . DarKnight : An accelerated framework for privacy and integrity preserving deep learning using trusted MICRO 54: 54th
Annual IEEE/ACM International Symposium on Microarchitecture .

[7]
Hu, Xing, et al. " Deepsniffer : A dnn model extraction framework based on learning architectural hints." Proceedings of the Twenty Fifth International Conference on Architectural Support for
Programming Languages and Operating Systems .

[8]
Choi, Jinwoo , et al. GuardiaNN : Fast and Secure On Device Inference in TrustZone Using Embedded SRAM and Cryptographic Hardware." Proceedings of the 23rd conference on 23rd
ACM/IFIP International Middleware Conference .

[9]
Cao, Xiaoyu , Jinyuan Jia, and Neil Zhenqiang Gong. " IPGuard : Protecting intellectual property of deep neural networks via fingerprinting the classification Proceedings of the
2021 ACM Asia Conference on Computer and Communications Security .

[10]
Hanzlik, Lucjan , et al. Mlcapsule : Guarded offline deployment of machine learning as a Proceedings of the IEEE/CVF conference on computer vision and pattern recognition .
2021.

[11]
Kesarwani , Manish, et al. "Model extraction warning in mlaas paradigm." Proceedings of the 34th Annual Computer Security Applications Conference .

[12]
Hou, Jiahui , et al. "Model Protection: Real time privacy preserving inference service for model privacy at the edge." IEEE Transactions on Dependable and Secure Computing 19.6 (2021):
4270 4284.

[13]
Juuti , Mika, et al. "PRADA: protecting against DNN model stealing 2019 IEEE European Symposium on Security and Privacy ( EuroS&P )). IEEE,

[14]
Zhang, Jialong , et al. "Protecting intellectual property of deep neural networks with Proceedings of the 2018 on Asia Conference on Computer and Communications
Security .

[15]
Sun, Zhichuang , et al. ShadowNet : A Secure and Efficient On device Model Inference System for Convolutional Neural Networks." 2023 IEEE Symposium on Security and Privacy (SP) SP).
IEEE Computer Society, 2022.






## Progression-4:

![image](https://user-images.githubusercontent.com/47445756/233864378-89ecdb66-b243-40c4-8734-3bb358b85f67.png)
![image](https://user-images.githubusercontent.com/47445756/233864396-02af308c-f70c-43ef-860e-c87e326ef4e2.png)

### References
[1]
Lee, Taegyeong , et al. "Occlumency: Privacy preserving remote deep learning inference using sgx The 25th Annual International Conference on Mobile Computing and
Networking .

[2] Kim,
Kyungtae , et al. "Vessels: Efficient and scalable deep learning prediction on trusted Proceedings of the 11th ACM Symposium on Cloud Computing .

[3] Truong, Jean
Baptiste, et al. "Memory efficient deep learning inference in trusted execution environments." 2021 IEEE International Conference on Cloud Engineering
( IC2E). IEEE,

[4] Shen,
Tianxiang , et al. "{SOTER}: Guarding Black box Inference for General Neural Networks at the Edge." 2022 USENIX Annual Technical Conference (USENIX ATC 22) 22).
2022.

[5] Hua,
Weizhe , et al. GuardNN : secure accelerator architecture for privacy preserving deep learning." Proceedings of the 59th ACM/IEEE Design Automation Conference .
2022.

[6]
Li, Yuepeng , et al. "Lasagna: Accelerating secure deep learning inference in sgx enabled edge cloud." Proceedings of the ACM Symposium on Cloud Computing .

[7] Xiang,
Yecheng , et al. Aegisdnn : Dependable and timely execution of dnn tasks with sgx 2021 IEEE Real Time Systems Symposium (RTSS) RTSS). IEEE,

[8] Guo,
Yunqi , et al. "A model obfuscation approach to IoT 2021 IEEE Conference on Communications and Network Security (CNS) CNS). IEEE,

[9] Shrivastava, Nivedita, and Smruti R. Sarangi. "
Seculator : A Fast and Secure Neural Processing arXiv preprint arXiv:2204.08951 (

[10] Hashemi,
Hanieh , Yongqin Wang, and Murali Annavaram . DarKnight : An accelerated framework for privacy and integrity preserving deep learning using trusted
hardware." MICRO 54: 54th Annual IEEE/ACM International Symposium on Microarchitecture .

[11]
Niu , Yue, Ramy E. Ali, and Salman Avestimehr . "3LegRace: Privacy Preserving DNN Training over TEEs and GPUs." arXiv preprint arXiv:2110.01229

[12]
Mo, Fan, et al. " Darknetz : towards model privacy at the edge using trusted execution Proceedings of the 18th International Conference on Mobile Systems,
Applications, and Services .

[13]
Tramer , Florian, and Dan Boneh . "Slalom: Fast, verifiable and private execution of neural networks in trusted arXiv preprint arXiv:1806.03287


