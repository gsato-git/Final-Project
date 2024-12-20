# **CLIM680 Final Project**

## **The spatial variabilities of global SST anomalies in 6ka and preindustrial era identified by 4 ENSO indices**

## **Go Sato**

## Introdction
El Niño–Southern Oscillation (ENSO) is one of the most dominant and strongest events in terms of its influence on the whole globe, and research has been revealed its strong variations on orbital time scales due to changes in latitudinal and seasonal distribution of incoming solar radiation (Lu et al., 2018; Brown et al., 2020; Carré et al., 2021).

To understand the spatial pattern of ENSO, there are 4 types of Nino index across the equatorial Pacific; Nino1+2, Nino3, Nino3.4, and Nino4. It has been investigated that how the distinct types of ENSO events has been changing using these indices; Eastern type of El Nino, central El Nino, and La Nina throughout the Holocene (Carré et al., 2014; Karamperidou et al., 2015; Karamperidou and DiNezio 2022). Especially, the mid-Holocene exhibits the increased solar radiation in the boreal summer and decreased solar radiation in the boreal winter, so that this period gives us important insights into the climate response to very distinctive solar radiation changes. Here I would like to use the 4 indices and examine the spatial distribution of ENSO events in the preindustrial era (hereafter piControl) and 6000 years ago (hereafter mid-Holocene) to know how the ENSO has been changed spatially under different solar radiation inputs.

## Method
I use the outputs from the Comunity Earth System Model 2 ([CESM2](https://www.cesm.ucar.edu/models/cesm2)) by the NCAR for piControl and mid-Holocene. All input variables in the piControl run are set as the time 1850BP. For mid-Holocene run, the orbital parameters are set to 6000 years ago, and greenhouse gas concentrations are also set to the known values at 6000 years ago. The horizontal resolution is lat/lon; 0.5°/1.0°, and the temporal resolution is monthly. In each output, I picked up the last 200 years where the model outputs are considered to reach the equilibrium state. The analysis is following;

*piControl*

1. Getting the last 200 years (sel function)

2. Calculating monthly global SST climatologies (groupby function) => getting monthly global SST anomalies by substracting the climatology from each month's SST

3. Creating 4 Nino indices (sel function)

4. Getting El Nino, La Nina, and Neutral months (where function) by specifying as El Nino; SST anomaly > 0.5℃, La Nina; SST anomaly < -0.5℃; Neutral; -0.5℃ <= SST anomaly <= 0.5℃

5. Getting the global SST anomalies in the same preiods as each Nino index (sel function and groupby function)

6. Getting the composite SST anomalies in 4 indices (sel&dropna function and scipy.stats ttest_ind)

7. For El Nino and La Nina months, calculating the correlation coefficients between each ENSO index and global El Nino/La Nina composite SST anomalies with statistical significance (scipy.stats linregress)

*mid-Holocene*

   Doing the same analysis as the piControl

*mid-Holocene vs. piControl*

   Comparing the composite El Nino and La Nina SST anomalies between mid-Holocene and piControl for 4 indices (scipy.stats ttest_ind)


## Result

![image](https://github.com/user-attachments/assets/23554497-ff19-4f2b-b65e-596fbfbb981d)

[Nino index description from NCAR](https://climatedataguide.ucar.edu/climate-data/nino-sst-indices-nino-12-3-34-4-oni-and-tni)

### piControl
The number of El Nino events in Nino1+2 is the smallest among the 4 indices (603 months), and it increases as it goes to the west (703, 763, and 848, respectively). About La Nina events, there is no clear relationship among the indices. In each index, the strongest anomalies are close to the location of index. For example, in Nino4, the composite El Nino and La Nina show the center of SST anomalies along the equator shifts slightly westward than other indices. Comparing the El Nino composite and La Nina composite in each index, the strong SST anomalies along the equator are meridionally more expanded in El Nino than in La Nina.

![image](https://github.com/gsato-git/Final-Project/blob/plots/Nino1+2_composite_pi.png?raw=true)
![image](https://github.com/gsato-git/Final-Project/blob/plots/Nino3_composite_pi.png?raw=true)
![image](https://github.com/gsato-git/Final-Project/blob/plots/Nino3.4_composite_pi.png?raw=true)
![image](https://github.com/gsato-git/Final-Project/blob/plots/Nino4_composite_pi.png?raw=true)
Fig 2 Composits of El Nino and La Nina months in piControl

Fig 3 shows the linear regression analysis between each index and the global SST anomalies in piControl. All of the indices show there are strong positive correlations with SST anomalies along the equatorial Pacific in both El Nino and La Nina events. Thus, it means that when each index shows El Nino (La Nina) events, there are also warm (cold) SST anomalies along the equatorial Pacific. Conversely, all of the indices show negative correlations with the Maritime Continents SST anomalies.  Comparing the regression of El Nino to La Nina, the area of pronounced positive correlation along the equator is meridionally shrunk in the regression of La Nina in all indices. Zonally, however, the latter one is more extensive to the west than the former one. In El Nino plots, there are strong positive correlations (r >=0.5 or <=-0.5) in the South Pacific, the west coast of North America which is only in Nino4, and some coastal areas, while negative correlation in the North Pacific, the Maritime continent, and the SPCZ zone. From La Nina plots, we can see similar characteristics, but it is less clear. These patterns are similar to each other between Nino3 and Nino3.4, while Nino1+2 and Nino4 show the center of strong correlations close to the eastern side and western side, respectively.

![image](https://github.com/gsato-git/Final-Project/blob/plots/Nino1+2_regression_pi.png?raw=true)
![image](https://github.com/gsato-git/Final-Project/blob/plots/Nino3_regression_pi.png?raw=true)
![image](https://github.com/gsato-git/Final-Project/blob/plots/Nino3.4_regression_pi.png?raw=true)
![image](https://github.com/gsato-git/Final-Project/blob/plots/Nino4_regression_pi.png?raw=true)
Fig 3 Linear regression between each index and the global SST anomalies in piControl


### mid-Holocene
As we see in the piControl outputs, the number of El Nino events increases from Nino1+2 to Nino4 (621, 674, 711, 764, respectively). All of the indices show a decreased number of El Nino events compared to piControl. However, there are increased number of La Nina events compared to piControl in all indices. Among the indices, the Nino1+2 and Nino4 indices show a relatively smaller number of La Nina events (735 and 730, respectively) than Nino3 and Nino3.4 (782 and 778, respectively). The Nino4 shows the center of positive/negative anomalies along the equator is shifted to the west. 

![image](https://github.com/gsato-git/Final-Project/blob/plots/Nino1+2_composite_mh.png?raw=true)
![image](https://github.com/gsato-git/Final-Project/blob/plots/Nino3_composite_mh.png?raw=true)
![image](https://github.com/gsato-git/Final-Project/blob/plots/Nino3.4_composite_mh.png?raw=true)
![image](https://github.com/gsato-git/Final-Project/blob/plots/Nino4_composite_mh.png?raw=true)
Fig 4 Composits of El Nino and La Nina months in midHolocene

Fig 5 shows the linear regression analysis between each index and the global SST anomalies in the mid-Holocene. As we can see in Fig 3, all of the indices show there are strong positive correlations with local SST anomalies along the equatorial Pacific and strong negative correlations with the SST anomalies in the Maritime Continents in both El Nino and La Nina events. Thus, the relationship between  El Nino (La Nina) events indicated in each index and warm (cold) SST anomalies along the equatorial Pacific is the same as the piControl outputs. Comparing the regression of El Nino to La Nina, the area of pronounced positive correlation along the equator is meridionally less expanded in the regression of La Nina in all indices. Zonally, however, the latter one is more extensive than the former one. In El Nino plots, there are strong positive correlations (r >=0.5 or <=-0.5) in the South Pacific, the west coast of North America, and the Indian Ocean, while negative correlations in the North Pacific, the Maritime continent, and the SPCZ zone. From La Nina plots, we can see similar characteristics, but it is less clear.

![image](https://github.com/gsato-git/Final-Project/blob/plots/Nino1+2_regression_mh.png?raw=true)
![image](https://github.com/gsato-git/Final-Project/blob/plots/Nino3_regression_mh.png?raw=true)
![image](https://github.com/gsato-git/Final-Project/blob/plots/Nino3.4_regression_mh.png?raw=true)
![image](https://github.com/gsato-git/Final-Project/blob/plots/Nino4_regression_mh.png?raw=true)
Fig 5 Linear regression between each index and the global SST anomalies in midHolocene

### mid-Holocene vs. piControl
Fig 6 shows the differences between the composite global SST in mid-Holocene and piControl for El Nino and La Nina events with 95% statistical significance. Firstly, none of the panels shows statistically significant SST differences. The SST differences themselves are also relatively small. All indices show basic characteristics of the distribution of SST differences; positive SST anomalies in the western Pacific and eastern north Pacific in El Nino composites, positive SST anomalies along the central-eastern equatorial Pacific, and negative SST anomalies in the western Pacific and eastern basin. The Nino1+2 shows the most significant differences in the El Nino composite, while the Nino4 shows the most significant differences in the La Nina composite.

![image](https://github.com/gsato-git/Final-Project/blob/plots/Nino1+2_mh-pi.png?raw=true)
![image](https://github.com/gsato-git/Final-Project/blob/plots/Nino3_mh-pi.png?raw=true)
![image](https://github.com/gsato-git/Final-Project/blob/plots/Nino3.4_mh-pi.png?raw=true)
![image](https://github.com/gsato-git/Final-Project/blob/plots/Nino4_mh-pi.png?raw=true)
Fig 6 The composit global SST differences between midHolocene and piControl (the former - the latter)

## Discussion
Fig 2 and Fig 4 give us an idea that the La Nina composite is a reversal of the El Nino composite in most regions. In addition, the strong SST anomalies are always near the index region in each index output. Therefore, my research project could capture that each index has beed designed to understand different spatial mode of ENSO events. When we compare the number of El Nino and La Nina events between piControl and midHolocene, there is no clear relationship. This is consistent with several previous studies indicating smaller or the same number of El Nino events in the mid-Holocene (Cobb et al., 2013; Carré et al., 2014; Emile-Geay et al., 2015, Iwakiri and Watanabe 2019; Carré et al., 2021). However, Fig 6 shows weaker El Nino and La Nina events in the mid-Holocene than in the preindustrial era. Therefore, different types of ENSO events changed differently and reduced intensity as an overall, they affect multiple index regions instead of "1 to 1" relationship, as previous research suggested (Karamperidou et al., 2015; Kao and Yu 2009; Karamperidou and DiNezio 2022; Carré et al., 2023). Neverthless, we still need to be careful about the fact that none of indices show statistical significanes. Moreover, there must be some model biases regarding this ENSO capturing specific to the CESM2.
When we look at the correlations between Nino indices and the global SST anomalies, the basic strong correlation with the SST anomalies along the equatorial pacific is the same in both simulations. Not only the equatorial Pacific, but some other regions such as the west coast of North America also have strong correlations, so it might encourage us to investigate the relationship with the SST anomalies in various regions, as well. Although the number of events varies depending on an index, there is a consistency between the captured events and the strong correlation with the SST anomalies along the equator. For example, the Nino4 captures a smaller number of La Nina events in piControl (675 events compared to 730 in the mid-Holocene), so the region with a strong correlation with the Nino4 index is also small. 

## Conclusion
From the composite and regression analysis, we know that the influence of ENSO events is strong along the equatorial Pacific in both piControl and mid-Holocene and more pronounced anomalies nearby each index. Although there is no clear relationship between the changes in the number of events from the mid-Holocene, the spatial distribution of strongly correlated SST anomalies is consistent with the change in the number of events. Finally, since there is no statistical significance in the difference between the composite ENSO SST anomalies of the piControl and the mid-Holocene with sloghtly decreased instensities, spatial pattern of ENSO events has been changed since 6000 years ago and they have been affecting the global SST distributions complicatedly. 

## References
Brown, J. R. et al., Comparison of past and future simulations of ENSO in CMIP5/PMIP3 and CMIP6/PMIP4 models, Clim. Past, 16, 1777–1805 (2020). https://doi.org/10.5194/cp-16-1777-2020

Berger, A.; Loutre, M.-F. Insolation values for the climate of the last 10 million years. Quat. Sci. Rev, 10, 297–317 (1991). https://doi.org/10.1016/0277-3791(91)90033-Q

Emile-Geay Julien et al. Links between tropical Pacific seasonal, interannual and orbital variability during the Holocene. Nature Geosci 9, 168–173 (2016). https://doi.org/10.1038/ngeo2608

Karamperidou Cristina et al., The response of ENSO flavors to mid-Holocene climate: Implications for proxy interpretation, Paleoceanography, 30, 527–547 (2015). https://doi.org/10.1002/2014PA002742

Karamperidou, C., DiNezio, P.N. Holocene hydroclimatic variability in the tropical Pacific explained by changing ENSO diversity. Nat Commun 13, 7244 (2022). https://doi.org/10.1038/s41467-022-34880-8

Kim M. Cobb et al., Highly Variable El Niño–Southern Oscillation Throughout the Holocene.Science339,67-70(2013). https://doi.org/10.1126/science.1228246

Matthieu Carré et al., High-resolution marine data and transient simulations support orbital forcing of ENSO amplitude since the mid-Holocene. Quaternary Science Reviews, 268-107125 (2021).https://doi.org/10.1016/j.quascirev.2021.107125

Matthieu Carré et al., Holocene history of ENSO variance and asymmetry in the eastern tropical Pacific.Science345,1045-1048(2014).https://doi.org/10.1126/science.1252220

National Center for Atmospheric Research (NCAR). (n.d.). Niño SST indices: Niño 1+2, 3, 3.4, 4, ONI, and TNI. UCAR Climate Data Guide. Retrieved December 3, 2024, from https://climatedataguide.ucar.edu/climate-data/nino-sst-indices-nino-12-3-34-4-oni-and-tni

## codes
[piControl](https://github.com/gsato-git/Final-Project/blob/main/piControl.ipynb)

[mid-Holocene](https://github.com/gsato-git/Final-Project/blob/main/midHolocene.ipynb)

[mid-Holocene vs piControl](https://github.com/gsato-git/Final-Project/blob/main/pi-mh.ipynb)

## conda environment
[conda environment](https://ondemand.orc.gmu.edu/pun/sys/dashboard/files/fs//home/gsato/climate.yml)

