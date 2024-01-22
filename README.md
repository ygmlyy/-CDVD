# -CDVD
This is additional supplementary material for the paper 'CDVD: Causal Dynamic Variational Deconfounder for Estimating Parameter Adjusting Effect'.
The real-world dataset is collected by China Mobile in the Shannxi, China. It consists of 328 gNBs between 2023/7/6 and 2023/7/20 with a 15-minute sampling interval. The dataset is split into training and testing sets in an 8:2 ratio.
Each gNB collected a total of 1344 samples. We chose 16 indicators as covariates, 2 indicators as the key performance indicators (KPIs) of interest, and the transmission power as the adjustable parameter (treatment).
Details are as follows.

Indicator name| Indicator Chinese name| Indicator type   
Intra-Frequency Handover Out Success Between eNodeB|	同频切换出成功次数|	X   
Inter-Frequency Handover Out Success Between eNodeB|	异频切换出成功次数|	X   
Inter-eNodeB Handover Out Success|	eNB间切换出成功次数|	X   
Inter-eNodeB Handover Out Request|	eNB间切换出请求次数|	X   
Intra-eNodeB Handover Out Success|	eNB内切换出成功次数|	X   
Inter-eNodeB S1 Handover Out Request|	eNB间S1切换出请求次数|	X   
Inter-eNodeB S1 Handover Out Success|	eNB间S1切换出成功次数|	X   
Inter-eNodeB X2 Handover Out Request|	eNB间X2切换出请求次数|	X   
Inter-eNodeB X2 Handover Out Success|	eNB间X2切换出成功次数|	X   
Total Handover Out|	切换出总次数|	X   
Handover Success QCI=1|	切换成功次数(QCI=1)|	X   
Handover Request QCI=1|  切换请求次数(QCI=1)| X   
Average RRC Connection|	RRC连接平均数|	X   
Downlink PRB Average Utilization|	下行PRB平均利用率|	X   
PDCCH Channel CCE Utilization|	PDCCH信道CCE占用率|	X   
Is D Frequency|	是否D频| X   
Transmission Power|	参考信号功率|	T   
Uplink Traffic|	上行流量(MB)|	Y   
Downlink Traffic|	下行流量(MB)|	Y   

We predicted the values for 96 points (one day) after adjustment. The experiments were conducted on Nvidia RTX 4090 GPU. To train the CDVD model, the learning rate is set to 0.0001, the training batch size is set
to 32, and the training epoch is set to 20. we used Adam as our optimizer. The encoder and decoder in representation learning module is BiLSTM network with three layers. The dropout rate is set to 0.1. We implemented the algorithms by the PyTorch framework. 
The experiment verified the accuracy and robustness of the CDVD model in estimating the effects of parameter adjustments. The proposed CDVD has implication for practice and can provide support for wireless network optimization.
