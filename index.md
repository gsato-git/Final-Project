# **CLIM680 Final Project**

## **The spatial variabilities of global SST anomalies in 6ka and preindustrial era identified by 4 ENSO indices**

## **Go Sato**

## Introdction
El Niño–Southern Oscillation (ENSO) is one of the most dominant and strongest events in terms of its influence on the whole globe. To understand the impact of ENSO, there are 4 types of Nino index across the equatorial Pacific; Nino1+2, Nino3, Nino3.4, and Nino4. They are useful to capture the spatial ENSO, so it has been investigated that there are distinct types of ENSO events using these indices; Eastern type of El Nino, central El Nino, and La Nina throughout the Holocene (Carré et al., 2014; Karamperidou et al., 2015; Karamperidou and DiNezio 2022). Here I would like to examine the spatial distribution of ENSO events in the preindustrial era (hereafter piControl) and the mid-Holocene (6000 years ago) to know how the ENSO has been changed spatially using the 4 indices.

## Method
I use the Comunity Earth System Model 2.1 from the NCAR output for piControl and mid-Holocene. All input variables in the piControl run are set as the time 1850BP. For mid-Holocene run, the orbital parameters are set to 6000 years ago, and greenhouse gas concentrations are also set to the known values at 6000 years ago. The horizontal resolution is lat/lon; 0.5°/1.0°, and the temporal resolution is monthly. In each output, I picked up the last 200 years where the model outputs are considered to reach the equilibrium state. The analysis is following;

*preindustrial*
Calculating climatology (groupby function) => getting monthly global SST anomalies
Calculating the spatial mean of SST in 4 ENSO indices (sel function), then getting SSTAs
Extracting months with SSTA < -0.5℃ and > 0.5℃ => getting composite El Niño, La Niña, and Neutral months (sel function)
For 2 cases above, checking correlation coefficients between the individual ENSO index and global El Nino/La Nina composite SST anomalies with calculating statistical significance

*mid-Holocene*
Doing the same analysis for 6ka
Comparing the composite El Nino and La Nina SST anomalies between 6ka and preindustrial for 4 indices.


## Result

![image](https://github.com/user-attachments/assets/23554497-ff19-4f2b-b65e-596fbfbb981d)

[Nino index description from NCAR](https://climatedataguide.ucar.edu/climate-data/nino-sst-indices-nino-12-3-34-4-oni-and-tni)

### piControl
The number of El Nino events in Nino1+2 is the smallest among the 4 indices (603 months), and it increases as it goes to the west (703, 763, and 848, respectively). About La Nina events, there is no clear relationship among the indices. In Nino4, the composite El Nino and La Nina show the center of SST anomalies along the equator shifts slightly westward than other indices. Comparing the El Nino composite and La Nina composite in each index, the strong SST anomalies along the equator are meridionally more shrinked in La Nina than in El Nino.

![image](https://github.com/gsato-git/Final-Project/blob/plots/Nino1+2_composits_pi.png?raw=true)
![image](https://github.com/gsato-git/Final-Project/blob/plots/Nino3_composits_pi.png?raw=true)
![image](https://github.com/gsato-git/Final-Project/blob/plots/Nino3.4_composits_pi.png?raw=true)
![image](https://github.com/gsato-git/Final-Project/blob/plots/Nino4_composits_pi.png?raw=true)
Fig 2 Composits of El Nino and La Nina months in piControl

Fig 3 shows the linear regression analysis between each index and the global SST anomalies in piControl. All of the indices show there are strong positive correlations with SST anomalies along the equatorial Pacific in both El Nino and La Nina events. Thus, it means that when each index shows El Nino (La Nina) events, there are also warm (cold) SST anomalies along the equatorial Pacific. Conversely, all of the indices show negative correlations with the Maritime Continents SST anomalies. There are 2 pairs among the indices in terms of the correlation distribution. Nino1+2 and Nino4 show similar patterns, while Nino3 and Nino3.4 show similar patterns as well. Comparing the regression of El Nino to La Nina, the area of pronounced positive correlation along the equator is meridionally shrunk in the regression of La Nina in all indices. Zonally, however, the latter one is more extensive to the west than the former one. In El Nino plots, there are strong positive correlations (r >=0.5 or <=-0.5) in the South Pacific, the west coast of North America which is only in Nino4, and some coastal areas, while negative correlation in the North Pacific, the Maritime continent, and the SPCZ zone. From La Nina plots, we can see similar characteristics, but it is less clear. 

![image](https://github.com/gsato-git/Final-Project/blob/plots/Nino1+2_regression_pi.png?raw=true)
![image](https://github.com/gsato-git/Final-Project/blob/plots/Nino3_regression_pi.png?raw=true)
![image](https://github.com/gsato-git/Final-Project/blob/plots/Nino3.4_regression_pi.png?raw=true)
![image](https://github.com/gsato-git/Final-Project/blob/plots/Nino4_regression_pi.png?raw=true)
Fig 3 Linear regression between each index and the global SST anomalies in piControl


### midHolocene
As we see in the piControl outputs, the number of El Nino events increase from Nino1+2 to Nino4 (621, 674, 711, 764, respectively). All of indices show decreased number of El Nino events compared to piControl. However, there are increased number of La Nina events compared to piControl in all indices. Among the indices, the Nino1+2 and Nino4 indices show relatively smaller number of La Nina events (735 and 730, respectively) than Nino3 and Nino3.4 (782 and 778, respectively). The Nino4 shows the center of positive/negative anomalies along the equator is shifted to the west. 

![image](https://github.com/gsato-git/Final-Project/blob/plots/Nino1+2_composits_mh.png?raw=true)
![image](https://github.com/gsato-git/Final-Project/blob/plots/Nino3_composits_mh.png?raw=true)
![image](https://github.com/gsato-git/Final-Project/blob/plots/Nino3.4_composits_mh.png?raw=true)
![image](https://github.com/gsato-git/Final-Project/blob/plots/Nino4_composits_mh.png?raw=true)
Fig 4 Composits of El Nino and La Nina months in midHolocene

Fig 5 shows the linear regression analysis between each index and the global SST anomalies in the mid-Holocene. As we can see in Fig 3, all of indices show there are strong positive correlations with local SST anomalies along the equatorial Pacific and strong negative correlations with the SST anomalies in the Maritime Continents in both El Nino and La Nina events. Thus, the relationship between  El Nino (La Nina) events indicated in each index and warm (cold) SST anomalies along the equatorial Pacific is the same as the piControl outputs. Comparing the regression of El Nino to La Nina, the area of pronounced positive correlation along the equator is meridionally shrinked in the regression of La Nina in all indices. Zonally, however, the latter one is more extensive than the former one. In El Nino plots, there are strong positive correlations (r >=0.5 or <=-0.5) in the South Pacific, west coast of the North America, and Indian Ocean, while negative correlation in the North Pacific, the Maritime continent, and the SPCZ zone. From La Nina plots, we can see the similar charactersitics, but it is less clear.

![image](https://github.com/gsato-git/Final-Project/blob/plots/Nino1+2_regression_mh.png?raw=true)
![image](https://github.com/gsato-git/Final-Project/blob/plots/Nino3_regression_mh.png?raw=true)
![image](https://github.com/gsato-git/Final-Project/blob/plots/Nino3.4_regression_mh.png?raw=true)
![image](https://github.com/gsato-git/Final-Project/blob/plots/Nino4_regression_mh.png?raw=true)
Fig 5 Linear regression between each index and the global SST anomalies in midHolocene

### mid-Holocene vs. piControl
Fig 6 shows the differnces between the composit global SST in midHolocene and piControl for El Nino and La nina events with 95% statistical significance. Firstly, none of the panels shows the statistically significant SST differences. The SST differences themselves are also relatigvely small. All indices show basic charactersistics of the distribution of SST differences; positive SST anomalies in the western Pacific and eastern north Pacific in El Nino composits, and positive SST anomalies along the central-eastern equatorial Pacific and negative SST anomalies in the western Pacific and eastern basin. The Nino1+2 shows the most siginificant differences in El Nino composit, while the Nino4 shows the most significant differences in La Nina composit.

![image](https://github.com/gsato-git/Final-Project/blob/plots/Nino1+2_mh-pi.png?raw=true)
![image](https://github.com/gsato-git/Final-Project/blob/plots/Nino3_mh-pi.png?raw=true)
![image](https://github.com/gsato-git/Final-Project/blob/plots/Nino3.4_mh-pi.png?raw=true)
![image](https://github.com/gsato-git/Final-Project/blob/plots/Nino4_mh-pi.png?raw=true)
Fig 6 The composit global SST differences between midHolocene and piControl (the former - the latter)

## Discussion
Fig 2 and Fig 4 give us an idea that La Nina composit is a reversal of El Nino composit in most of regions. However, the number of events captured is strongly depending on an index, which means different types of ENSO events exist as previous research suggested (Karamperidou et al., 2015; Kao and Yu 2009; Karamperidou and DiNezio 2022; Carré et al., 2023). When we compare the number of events between piControl and midHolocene, there is no clear relatinoship, while some other research point out smaller or same number of El Nino events in the mid-Holocene (Cobb et al., 2013; Carré et al., 2014; Emile-Geay et al., 2015, Iwakiri and Watanabe 2019; Carré et al., 2021). Therefore, there must be a model bias regarding this ENSO capturing. Morever, since ENSO events are often discussed in terms of the variability (standard deviation), further investigation into the amplitude of these events are necessarly. 
When we look at the correlations between Nino indices and the global SST anomalies, the basic strong correlation with the SST anoamlies along the equatorial pacific are the same in both simulations. Not only the equatorial Pacific, but some other regions such as the west coast of North America also have strong correlations, so it might encourage us to investigate relationship with the SST anomalies various regions, as well. Altough the number of events varies depending on an index, there is a consistency between the captured events and the strong correlation with the SST anomalies along the equator. For example, the Nino4 captures smaller number of La Nina events in piControl (675 events compared to 730 in the mid-Holocene), so the region with strong correlation with Nino4 index is also small. 
Finally we can see that the SST differences between the piControl and the mid-Holocene is small without statistical significance in all indices. Given that each index is influenced by combination effect of some ENSO types events, it is inferred that the spatial pattern of ENSO changed and influenced along whole equatorial Pacific nonlinearly each other between the mid-Holocene and piControl.

## Conclusion
From the composit and regression analysis, we can know that the influence of ENSO events is strong along the equatorial Pacific in both piControl and mid-Holocene. Although there is no clear relationship in the changes of number of events from the mid-Holocene, the spatial distribution of strong correlated SST anomalies are consistent with the change of the number of events. Finally, since there is no statistical significance in the difference between the composit ENSO SST anomalies between the piControl and the mid-Holocene and the strongly index-depended, spatial pattern of ENSO events changed in this 6000 years and they affected the SST anomalies nonlinearly. 


## References
NCAR Nino SST Indices (Nino 1+2, 3, 3.4, 4; ONI and TNI) URL:https://climatedataguide.ucar.edu/climate-data/nino-sst-indices-nino-12-3-34-4-oni-and-tni

## codes
[piControl](https://github.com/gsato-git/Final-Project/blob/main/piControl.ipynb)

[mid-Holocene](https://github.com/gsato-git/Final-Project/blob/main/midHolocene.ipynb)

[mid-Holocene vs piControl](https://github.com/gsato-git/Final-Project/blob/main/pi-mh.ipynb)

## conda environment
[conda environment](https://ondemand.orc.gmu.edu/pun/sys/dashboard/files/fs//home/gsato/climate.yml)

