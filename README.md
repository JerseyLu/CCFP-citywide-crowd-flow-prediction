# CCFP-citywide-crowd-flow-prediction
We propose a novel Citywide Crowd Flow Prediction (CCFP) model based on the combination of statistical rules and machine learning (XGBoost, LightGBM, and CatBoost), which fully exploits the spatial dependence and two-level (weekly, and daily) periodicity of population flow to forecast crowd flow indexes in specific areas in the future.

**The key contributions of this study are as follows:**

• (i) Generating 24 weighted directed graphs through Node2Vec, which utilizes grid connection strength data to extract spatial characteristics of the 24 hourly-related regions.

• (ii) Extracting temporal features such as closeness, period, and trend, and integrating them with external factors like weather, epidemic, and migration data to forecast the hourly crowd flow for each area.

• (iii) Developing a citywide crowd flow prediction model using machine learning techniques, including LightGBM, XGBoost, and CatBoost.

• (iv) Incorporating factors like growth, base, weekly, and daily cyclic patterns into the model. Furthermore, it enhances prediction accuracy by multiplying the regression model’s results with trend factors.


Table 1 provides a detailed summary of the merits and demerits of the current techniques used to forecast crowd flow dynamics. Despite advancements, existing research on citywide crowd flow prediction still has limitations. Few models simultaneously consider temporal correlations, spatial dependencies, and external factors like weather, migration, and events. Our research seeks to overcome these inadequacies by offering a more comprehensive approach that incorporates all the mentioned aspects, aiming to enhance prediction accuracy while minimizing computational costs.

![image](https://github.com/JerseyLu/CCFP-citywide-crowd-flow-prediction/assets/104020492/b2d7c2ec-31e1-4263-8c9b-c066094e5b21)

To study citywide crowd flows in key areas, we obtained a dataset from DataFountain comprising crowd flow and migration data from 997 key areas, contributed by 11 units, covering the period from January 17 to February 15, 2020. Additionally, we integrated historical weather data from 2345 Weather Internet and epidemic data from China’s National Health Commission. This comprehensive dataset gave us insights into area interactions, population density, travel patterns, and potential abnormal events. The description of the datasets is provided in Table 2.

![image](https://github.com/JerseyLu/CCFP-citywide-crowd-flow-prediction/assets/104020492/cadef4c5-2444-47ea-9bfb-158036c306b4)

Figure 1 demonstrates the changing patterns of population density in Beijing over time. Notably, there was a peak between January 17 and January 24, followed by a significant decline. Factors such as the lack of travel restrictions and low public awareness before the first confirmed case of Covid-19 in Beijing on January 20, as well as extensive travel and movement before the Spring Festival (January 25, 2020), contributed to this trend. 

![image](https://github.com/JerseyLu/CCFP-citywide-crowd-flow-prediction/assets/104020492/6b00a0b1-d2ef-4f18-a0c7-cb56d037da6e)


The research goals are aimed to be addressed through the utilization of statistical rules and machine-learning methods in the CCFP model. Our CCFP model is structured into three layers: the data layer, the model layer, and the fusion layer. The data layer incorporates historical crowd flow data, migration data, epidemic data, weather data, holiday information, and area encoding data. The model layer consists of a machine learning model (indicated by the blue frame) and a factor model (indicated by the yellow frame). The machine learning model employs regression trees for prediction, while the factor model captures periodicity and trend patterns in crowd flow data, defining prediction factors such as growth and base. The fusion layer combines the predictive findings from the factor model with those from the machine learning model.

![image](https://github.com/JerseyLu/CCFP-citywide-crowd-flow-prediction/assets/104020492/b282d1f4-08dd-43db-9353-6ae34a8f3c5c)

Algorithm 1 outlines the CCFP model training process. We first construct the sample from the original sequence data and build ML models(lines 1-7). Then, we introduced a factor model(lines 8-14). Finally, the results of the factor model are combined with the machine learning model’s prediction findings(lines 15-17).

![image](https://github.com/JerseyLu/CCFP-citywide-crowd-flow-prediction/assets/104020492/889f3694-5d3e-4ea9-a41e-ea53be91759e)



To evaluate the impact of Area encoding features, Temporal features (closeness, period, and trend), and External features (weather, holiday, and epidemic) on predictions, we systematically excluded each of these feature categories from the input factors of our prediction model. This approach allowed us to measure the specific contributions of these feature categories to the model's performance. The optimal parameter settings for all tested models, determined through grid search optimization, are presented in Table 3.

![image](https://github.com/JerseyLu/CCFP-citywide-crowd-flow-prediction/assets/104020492/c74dc223-d258-4434-a538-cfdd018e4b06)

Subsequently, we compared the predictive results of our model with controlled feature removal to those of the original feature-inclusive model. The summarized findings in Figure 4 show that External and area-encoding factors have a moderate impact on predictive accuracy. In contrast, Temporal features significantly improve predictive accuracy.

![image](https://github.com/JerseyLu/CCFP-citywide-crowd-flow-prediction/assets/104020492/a11e7763-acaf-4ed0-b3a3-1e2f1266620e)

The convergence plots (As shown in Figure 5) showcase how the machine learning models perform during training and validation. These plots help us choose the best model and feature set for practical predictions. Notably, the XGBoost model, using all features, converges quickly with epoch=191 and an RMSE of 2.2167. This highlights its efficiency in utilizing features, feature selection, ensemble techniques, and hyperparameter tuning. In summary, our findings emphasize the importance of feature engineering and model selection for achieving strong predictive performance. Therefore, we can conclude that our proposed machine learning model achieves convergence, providing a solid foundation for practical applications.

![image](https://github.com/JerseyLu/CCFP-citywide-crowd-flow-prediction/assets/104020492/7ff54636-601a-4632-9a93-4e95691469e6)

To assess the performance of our CCFP model, we conduct comparative evaluations against a selection of well-established methodologies for sequence prediction and state-of-the-art approaches.

![image](https://github.com/JerseyLu/CCFP-citywide-crowd-flow-prediction/assets/104020492/8a6f3b9c-83e9-4df1-bec8-b5fed0247c7a)


In this study, we introduce an innovative fusion framework based on statistical rules and machine learning methods that harness historical trajectory data, meteorological insights, epidemic data, and spatial features to achieve precise forecasts of crowd flow dynamics within urban landscapes. The empirical validation of this approach, conducted through an analysis of human mobility patterns during the COVID-19 pandemic in Beijing, establishes its superior performance compared to established benchmarks. The model’s efficacy and applicability in predicting crowd movements empower urban administrations to proactively institute targeted interventions for curtailing the propagation of COVID-19, encompassing strategies of flow diversion, guidance, and control.

The key findings of this paper can be summarized as follows:

• (i) Explores spatial dependence and dual-level periodicity (daily and weekly) of human flow patterns and develops predictive models for hourly crowd flow, considering external factors like weather, epidemics, and migration.

• (ii) Temporal features ($closeness, period$, and $trend$) are integrated with external factors to provide accurate hourly crowd flow forecasts for each area. 

• (iii) Enhances prediction accuracy by incorporating $growth, base, weekly$, and $daily$, along with multiplying regression model results with trend factors.

• (iv) Empirical validation during the COVID-19 pandemic in Beijing demonstrates the model's superiority over benchmarks, enabling proactive interventions for COVID-19 control through crowd management.

**Citation**

Please refer to our paper.

```bibtex
@article{jiang2025data,
  title={Data-Driven Predictive Modeling of Citywide Crowd Flow for Urban Safety Management: A Case Study of Beijing, China},
  author={Jiang, He and Zhang, Xuxilu and Dong, Yao and Wang, Jianzhou},
  journal={Journal of Forecasting},
  volume={44},
  number={2},
  pages={730--752},
  year={2025},
  url={\url{https://doi-org.recursos.biblioteca.upc.edu/10.1002/for.3216}},
  publisher={Wiley Online Library}
}
