# Repository for the analysis of Arabidopsis field trial data
* Field 2007/08 = Field 2
* Field 2008/09 = Field 3
* Field 2009/10 = Field 4

## Figures
* **Figure 2**: corr_plot_all_fields.png based on cor_field*
* **Figure 3**: predictions_train_corr_plot.png based on **field*T_regressionACC_factor**
* **Figure 4**: predictions_loocv_corr_plot.png based on field*_pred_cv
* **Figure 5**: predictions_train_reduced_corr_plot.png based on **field*T_regressionACC_factorAIC**
* **Figure 6**: predictions_all_corr_plot.png based on **field*T_regressionACC_all_factor**
* predictions_test_corr_plot.png based on **field*T_regressionACC_factor** and **field*T_regressionACC_factor_red** (for 12 test accessions)


## Models
### LT50ACC model

*  **field*~~T_regressionACC_factor~~** model using *transformed* and *scaled* TRAINING data (with factor)

  * ``field4T_regressionACC_factor <- ``

    ``lm(LT50ACC ~ glc + frc + suc + raf + aa + mal + fum + pro + 
        bbch + anthoscore, data = field*_trainT_fac)``

* **field*T_regressionACC_all_factor** model using *transformed* and *scaled* ALL data (with factor)

  * ``field4T_regressionACC_factor <- ``

    ``lm(LT50ACC ~ glc + frc + suc + raf + aa + mal + fum + pro + 
        bbch + anthoscore, data = field*_allT_fac)``

* **field*T_regressionACC_factor_red** <u>reduced</u> model 

  * using ``step`` or ``stepAIC`` function with ``direction = "both"``
  * ``scope``: **field*T_regressionACC_all_factor**
    * **field2: raf, fum, mal (AIC=72.58)**
    * **field3: glc, raf, fum, pro (AIC=99.08)**
    * **field4: factor(bbch), raf, suc (AIC=94.17)**
    * ~~field4: factor(bbch), raf, suc, fum (AIC=83.17)~~
  * ````scope``: **field*T_regressionACC_all_fac_null** (both)
    * field3: factor(bbch), aa, suc (AIC=99.49)

  