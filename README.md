# How can we maximise profit as an airbnb host?


## Contributors:
 - Isaac Chun Jun Heng U2221389B
 - J'sen Ong Jia Xuan U2220457J
 - Tang Teck Meng U2221809C

## Code located in:

1. (Master File) [AirbnbAnalysis.ipynb](https://github.com/isaacchunn/SC1015_MiniPrj_Airbnb/blob/main/AirbnbAnalysis.ipynb)
2. [EDA_First25.ipynb](https://github.com/isaacchunn/SC1015_MiniPrj_Airbnb/blob/main/EDA_First25.ipynb)
3. [EDA_Middle25.ipynb](https://github.com/isaacchunn/SC1015_MiniPrj_Airbnb/blob/main/EDA_Middle25.ipynb)
4. [EDA_Last25.ipnyb](https://github.com/isaacchunn/SC1015_MiniPrj_Airbnb/blob/main/EDA_Last25.ipynb)
5. [Airbnb_EDA_Vizualization.ipnyb](https://github.com/isaacchunn/SC1015_MiniPrj_Airbnb/blob/main/Airbnb_EDA_Visualization.ipynb)
6. [Airbnb_LinearRegression.ipnyb](https://github.com/isaacchunn/SC1015_MiniPrj_Airbnb/blob/main/Airbnb_LinearRegression.ipynb)
## We are using Airbnb Singapore Dataset on 29 December 2022 and the source is located in http://insideairbnb.com/get-the-data/

## Content

1. What is Airbnb? (Introduction)
2. Introduction to Problem Statement and motivation
3. Libraries used
4. Explaining general utility functions that we have created
5. Dataset importing and cleaning of dataset
6. Exploratory Data Analysis
7. Linear Regression (Machine Learning)
8. Conclusion
9. Video Presentation
10. References

## What is Airbnb?

Airbnb, Inc. is an American San Francisco-based company operating an online marketplace for short-term homestays and experiences. The company acts as a broker and charges a commission from each booking. The company was founded in 2008 by Brian Chesky, Nathan Blecharczyk, and Joe Gebbia.

![enter image description here](https://mma.prnewswire.com/media/1121685/Airbnb_Logo.jpg)

## Introduction to Problem Statement and motivation

Problem Statement: Identify the factors that could help maximise profit on Airbnb
Motivation: Help Airbnb host get a better idea on how to maximize profits for their Airbnb listings.
Hypothesis: The number of amenities a listing provides will affect its price, the more the amenities, the higher the listing price and variables related to a listing's review will have positive correlation to listing's price.

## Libraries used:
NumPy: Library for Numeric Computations
Pandas: Data Acquisition and preparation
Matplotlib: Low-level library for Data Visualization
Seaborn: High-level library for Data Visualization
Wordcloud: Create word cloud
Folium: Visualization of data on map
Geopandas: Handle geojson data to generate chloropelth maps
Sklearn: Machine Learning

## Explaining General Utility functions that we have created
countOutliers(df) takes in a pandas dataframe as argument. It then finds the 1st and 3rd quartile in the dataframe. By applying the formula of 1st quartile - 1.5 * interquartile range and 3rd quartile + 1.5* interquartile range, we can deduce which data is a outlier as an outlier would be outside the range of the values we have calculated from the 2 formulas. This way, we can count the number of outliers with a for loop.

removeOutliers(df) uses the same principle as countOutliers to find out which data is an outlier, we then apply pandas loc method to exclude data that are outside the range of non-outlier values.

The purpose of the general utility function is to assist with our data cleaning process.

## Dataset importing and cleaning of Dataset
Our dataset is very large with 75 columns, hence, we first apply the pandas info method to get an overview of the columns that we are dealing with. By analysing the description of the columns, we have first exclude the columns that are obviously not relevant to our problem.
### Initial Visual Data Cleaning
We looked through the columns of our dataset and pick up the obviously redundant columns to drop such as the host identification number. This is shown in detail in the notebooks [EDA_First25](https://github.com/isaacchunn/SC1015_MiniPrj_Airbnb/blob/main/EDA_First25.ipynb), [EDA_Middle23](https://github.com/isaacchunn/SC1015_MiniPrj_Airbnb/blob/main/EDA_Middle23.ipynb) and [EDA_last25](https://github.com/isaacchunn/SC1015_MiniPrj_Airbnb/blob/main/EDA_Last25.ipynb).

The general utility functions we have made will assist in removing outliers in our data.

We will also be dropping Null values when nulls values do not mean anything in the column or that the number of null values are too small for the column. An example would be dropping null rows for host_location as an Airbnb listing should have a string that contains the location name that corresponds with it.

## Exploratory Data Analysis
We will look into univariate and bivariate EDAs concerning the interesting or important variables that we have identified.

We will be looking at the variables that are left after dropping the columns from our visual analysis.

This is divided into [EDA_First25](https://github.com/isaacchunn/SC1015_MiniPrj_Airbnb/blob/main/EDA_First25.ipynb), [EDA_Middle23](https://github.com/isaacchunn/SC1015_MiniPrj_Airbnb/blob/main/EDA_Middle23.ipynb) and [EDA_Last25](https://github.com/isaacchunn/SC1015_MiniPrj_Airbnb/blob/main/EDA_Last25.ipynb). We conducted EDA on the remaining columns to confirm which columns are interesting or useful for our prediction.

### Initial EDA findings
We analysed the columns of our dataset to find out if the columns provide any meaningful insight for our project and also find out which columns would be useful for more in-depth analysis.
#### EDA_First25
host_location, host_location, host_is_superhost, host_verifications, host_response_rate have a very skewed data with 90% of the rows having the same output for each column respectively. Hence, we will drop these columns.
#### EDA_Middle25
The variable beds which describes the number of beds available is unbalanced as a huge majority of listings only has 1 bed available. Therefore, we will drop the beds column.
minimum_nights and maximum_nights will be used in our calculation of minimum and maximum profit a host can earn, but will not be directly used for prediction as a predictor.
#### EDA_Last25
The variables that are review related are skewed on the high end and is imbalanced, hence they shall be dropped.
We believe that license should be dropped as it is not necessary to have an Airbnb listing. 
A majority of host chose not to enable instant booking, which results in high False outputs for the column instant_bookable.
In conclusion, we can assume that with a higher reviews rating or score, it can help attract more guests and ultimately maximise our profit as an Airbnb host. However, it should be noted that there are many other factors that can influence booking rates and profitability.
### Uni-Variate EDA
For the remaining EDA, kindly refer to [Airbnb_Visualization](https://github.com/isaacchunn/SC1015_MiniPrj_Airbnb/blob/main/Airbnb_EDA_Visualization.ipynb) for detailed code and explanation. We included the overview of what we have observed from interesting/useful columns.
#### 1. host_response_time
This describes the average response time of the host to message![enter image description here](https://lh3.googleusercontent.com/pw/AJFCJaUg9xl0YdOagfTAAMfgAGUvo4d_8PbQC9ahFK0TzZ1Nl1iF96vAzgGNCSNuBm8EXvzMl2T-Qz9UHsXC7pVoKfyzIfXlIQUWty-WVzAyulwtBbVuZMpVQACg5Hkks2GPAtuTb2v-EFYawS2cvEYPjX809iaFPwRZGiGuFLZ-l5TgihIP9hub_QpQyMiVDrOYF4rHymkL0iPbaf-8JkDN1sR6kMkyzYW8tcvEGbK_VAJSDz-QyJCJYRt8PPRs1oD6X08ttKa5JXQGpexWfMggJR-IC0nsmdSKa7-iJV9F8f4vG90ssaTM_26HFgjBzO8WT8YCHtjJKwegVho9w-hiWThqB0jkx1tqQsIz9Rgvc_JITMg5DAVcjDxel7DPsWm4AltJ_1eO--5DdimX_2SLtuiB8AFxY85GG-fiDKQbh13KjDzwo2viMtCAy0pr9ZShEDgyKz7w4szryKTEbjjnU4lpW6Hkm0z-f6loo-RkZ08tZ4TRlZHCpPFPt6w-LwmOpMoarcuC86utMuqNclp0Hl13Sw9ywAtxmZl2TxBjxqiXB4fcadKjdc8Imie-jpzsl0DQWfExa3s3qF8hzCuV5C0iUmchraR_JkGXtiLBmD4J5-QynEVJD3l9A_qN2GDQE2RF04HeOsS2FjihqOi6DcV3njichkBn14-07Jytuq8-7RatZfGQxdOvo0U-2H7GC4vmZHnotFOFT-ZRhL9dxMK7Cc2lb3iPZgfPruaJWjjtwM6qPM66JQTwWU5Z8BdZiJr_tJ1lDOIT17GucRN9g2KkYBtFu0j3MXc6ZAgXStNOGOI1XA0D5UuxtcMVD-2jtOOL6mwAuQoV2xnpdUEaJxuwgVoGl1j2ZHJMTP-Co3Qg0f62Dl85n8nc_rRQdkYOwu9BdfEyI-HRIGaOemPQLYB1CZ2_HxH4a58exYUV7OrP2VqqQlGg0lmKyqzr-X35utc0gWTkzaZET8PMK6Vq_02I_mFAV4KQwOwltYf0u-h0T7NVbMZ29W85VhE_AkwnIue33ZY=w1050-h685-s-no?authuser=1)
We can observe that majority of the hosts has a response time of within an hour, with 855 hosts replying within an hour, about 21.95% of hosts reply within a day.

#### 2. neighbourhood_cleansed
The neighbourhood group as geocoded using the latitude and longitude against neighbourhoods as defined by open or public digital shapefiles.
![enter image description here](https://lh3.googleusercontent.com/pw/AJFCJaUD2unlbsjy4Pn26LH_zWIXK9xQxy0T6uq5ZyIiwTmbvJ7erQD7k_ThW6N7I-3vCIz5zC62_j1_kv-Ed7_GCqsV_uSPQEWv-sEH24E6_Gjs8YqaJz_RCGNoQGeEbiYp3rdeBkOI7veyfKknzbSOakXhjxdvcX4el078RKYdXl0MQ_2raH9cSgvGBGJODw8v6-xoQ8Oo15FkfIpSGtc4Y9pKJKnoqtaoVlibyV8aa6x7dIbB-a4PTmmCvSpXwsqrYJqtM_u9024LKEPu_t5opIVMK19Uias9e4jN_O3hraliFrtoKAPa4hqKT3p8tuR4BEAoeoRdMb3MCsWqVHmsTvqdz6QXyLVslcBsbWS1HO_cyKUwmNqqrnpcLUaLci3svAhzKPXxAPzSk99xhfiC2bRNzQolMlrULZm7WffO3Bl04FAnDheEMu-NChQhacapwPCHFTaTkuWcHavt5kP505rPXw58OcOfVv9nw-ufBTsAhn_YAc3oDxxil15ihn19oVyfCf0ASY_rNu6bNuJAnux5GbIPsbTEpT49Rh0uWtC_ONz7sZJ_EV59EQOrOWv4UVhjr71rZKwyBrvvNBrFd8lHc8XnUmkcgZ2xivKChQwoK3zCE9OUWxq9-82S6p_oIQYIrb_tjvAeFWN-n7rTKzCWdO2zIdlKn7uVZ9O6xGfoUtgzI5YqOEYDs4wSKNsldwdo7OaQr3vrsv9SKd5wDthulny_VzAJ3kEkXJUA2BRjAgQkBGDG0C9txds_MgHYbRPLvtsr-PQhw-rw2mgw0Kgu85UqxBzts2immzwvNxpaiGYvKLFaF9J0kezJluA50dszGWCv7t0i0ddtfdw74h1GX1UZ_1FIsRt_H88TFvLKPhzrt-HGkGH3hvJUbA2HaE2ZAJQj4KNW48-MXcK1_zM3hfDWozqKtGfz26SHK_i2vnHnlHybz5nByAcpB-_4W7njMvPsu0Q2PVm1EYlFsDoU6YOF9oGwfhAnUSnLIKaNwzMZob1Rz2qxb88j_HAsveQB6yg=w1110-h532-s-no?authuser=1)
We can see that Downtown Core has the highest amount of listings.
![enter image description here](https://lh3.googleusercontent.com/pw/AJFCJaWoIi7WvEDjzSgTNJIMh9yPTwxrtomepPM206nj2zz_I-oFx2eoDlkKYYs6idm-OAL37ecgxsAsoFjOd4A_Y3WHlfYV759gjykokBWx2Y6w8iWVF1tyxJ_AzJLYR94j9kuMXljAUUerMkLCypmiK3pWPZSF1UM97OmMqTKJgzLYUXGXdLBTX7Cjjl3a0SmASxRx7kJ6JsFM9eRglYyFokIydjQs6HdJ7cz8Wl_xNNoeil-4vaAU2clxPlFBDL7L4Me5U4Mo-v12Cn3u4IXo9VQDwW2ZDQWhyHiDOC6GoEElwcxWCP4TJ0O__H8MqOyPNM9sRGrc04QQlyof-d5Py84DpeKWeCtGwO-w6jpk57NPBiI9najw5g5XErih7LqApMC1-udNOmT6ZcUpDYoJ4txQMhGkzEZgecr59oB2bi166mivOcX98UNqxnlqyJYbotfDBIiGYG7z98pwmuR3uRfDCuHAjqcqYzCZ6GWoNq4SNVf7csSupXgyxDhhLP1s_RPiB95pjT49SSM6pv3O5ymPS_43r-ELXKgrMYZYZ9emybiUB2iSLYsubNJ_-5HvwAYckqnpeHHQK51FnXxtRmfbPPQoSvadq0LsUWsPYzoi4EeUN-uiLc_CSk667Z6B-EKk0KRfCMMmS4hbLb2hhhKZxQL0QoBl0Jrxik7r9nHIOkr0F1EGPA8akVN31hKB1itUUqUY73DvVjmpSwvEiY1eKxk8-rNpUJaqY5QLKSZQw5BrUmNYlcohXuQgGoSq2jISbQurL2eD4Qf5yb0oxYpWK9BC_rq4Gd9y5RcgRX77zqcwY1spHJIuIbVxbJOb8-L0yFv0ZlAbiRJdv2tnpBaBU6ea9_cJrhNWc0DjhszkXDdYtwkQwslCXNDLVCnujceRaGWt8mSYegUTcXSZKH5YHWZSMCZLOuQ6aejqRy6gN_W6Sp1j7n63QCMoJ1N-b7wXHTkulFTYQCJ-qOYaDqQ2AE32CTi0oWfbqunGBL50-bUllzLXr4fbMxvtDzMhmZ6GMwU=w624-h349-s-no?authuser=1)

We can see that places like Kallang, Downtown Core and Outram has the highest proportion of houses as compared to the other areas.
#### 3. neighbourhood_group_cleansed
The neighbourhood group as geocoded using the latitude and longitude against neighbourhoods as defined by open or public digital shapefiles.
![enter image description here](https://lh3.googleusercontent.com/pw/AJFCJaXdF1-nwWsMZ--QZZci5ct3hXehxbW1q1WPPQ-2lybZW0V9icICPp07g-VPWpy7qY8cBXLdw_JYlrAGyL561r5Z2CMrqWh_5FkTSJtmZRZMESS5YwXbVpgsvtxBP0I9RxbO_kpOxgEfgW_nsLqicv7XSs6aHS6NutR8ulXUNODGS8zYPgUshVk9aMZtQ0ysLHMUcg0QQqsxnTir9lqVCsJvCeSNrG5RH6PS7AgKl1cVBT8ZBpnnSVtebJSS4BH5suFWYw8q9j9jXs68UJUv9eV-8rLmT1RD5kN2ehZ3Rtq1qud04cwFfR5dHn76J9fnzezIPipmDPacnVkRePgntjVvPLffth9VfQ6mLfRoItjCWyeXDd0oVTZoavs-3VisedwkZxZZeoLAqh1IvN2b2bAYLDoFZ3AQpLYRx2IbOEPCDzE60oQRBZn4gb6_fD2EsLzr-Gi7EtEjgLPwDGdCn6U2DnWloHubZpjuXWOv2l2YdBOlSG_ofiHoUQq9JeBh0SMJbYsO6E5Z2BgbtWKngSLZuA4jhxIvU768imFlZ-jjJjqbMSreRySBFJ_EUkxJXCDJJlm-m4_cihTCGkaT0OhZxYPL7rkRFU2SuBmlTjeDwTYw3JfxG2R_lKe-nGo2YP8lsBIOoeQzkCy9NI0WGmW421uUSthmM4z-MTFejHh1X72ZKYnYv8SeEb2VW7WHI-25OxioFCOIeoT6LwaBirWGCo8I8fgnzuURZbPzGtyMBxbyHlzzjs4HEHAYV_jgWHGwDuRDL_4TO0Tk2aIf0hpjjxRUmPEaqPv5nuJU6q_lWB5xj5uzUasClKsVodpetTJooTxRZK6TTBwfY0-Grb5fKk0_uu8KcFve5mNVjmSL9E5KeePWlmYGjf30Ehirkmmq-hS3nEsQdkgrUVVuDigonUDqziS3ZdWCt734A8SbiYe2oT8yax6gRu2CNSUsfwQezfqQ-aYufoVPfdg6s_DOPq6-1G-MJby3K-s7T-5CsAsTt5vhn04U9vkLSd5nB13a264=w1071-h553-s-no?authuser=1)
We can see that there are many property listings in the central region as compared to the other regions like North-East region or West region. This is probably due to the central region being closer as tourists attractions, so there is a higher amount of listings there. 

#### 4. property_type
Self-selected property type. Hotels and Bed and Breakfasts are described as such by their hosts in this field.
![enter image description here](https://lh3.googleusercontent.com/pw/AJFCJaUDoyrU_knLH6YnrK4Y4JSNIAOBwjDDOGoq3ot6KTV15FmPo1tzPrlNrzqNkAV2jbQbTwz1U-b5W1IDuloRv7QDwN4OZqhSmkZK-ZhG1VIZ6KzAt2X9ED0pw1gYchD-GhIgbKqJJciGDMEPbH2hJ1_CEQ49owb4WWulG4KO2HMg4-xLFjGQfybM43P05mGAcssPBZMgFLRON6blIHK-c1QbNnCZ6wrGCf09R_iWhEdUbAAvBSXajsAPsaIM3_-7m9Pan0C7Qv12PqV0KUWN8UjIZdAu6QxagFqNfO-_togGSYx4ZsVPoUX5oUxXO_cdoiLk_QNYmQV2K4fIH37MowDJUNJLsgwJDSNsXyUk7-UlfywFk9dSzw4yENUfPzxAjmO2tEfChxQBDLy5yW-T7EzCKSforUy2GZYMb38R8QkqdrecAMPnUO9aW5O3FG_MrNSv1DoF1Yztuv_-FB-sG3-4gVD-oWQca3-71JKeC5LelseCGW-1Y6IPxJvi7pJkIv4yBWYAafks9BgCCJLCBxsbkjw0Y9wwBdFODeB7X7D4g1ssYbvk3XNb5qumccz0kTnrh_FnFcJoXNUGOlRIcpfMkxRqoT2ci1T593fR1YPGvSd8oWnOoEy0CAukvywE4YyrbvzMGYEPkr_2JrI2gSjPIA52B2wTOJoiRenqw7syWIC8xzKKRuX4VMOkZ2RbOyltr1WX0FB3xML6ePMCpKm9q6Un7TJ6l7Mc05MrDjIl22JSRvfJKT1ZCTIHo9QwyXOsPWSDH0uX68RHmJ9ZzKECeaWfyTxLkRpAm1_SDPkW742ia830MVcIYKExus2I6wyPeAU_Z1zlFqNql6efWny1Jrwo8bQxRr1vxrDa94CJwtezNZ1y0Bf8XjwaWH5OUT04miTQUEBooyFEPwBNtcb4gwNwdUiBwFpE-SU4yWeEfIzbK-CICU70pQY5gvVRQxzO7OeyUlMGlW0X0tToWwhoRD27QqqUknflsqy0tpbyMw9EADgpL0TBXJ__rGQa9huxVAw=w1120-h709-s-no?authuser=1)
For property type, there are mainly 3 types: Private, Entire and Shared. The rest are either hostels or other niche categories. We shall look into property type according to their categories for classification purposes.
![enter image description here](https://lh3.googleusercontent.com/pw/AJFCJaWLT2kxW1eCDeKmDSlPsC95Jnft7HYIs1OZCJIwL2344zpSUgJI807IjJe1ZuhhdoWuDhG8hbDRIvyUyii0Y7_3uI1r9TmQ-MIdxcrUgbANb2m1U0r3g8glU5HPPTMBM8SUd8_Dp9wWtgfjsFpB9ZiiFfcVrR2YQr6S_Z5ptEm5N8RN5AJvyh97KI_EyLuzq_5_rGoI-Pc2hLzdvxFQ2oN7HTXHQ0sLIbM0FDqSkTEZg4hardGPXGQ2DzAT24O1fFEGLMGYpYabI9i11Uq2_wLlVTHrKh8bjrkyWdXh5Iacj_lmfDK904alKeSguVljQi6y42B7PoIw_GJ2nZYfeQcIn6aHBFnU5xWRriArNIcC0Vg45uBuDmtGGZ1Zl-u1u_qLKhDHJTO-nGUvuV0VrRyQ888fRMml8oNKI1-aVERSvCfuMsOLmFDjRPPaYCCbyx41gXVBTzCP_5Q3TVBV3q4mY-qKeFx9FLYnA_Too8jN29wHh45rDzNLDrUrV7w-CbCnLUCrlpVMXwcYdHdijXGurXsXELie_jKvI7MzJh1N2GFh2uftlSTkDCjg87H60AS60UoYSPEuceGXT-711K51sSKr5p13914tfkpmmGU96Ki4CMvXQQY2bRszWbWUadK5mY-I7TlXgtjJB986PYvTfaOoty8cyB3jWKRvFengbhsSqey41dYqA4Zvhne_44mZK-GZtGafUz6mJ2rXj4uf2REWarH3rlWjRlvOtRjzyfbD8zqYEJ6R0aZQsmBHgbYXoE1OC8M8ROQZrazIYb3p1NYHb6PF_eaWmLxle3Ykrj7MizC5yVKkm_5Ce6eib-ykTUwDgGCM6wRuUVW4KEXQoFxdns3CdipGDuw4glPQQmKy1fKWl8-NKfq9Kzo-HIXPPksOYTJ2RwGrUqKDT3XFjjyo9cMH67-XBKiJC5yq8-IRITFyFrbJXJQ3PSjfSzEuxhMYKgC4UNwmYgVKbXfAL1SNNDZ4ruKLuaLgYQf8x_4hOFcKWsr0A1p-2_hTXIOI09k=w1066-h547-s-no?authuser=1)
This representation makes it easier to analyse property_type, we will observe the impact of this variable with the listings price.

#### 5. accomodates
This is the maximum capacity of the listing.
![enter image description here](https://lh3.googleusercontent.com/pw/AJFCJaVhrrjm0dbziCRVboX7UFMO_sv-MHUn3XOE-Lr3hanqki14Pq0iSjaZq7di0VIDbN9CnT8hr42S5DG04aqn0SzsBIsfvxuAfKDGfZ-ksl94FlBkZ-zwfzok9_TXHTT8-nbAlET19b1TYYtT1i3mpHAXlvQqkX7duzZdAxvAeajJbkbGAhFZZUHM6QRleKJXfdTC6a44UiKe0m4FoM3dnjSzpix1wtJA7qSLemgGiiDyIJYQJBe2FJHJKh7HANYmfgZTDiWyG94zKcvocCvGaYGWoo1Ds83gRwsll2vH4_hHWneoZQSefAjMMzhbC3KQyF6NQ7nVOK5P5JigdH26Ij025aGrH7NowYRhrdvFupCgi4YPqr-UwC77_HBk3ehh1-mCs4v_XmzB2w4z54nGAxdlxt08nirbQ0HWJ85xRyZnrY8RrWBgqneETsL4A_c-uqNMC1zEw83cpAqEYFIhCV19RUMf6_qyJz5FIHDhov5HfisBnu0kuybW0gjzgsxIvojCFlS2SBx1BuBFVouClZjvp2k-QTTMcSC1ZHsFkIpOh-kS62AFtlHbthlZF70nv36BlDbpnn18ccpwz-zgSPrz1OLvebo7yQ8h8JEsUSrONSl79GGxVEbkIpK1siYuk-nb1TjWIevS2cAnGi9I7UkN4-P3VhLimHBaPZChl7p4CQdJLdkXAB9UadHqOr_r77j5UzvDd28cJCNt1LGGxb8HhK2kRtQ2EiWrcmRzj-FRyL4LiE93ZXnnzyuoY_Frzr8-fixaiJmBdIBsXKyCd2YeWUQ0gcGNWwp1B86_IBecyJVDK49fCO7tLOCW5o4noi7HFwO3-d0tFsj_SNVmHcUJXdxhiTrXmxZGYwzjWpyVyfxZQ07UWKnsCSX94r_YVcesjObtJ5j1NZzNV_PZuSCE5M7e555aeNz_9oBUvG15us1_ojlJv7Q-omEJwDj1Gi36qvv6yMwLLX_5wgrN1W6Z_G3CLahrjlX3sAemBilCnMKaRB1SEBESYIc8YMHWqD1ah88=w1066-h537-s-no?authuser=1)
Generally, most listings have around 1-4 accomodates that can stay at a listing at a time.

#### 6.amenities
This describes the amenities present in the Airbnb listing
![enter image description here](https://lh3.googleusercontent.com/pw/AJFCJaWUXb24is_e_uedpDAwkuAKuxlDqHxWg5SoKbiLwEH56tmGhXyohyf6QPeY0I_tpAYKi_bWvUzKx8Hwls6H7d9ZtP7hGGA4FK4AeIwTVqFty-LxMzbwB2wmj_uAcIpQ_oxz2PfNnifPJb-anOwwMZpp58T0EAuEkq5DkGRjItKMQucguSyhmqrjQScrb8U9ad1vYbYB4IpXHOQby-jso6r26zVZ3yzP2fEobofbGkPPSGN4vH5HyY0w7pLZE4ZhOxVt0nCpe3xsr6pINNSsGByyPnhqhttl1l0zuFMXBJGX-uj96Qt_-Ws2BxkHoqocx6Lpjo0vsUFF08bcxpCe_4KKzyBQlZmpEmKi9dcFFOxSlWdDOCm8PG4XrtxlFyEaE66vQGDiiR1K4cG9iHBXyKSQ-1UFUWTFTGYWxrsDuyxISiaJypsfc5bo0M-npLId5XqHY4xR2BecfQgSxrqQndx8vMHRmANfy8Mqo8wHUuz-JbIlbMC2nG-v9G3ud5C81nk2jl4a59k512GjYW1bwsg4IUs0kDHFqhS1PSBieXAhEpf4VbbdnyBV4wjdGOdg5HybVdDWkIbD5CoNTliYRhmahdJ9NOsaAsCmHLeDeWI3nemWLjFFskZicBB_1pyuEiaHJMhZv9G8-lzCnE1fiM_LiwUD6KXtRnF_nSiZut251L0butpVhNz7NhAYB6xqo8LVhrgJEo-siJVCf6rVyTMH0saimn4TgquSAC8t2gs5ga8A67zOam1RwbMivgFc8kh61QuNJaKJvT16XS3dzwPqOKirUj8my9Vd_4As2DNtrTP1mbwYPWT9jzJZhuX99oL6Nz0Ws5r2A_7Y8rnWc8k2V3UggCUtWHND-A8G1mFbdZcl8Yxs-NY4KQcpnUoK29tXHtls5ykCC_h_4t_OHDNcIqoSrThGVkbqxJ7WDhPnf7eZ1S58M4Xx1-XCVOzM3-e2RPSfmwLoVqnBvbo2FfRs-0v58PabzFcMGdpSjDWKv4Pb25WhmnWyIT6MD1cSk4erX_U=w327-h325-no?authuser=1)
Many properties have amenities that allow long term stays, have air conditioning, as well as hot water, hair dryers and smoke alarm. This means that most properties that are on listing have these basic amenities.
![enter image description here](https://lh3.googleusercontent.com/pw/AJFCJaV59L6tOKdA08vyiPLsNZbLudQAhHMYc1q17D1LjZM0tQ5VgEobMw4N1X9HPLTu878VVe5PNGEwcUYaXmISu90-olnWjfnpgDNDxX02wEL7nxZ6oG0sbB7EcmMI0Y2Dv6_9MxunCNYiiPGgynXGN9X3C6PAzLlhKlRG1FBA_k3UN9KX8ZDaBcpLA4GP6AjRD5JV-8zDafFgOjnWUGzWfEV098tQWjKqA0PAF4B7Op3Nr10QGL7sEDD3IFwTEszyRw_7gZemyuCzEYORLIohK-WgGDIdLPIeTsLCMzwAlF9GV6YCGIZJZw52kq5rFarVMDpXX29PbgAQQP2JIBdVSavFqX6QBlbAUd_wBZ3HtEVFrbs7W7Bq9Cj4jnJ98VjmYms-jdBhT9I4YWuUWO7D35Ku6QVVWVwKKQ68Y2Gy1p30EeUxUnDVknO0vOFcc-TeIobb-_G27JLAtbf5Tlj9LKshQseMq6-feUPJKVDiCTX0FsMZJnKK8PBoFsX3ciKjmjVjEMG-1SvowuzciQvHWESbEEANIuJBswYYuFaiDZHb4FC7jROlWDbNAD36TXmypJBznAJCf-58BvuSv5FQE98SIp21Fk1PaJtkgUluJU2QbczvaxJpZM8PDRHuNRqkS8nKDnpgYxJ95-7ui_sZvpUIL9044e6PT2xaFyMyiibueu2ku4DKGYHR-EyOuQD7FHSCi5NYCZm5ZgAjxp8-8DWoUq0Znt2OVHa-ePQQ2LBof8J9xOaiXDqljpxihTTvSXf5Qb6NUD6yXrn7OPRCaJ6xJxjKBOtOBXNAGn-9UOzR5ksNORJewCeyFuwK57hSfkstbSHLJtPSPMRbnlsCRaKLV__3wf9HwncyUyPxR66gu0xyWHXOzinHcww4PxK9x_SQ_KZqWB4t6eLQ2YeN96lX2mdGtnv1379YGjc14DGfHhwCFb9iP5KQV30K1oMEXUSltA6MTdOt5yOqyyq6qznvFutXh01ePiZYRF-2_Xl1zGZ5v0ikGGgvfdP92sEIf-Xmqek=w467-h247-no?authuser=1)
Looking at the number of amenities in a given Airbnb listing, we can see that this column has potential to being one of the predictors, with it being following a decent distribution, we will compare it to price later in our bivariate exploration.
#### 7. number_of_reviews
This describes the total number of reviews for each Airbnb listing
![enter image description here](https://lh3.googleusercontent.com/pw/AJFCJaW5zcF4HZimWiZBgscXjpANFO3ZxtPRV7CPekCDHoF0nieXVb-SGi1zHNvUy9Bdvs_SwnhTwuJBcW9yynRasYZT7b6lWj05JsPZyQNz-2SbnxpmDGR-wWjMRMvS9BpgbZYokcKYaiDsf3WxVLa0AdO8sFGTynQqQxu2KnR_r35KsNmgtcR3v0JIPJXWwzhtfavWmo1F1Hqn51_2mnjT4Q48fUHkPIaMD4Z2B1gqRr0Y1L21CjzjPT907ll5zNpQ0pbSRn5ofHrfCwqm9P79Lq50E69Mz7HoeL5TMKargjmrL6cFDxxWKFskYGdd5suXVjjKtBoVQUNPqZcMx5fWnIj-gWURsN6bIukmZf_a7ws8ekf8htskaVUifC3EZ6ZXL40GjpTt_lR-pDcQpJ3aSSdqgCg492rSGVHfqk1pe7aBJDzKKk6Z0lhPMrOkwab81GgEl4jZElOyAE4eDHB_fVL-8UpYrwv4XPeaehUlXKm44G11pRXQN6tTnKUZ2XUFBUISFfgz8qd8QzfQN6WNh4J6NqDLZ2WJwVdLk_DOpxVisrXCwfUPWIimk1ICTkqvo1gXjIFqeOOZSye95ulyn_jSx37n1V4Lr7ntwslFjUGmB1u_yQOYScJNigk-7yw14en1it0OSxE3L-wQ1IZu71MMNhEFEyjdTb6qEtYPfbf0REnVQuGtEuXGtLnFqjpWP028GP4xVhfXIvU97tfGZXBs1U3uBpp8sWFDtg1ZgeMX24fg7z1DlLSIt1_YLA6mMBoIx-PROVsrWgjm09Bs7dWyaXol3L9nzyhCGBZ4X-1qdZeFzoDKIZquQe_13QbUOuHCu0n5hFaexq1EcMPLBvG89kCbnAkdgNT5dGMWuTUzhrxZNMwe4jYGEzWh3u_AcE9ewfb7zEIjxco1jAM3p0USHsWiG3Nf5OK5FfwNC8IuOHz--cGkWA2MN9uJPTk7yeQ8N1p4gMHpSjqxASGZa-rM7azeZXOQcksepxaqVMRRIC_fe5KKDQjnnex1vn2gxbSmJBY=w1057-h390-s-no?authuser=1)
We can observe that most of the listings have 0 reviews, so we can use this to check if the number of reviews affect the price of a listing in our bivariate exploration.
### Bi-Variate EDA
We will be using price as a response for simplicity.
#### 1. host_response_time vs price

 - Box plot of host_response_time against price
 ![enter image description here](https://lh3.googleusercontent.com/pw/AJFCJaWnUOCcXmdpBs8PA8OyyBA1ag5bB9pngGVqVajKQYz8x7kd5A0nnCkW2yi-H7wyBDNnqowgOqME63kuhMoYY-0wX38zFeuAexR9qsylj0WoxRKoQ1XERY7t7kQhn2YiuGTFjID28K7f-VsaOWgQIFkwK7IcvRZW9o_AJoelapBg55xXW0vIi3TYJDONVJLBDFYL7dTZMFs73gjv69-SCeU3_uPe5K_JIySvBPN-s4G7QVq27pWYS4oLFIIriCSCZBxya8Wp9wzZW99yeFt8CcSuG3MUOXWA3apVqj9YUp5-cBWGXuumdC1x0dBJnBo-93elRwwOBsA38v297gmxB6CRDu12SUiuWiW-JLpwe023ekzU5Ej6nj4KVbMxsO9Q_oRjpwDuVUVdfLNIOSKFE4VHJYdga-xFVOmsENXEVUKDNjiSRkVob2B4QGmmMAo3rVogdItGvKgRzgR8O-1CJ6OJg87JOXTOVTerdsv4PqJo-vtBAGiWae-BHS6K3PiPSTlaYRx7id2xuB5hVz0MBMmxztDad6pcyorgzzd-gSpSCwr7dZKPP05xpFG66atof40Wb9pWAivTlsjylGqScvbIsn71SkPSa-_0XoDvFawK1gJE5UYZeWVHbMxt2Kiuwzhr25kXOkrxIxWrE1dPyylkMZKW8xXZk8ApMsn_9o9lmiQc4Jbn5OBypLrU6M8z9hTjzrj_9dV6EFojr-76_EVm2Eqs5415fDSS8Sjm4h44hPWr5vIJ6_fomyhr_m5y49ri72LR3zeU5wW7-PYDLa0U6czeHNlTuQDMhT_pPl26khEwLYi96izgheSlygtz6Rmrz90uzehRDtuXp5GiQJxxcgGmnsVtEln0_E38RTACUuWyjM7j6FNUpxk2-jChhG28MijlRLG3-fssxUEMFTkdf5fARyr6UKv2JVG-H9jMcdSVqev1-XZCniFtZC-nEtpLhPtygaUkNAwnUjc5r1xaebTQlVL3SI7zLzq4h8KzXGviZjdEuSTzzV-gH0Dh1XgyS-Q=w1075-h550-s-no?authuser=1)
 - There appears to be a positive correlation between response time and the price of the listing, suggesting that hosts who can reply within an hour tend to command higher prices compared to those who take a few days or more to respond.
#### 2. neighbourhood_cleansed vs price
We found that Downtown Core has the highest number of listings at 288. 
![enter image description here](https://lh3.googleusercontent.com/pw/AJFCJaXyIJz_ZUOKLnTw5o9A5CovFWlv14F3OLujuOI_hAs61UT3Qb5IDXD6FOPlp3IdKRm5Yab-YiHaMa5OgBRAhLg1Tt0SCeXe-NSD2aWOOijs5w1h_1wJ4ybwVnInzKr4oQILREGqlawSeqvxRn4cDB4RnzU6AjF05QvjHPAdUn4O9ocKk63fND88i_fYw3BO3yA1p1alA7X6Z8p8dOqPGVT8gTd1C0U9mWF9QFyHorQZBAc_bT_bvJOWN7CkU1DH2CEzz_jHjwoMHgO59CLZ8eRKFYLc5VswjWQdFEHQxFywwu5pyrKbz9mgSS_u1yCAjqaitbYZ-9jOaAEZqAM_KcEwOAzdwDQ702J6mQeY8OJBagk1grxDzcrtQYQ70FpHjJE1D7bz1PsnH6KW5axrMXGoUTU1k8fDC8eajtZnZAQOA0luU_NiwlnYxe5D_H_N1Zn5uO6KYFtanmuEuhhagAk5ZzXDPW3nsFZQfaoO7f_Y4JARPNT1bfju6t3Gn9UIx3MwspDsjUyVf8mZWHaRdN9AZIa52QSecZp32UwqpUA0qWj6xBJcDY7DznnbKx_Q6s3jHxAVpOqvlE9740u16Xam8JBtVM6eQymcqkT4hWwO5oyxoAU7KBG2TxpDd2kTZy-rdss-OrXPN99S18l7jqge-m1-EIgZ_lfhL55VqMpoHSldcnhfk_AwwkYMhPxbhKh8WMxyVlN266K_MGDYyRHqg066jlSNEZGN7REZFfxOkq0VjudismY6jMo_wmeT-vs2MBT0ulDRh_uF-VrPGoVHa3nqV5kFYdkM7eecOphu_49Y8sGuZqtfQzrupd3op-V9brwM2k6tmNG9lqhB25laYQ2dAMOVS6qtYZ8-4X9ou13j-GbvzL_PCbmdvGwFOtonyB-rN-uLaidEhQAPClikLEL3c2hJBrUGKy5F2dwQmhdnPiS5w1tlRpunsJtnjcxKuYiN0fyJxFyHWSojswwDXLGuavK-pUksg_U_K9nSoIy0_PFWpHlPYdgQ4uN7p1Hd3BA=w1280-h618-s-no?authuser=1)
Listings at Southern Islands and Orchard have the highest median in price listings, which is corroborated by the fact that they are touristy areas. In comparison, Ang Mo Kio and Yishun have low Airbnb price listings relatively.
#### 3. neighbour_group_cleansed vs price
![enter image description here](https://lh3.googleusercontent.com/pw/AJFCJaXr4SQWjWLJIpO5e2W9n-R5VBN7F0GTFxvLkWkZBpQLQhAEk_A2wx-1lLYEX-zaY43VvNS3084I9x5kx2StXiOfSOg6Ip1rvGJziJYrzzCU0xqsScGpsfC3LjSHv-7BStIf-uC-CJjqJKAhNUawsoFJoPPAHKULt4cHnzGt_Ldz4RxLtW7_hvjkeRR197RuiY_irW_yBBgtxr8B4CId3HkZasjsgpbFCNz-g3-I00pF-d21v32pzQbRDzQlXpe_PD-yZFKQQdQs5TXwUJ20HIVIDcNr9a7S2lpsE5t54ytXERg4Up5jSGHINtA0ZaMjwgYsdouEeuiExUEklKpjpks3r03f3E1Hx-oLw9TWDQd6WEl5Qk9pHc6udZP10ugVSxzyawGQsM6Tyw2paXdwlwglJfG782ag5v4Vgu51S4kjL4GM58HKYGPzdQT6b5h6lOp3W_qu6e0F0WLOK1Ywx_Dr_BxorZVP3FNnlA417rjNfhSsk_p-G0m5jLM4cT6QqTKBdkY8r2GAv6RGjUmE8YfNejQJ2zbEe9LPT8Y47t_rmzQgUBBOMLJ-oaLv5T9CgbB1_m6Va7qEEaK1iCmopNL7xaqtCjkJgTHGl7_ufAefKgXjPdRqcKNN2YIhYBt8vGB79dv606-EX0SenjmbEU3I_qUYtC7s-pfVaIK6qoUSRmuMmBJpkuaMuz0vqVcKAIVYz0RoLjHJRgL1rRP7Joa0BVE-huhhrDD-m1-PooHOXp1nqRqPjbciIF79tz_ohR5LmOeO3spYnNvGWxr29tsnkRkBkSjXvmzYAanXtRqBaS3OcpSTbFZWvukiTNIeruO33YnHQcBsKiwfLPStvF5NX5qhR0Ir0CJFtItD1hRZS-jIBWT46SKfexT4nga-QZ4siIgsVjaicU9BjfLXBRVu1qQHqbrmjtuPMtJicWV98RzqcLCbwnZMu_rJ3Rgf3jQdrISYBFn3lf9ElhlFUy2TkzZMuzK9vwHC_R5QWynbVrhHepgwxga4boBzHmZ11rh8w2o=w1174-h691-s-no?authuser=1)
 The central and western regions boast high median prices. However, Central has higher median for property listings than the West, which is within expectation. To add on, we noticed that Central region has the most outliers than any other categories, which is also within expectation as not all central listings are tourist spots, it is possible that the outliers are listings in tourist spots such as Orchard.
#### 4. property_type vs price
We observe the categories within property_type and surmised that they could be split mainly into four types of property: Private, entire, shared and hotel/hostels.
![enter image description here](https://lh3.googleusercontent.com/pw/AJFCJaUDEFVRBMF-qbkyO9hE6QfNZBDehHv-4M1EJgBXdnzOla8HdB5lCeq8vKpP_3aN6crUDkvwSSz_4Ko72ej26EZrInYtTtk4hkowzDPWx9ZJIcmburhQ5-ou-24wvO7OtBEWJZb3ZesvQiaF4vwikpFYQgL4WddFH-F-nAswKvHIGmaZVYXHhaC0vUoL0TDegEktdZqHM6KvYi4oD3jPktJk6YFp3ws8WlltQiXWVNQVyYiJvFgggtEJhjGZJeRrWavXHCczC8GR_X4bPmqD3zW7n3Ts1JKj0Jv7DQla3URDPUnwxgt7OHboiz0w0--4ivI7cv2HlrlGv-rXFi2QDRbs4Lzo9q3XqbT5M0cr-ltDhaMp_OMcwSZLxdSKcsiiqIz5jLY3Wmg-HFWUqDe202JA-9zQo6-vGheFmOG6c7jUHChaZMGJ5w88HZ_0r_oI1PImzKhWKRTrr5Xokq2rlZWAyNRtWGgPng56DHAVHgFQJVTcMDrM8Ydov6Rwctoa0KQZr0qsW1g5t5ajkwEdLoGbK5jz4Q7v4SQqUmihGKpFkUtmJ_RdZQ0Lfl5x6Z1ZLPPHG6H4vk1rFqbDcK6vKw_NI798mC5-MvltgzgkrNvROVb3hwulAJvWp3sfaybT9L6eZAx95EyZugOhiBCguTCS9AAKAOVmlSsRyWuOXrcikY_78AX-Y7ejKaPO5JL-TLmAwYJ6tjB1J0tA1ln2u1S814msjugwjfKt18rPRvCj7sdE9jMOvJ1JYzMOZvGGtrSz1n43CXLIekrQ2utXdkiKsmsxYnflPx2KYe-jvqloNomLyv0THnroAFYja38T6UG8ZQZOt8CJq5e8ZBzFBrfJjZTnahC3qojM37rBRYIOIk2dYXcqjbhCx7vd6YKWX-YZ-84V_bxAifNZkTcQFs3HTtL2GRMr_cPo6LDfzXxHnKG6gTUNYxlvROBgYBpybSFExvz11L_YVbwfP_WhdIPh6wlfs_QZRD82QO2hqKGJc9RhN_fJjFCVe6kFXX49Wj4DiXE=w1152-h592-s-no?authuser=1)
We see that entire home apartment listings are generally more expensive than other listings, with the highest median as compared to other types of listings. Hotel/Hostels come in second, which is not surprising as hotels generally range around the high 200s range.
We can also observe that the amount of outliers for private rooms are very high, and this may be because if how the owner chooses to value his/her listing.
#### 5. Accomodates vs Price
![enter image description here](https://lh3.googleusercontent.com/pw/AJFCJaWP8sAbDjHh7k5jhbUIQ-iMcRWZoq6YFvyUD8kkJM6P0tWaC85wNmG1MGbVjMzl5oE9T8drpKbRostDzfB0t84l2YRP6gCOS2znq8SLjUXKu-yi5ioeX3vjewRqWxnP69PFx4xlGAtz579XuVCJxrCcRlFx10kr5mY4TOJJFoe4oOKThy7eFjMhzS38EtjvMDTgcUmEkLRi00DnDbFGW8WXCDlFzWYdRX4jMtK3T5oRHoNNO6_ys5vV7pSm9lJd0W5dlO65LbjPGjilEnZZOnBaufVe9PyBIW3ozhpqkuSSQyK3vz6oKFiHQWZh--CrIDmMO5fm-NzWcCgKltGU0f67hXymdwguGLwMy3g97j4OJpyZY_zmIfDqBfKXz_S6fIEtau6aOvwaLRIkNiifaBCrZZ5xGUEe1GpNo-f-M4EZb3ke-qfAhokQHnK23zQVvp2lW-RNSk0Ow-rGDRmNSD467O0reoKqdArFUcfRHM33JYVM12ePqPeBYP7CYDDfnZXTjC_4R0IcQCCLFwkQlI79K5lbhLQvVNO8nRQ-mymoFLUEBFBemjIbkdY_MB4XJRPxXHsbq2JdVbEZUEJJrQZ2uAwcQly3yEYBiQmRPKTHca2a1ZOsvz68pWBJezyZs5CqMnx_Y6Zd4inC_Qr4P90l7CMRlNHTsozMmzjOFzWKJReZEvruQhqe9uaBwUakcsJDuTU4xumgffclLLntFBPhiEqATkCZcY03o0e2U3b7GUokmFDUjuM7fsIPVyg1wZMtnawK-Vn-Lz4DpSHCD8UuFbJ-8hOmAySmWmVFSKEJgD_UpC92MJYbBVVIndJeqyDhZkJsGcpxS4lAaCV3fRkeQzu-IS5Vv9Iu6GT_eBLL8fXxGy0_gEQJHL4uzNRliM-6S41Pa_9zbHoO77PeEw148k17jyUGS813hHH-V6INFI48-tfhNk-nIFmioZ_Ut7qJgo8dBzWNZCYsEAYL3CLGnMTo_1O2s7cmlrqE5Lhz2UGf8KvVOsK-Qfh6tnbr5F7ZVpQ=w610-h457-s-no?authuser=1)
From the correlation heat map, we found out that accomodates and price have a weak correlation.
#### 7. number_of_reviews vs price
![enter image description here](https://lh3.googleusercontent.com/pw/AJFCJaXPhHfcc4-XAXAj1glHj2GHOtk-RQ3dijpi2kFmRECvBWlSBpg2a-naMlXnBpoGd2EnS4qAxxJXD-UYNxdtVKWCRp17fugmtojHfV_TNnjAl3aw-NK1BrgjKx4mcAo60SkRMkyEWmCCLDEzs_eEG2FMOBcpz2rYT329oph7MKfE6DSLg7hnk7JAarn-yQpCjMPlvJYEsUkiNjyimY5JUKXH7aLZHhSFP0mK2sktyXeXI_rvxbs49wDHsji-gcX5FRa2qMqfHyhG6knXZKREtEtntVrRme2EqFAT9HuTy2bJ0IHj5EaJhFC0mPFojMP_QwTI5mHtk2_Ep4yCtzhryPMIMHQCb4WNZXg-LNZa2Zz2miOC6YjkOMx5raR--F3gGWwUyJoJQZEDtZ5zRQKpCn6p4Joc4dvkqOUVZnUsyVtC4N91K9Swxf2TsT0gwCySZAn4VuipuVfDT_tDj4jyvCxpovI4dobSWIml7m8g1NDnOWMK9z4Rs7rhQ6wJff_IGoH07xK-mORHCW5tLYVxT7rwOMEfeXQX-FPFFQwWKLmNwzTbde_sIeLSmsRKIAts-fK3nWjJ-f9TL3iZZnz3UaMbqA1PDG4gC4gEnvUGMGVqe9JimNiv74HwSIGh7HldB944dfbjLEKWe6mxdYqsk7OaHmGT5E_f3btGJohjjZopTQ3v4ylUj9CQHX7HBTi25Eb_xcq6_C-Mdn8gxRZKx7gIgxNWcKVmQeV30Uv-VAkfo3oWie1jHlf6nOfA4XzyfQGg61qsl7DfsoKc2H80yD8XndE9bcaLx1pfaMU7GqOlvFPT8pIyIWTiMg9jH1N2PZH8a5NaoTpwtTYygotZo_ivWBT_mn0UnQG_XjIndm52mZqnBe3YhO0krX0OX2E26tXchXJ9kFA6kbACHfSXD-OIeq8ZWic8RCwNUeLblUDjoXmg-HTEILu5c8ln2d1jQTBmReTKKSEKkNa0rDg67BBAFN4rGIksFjfB0bm9i_Q4j33LxDcl8Jr3bz65ZjglqKFEGXU=w1191-h624-s-no?authuser=1)
From the correlation heat map, we found out that regardless of the outliers, the correlation between price and number_of_reviews are extremely weak and should not be used for further analysis.
### Insightful data
Here, we would like to cover interesting insights we have regarding a few variables. These variables may not be able to help with our prediction, but they can provide some interesting information regarding our problem.
#### 1. description
This describes the Airbnb listing itself.
Word Cloud of words in the Airbnb listing, the bigger the word, the more frequent the usage of that word is.
![enter image description here](https://lh3.googleusercontent.com/pw/AJFCJaWNlUcMtZjkoT1I9bfk4HY7vopaA6s-JibZe1TfTP0L1bPcU6231xqrQF-GDM0Ra0IbhQbTIEPyTf05ppwBM5X3bWrRzyvShQzXaS5kd4B6H40LbkAbLpc9C52A4vzjPTHkCUO_bGGn62ng_PczMfED0RIGS6TO7PQxriQRFfIB66FGmBGy1LG3O-WX4xnZ-CKOI9SPt4gAW6_NbnRbaAAfsDJnQdS2x_68w-ssOzgl88rfZlz5uYS19DcTWvVrpBg_0Y2qZDUclW-tJClKwCRTHwQKZtPPHaED_eSTMSkWcvn5QSZLUhkhbLhyUghoNcoQIXj_-Dog7Y-dOvMzGxQgsUzGwb3oFDjllL-oVa6wGQwjvMdkUeZTRrIIkRdOA5cDyoTGiwLoy4N3pbv_mBn6X4-P-EASQGbPK6KmQWs5n8r4CULmZXDKjNja29Vb0dEmeZ6xmhyc63xw9JesYaf6OzEDw8A_OdKii4LWx--oJdIZuHe2CY6vWQygh_8qWPaZNyb3gOnZ1XJPRLtVSYttW6E8IjjQVziwN3CmBjV5qau-4bstHoROREZGQYp6JtE0puNmTiIyuLWVIpqaRKCuiPAVx4ePe6nOhPtg1llHu9bssd-oiBNzTk9gl4ElyL3lesIjy_ADcUJDd30gUyLYy9k0ZllaOGwICGE3rCmhShXJw0eVtUl6jWHCGjp7AsLR4h7soM14WTgQWMcNccTf1wLWY60Pldmb-4dRcwdIXN9zak7oRSuBEuvOegcWHg7zODwZY50lar9lJpSEo-HJsCYZjvZZ5WcEW3ltgArmwrwK_-YAZct6RYshNAQvIKXMMxMnE7xrbTIHj1vqTuHkc2zA6Lwaq34Tk4eW2eLvBhnEj3dbAAgLv_lArST-38PVe2_jigVvwSa2EQku7N8qPSWaHZ_0coGfW6O3NPNrDgrH9eGGx2fKHy5aOyoA8seFCRkyW9LQIsr9gN7qRTff3B4OacnX_chjO1kJTQksKSaOp3gm_cNS46b3Fxqo7hCn9G0=w742-h741-s-no?authuser=1)
There is prominent use of words such as "fully furnished", "guest access", "space", "space", "located", "MRT station" and "walking distance", which reveals that there are high amount of listings that mention about walking distances near to MRT stations and also the interior of the house.

#### 2. neighbourhood_overview
This is the brief overview of the neighbourhood where the Airbnb listing is located.
![enter image description here](https://lh3.googleusercontent.com/pw/AJFCJaVZZMOE7pw07zyulZ8SYv2mI6yeOMnTrSKBU7QP9AVd6WDt5fR_7Zlv9ZyfghwXi0hmBBzCHcLtySx6sNI4e7Y5c2rKSj2n5FwueE4rXFhebpVp223t4X783xYCQnTwGU2qJbby2YSGoq47ZtzY0KzcUnAFG_AOUAG8DkKHQ_MdXeqN4T3MBGE0E0kk7WlENGR8YUutMEAv05NKffceoZ_b_-jH5CYjtrHEeR4f_w4GhVsMCwm0BIggVj-9-DNAEE4n7xPmRZmPMsHkvED2oaEfcN3ykoIvytke5YXJXAy2JLVKTQCYFJZS2g6MnjOaGz3KnBBxWbaQmI7uG3OT3KmRjvKXO689by41fSrjGFBXSZQ0QUJCmF_tL9-SkFXFqpOj6iAlmGScXwE7jhl4zlItXEGGD2SioXZV5nW_HunjGBp_yRWbmMazIPPs0II44KXAOCL4KXRBcpQXYPMePj0sWF9uGvyFrheet96dhr6BK10hDBfSLy4ntj-TRxyyXKCbwnn8iL65-bS49hYCJS73b_jmLegSV8iQEvIcHZR9YYvHchA_Uj4B7Ar-VW8iX_UTPePG0U-m5N7o5gi0LKa3S6IB_Bx_HuLO8aFa5EyLZWFhbWQA3CKyN3pu85sMlhsXDaWZcfeBOE3cDD3FjVOrdClleIXIJzeZiiY8_PQpPGz82dqOweTh0wD5lTqLWEJCevacEwQ5VuSLwmFUBHDejkn2K15rrwLEqNge-VSQEPIJ6hcFc1V1RzOlmhJSwDUsOuOHgNdgf_kLvTSBlpFYt8RovTihlWPraQaGTvbPWUnr9RKVt8hOpSwHyib5ZqmQng8WXh5xNRwZnRMcyK8tP_lYVb4djV1vc4HDYXg8SWQKxIuiJ-h1u7OIr1JpkLWOS4vrJ9UE7Ub2jXsa-_-WgIJAc1KI2-O3ezRPzSfZQdNanctvlAbJIbmQi25UR3rGZHpm-FzZxuLnTDU_ehe7y6GWLAjlIN1bGyMr_8YzEuBXg0FO159440U6s8q00JVff0I=w748-h745-s-no?authuser=1)
Words that has high usage include "MRT station", "mins walk", "bus stop", "Raffles Place", "Orchard Road", "Green Line", "Clarke Quay" and "food centre". It can be inferred that a higher proportion of listings are near the central region of Singapore, and are also within walking distance to the MRT station specifically East-West Line. (The Green MRT line)

#### 3. latitude and longitude
The latitude and longitude of the Airbnb listing
From this data, we can map out where each listing is on the Singaporean map.![enter image description here](https://lh3.googleusercontent.com/pw/AJFCJaVIzYKy6-47vF6IO4tIiBywzbMTUqFcC8kgaKT81uJzebPNH-osDy6XGctyLO_XHIfVUKda1Qj2JAwMo4emje9q3PPiCksxnoYNuVcSZj6J6qfnDQc_vF8mWGIPlm8pKagnPS0rcgD-4dJBc174ZZuhO2pEDn6cxC2LamoaWEhDTt7Pigo7Sc_8Klqd1y8EGqEd28yGObrC7iq2gcn8LZiED241pgzgem_h3G-BQTEh3NGo8SUMQh37eqDzAHld1vsHZatQjJzK0owBBz9xkUTeYTd5OonqIcmsT3sgQEpNf_p25qz-0K_vBwQBOyEfrTe5IitaZ7bhrlS1RYd6Rki0ZXRf2zggZro6Ir0cORX7pG3jcCtAsxiXvNRcnm0fSYTltqf7g-wVGHIiG2DGuVm12r3ZsD2o55l3zN_jchlFo-Xf62om8ODnDn7mOpdl4TvJiETz2lu_cshFkDDiVlAUfHo1o_xVHpTM8dL3FTLNqD9r0ViIuDETtUgnVonlqmL3UvvREOeVRsajYQVoVjDp6G20FNfutxGbvY_xAsYmg9ITgBpgWAUHtoBYIc6u2xCYWlR6mr4ZOiaE849raf3fUVrPihM6BGw5NzMTsgsZTLXLdG4d4Al44pkxPo3E50W9c03les2QvGAxxws3HdUcJ-C6minIi0wTszokLlPEkFG3o0TLQ991kX5cQa2J94wgsasdqf40Y4OegMd-9E2pQMxydRErc2Mqj6h9D3UfU22o9y6PT4Z7Xf6TzjUMOUyCgmTpPZEvH1_wtIzQOqOAQfvGRDQOujVs-H9_7Zgik-3wQXZ4MMqsXld8j0oiGG_h4C2ksBfwk_bfmnxlp3ioK6EKIivsl9EH5TR63ykN0gSDXTx4REYrLSN5b8wdniufpq9q9yC_iRuWAeDMeLCoA-w_-otELEHJefyDXmZuFJQ0YlAkt0UugoreyhkQZn95bDQtjZI95kx8EGNxjMbLoBfDusOG2fe__3YCEaaNoPFfwZLNrAXEk-nFomDnVQmvmEs=w1081-h655-s-no?authuser=1)
We can see that a large number of points are concentrated in the central region, as well as Kallang, Downtown Core and Outram.


## Linear Regression
We have chose regression as our Machine Learning model to help with our prediction. The notebook for this part is [Linear_Regression](https://github.com/isaacchunn/SC1015_MiniPrj_Airbnb/blob/main/Airbnb_LinearRegression.ipynb) which will include the code and more detailed information.
We split the dataset into train and test sets of 80:20 ratio for our machine learning model.




## Conclusion



## Video Presentation




# References
### Github repo : 
[https://github.com/isaacchunn/SC1015_MiniPrj_Airbnb/tree/main](https://github.com/isaacchunn/SC1015_MiniPrj_Airbnb/tree/main "https://github.com/isaacchunn/SC1015_MiniPrj_Airbnb/tree/main")  
  
### AIRBNB EDA exploration : 
[https://colab.research.google.com/drive/1Gh1p2MQXTThs134dRyLT6XqGNbGavm9J#scrollTo=tUY3F6v5qM96](https://colab.research.google.com/drive/1Gh1p2MQXTThs134dRyLT6XqGNbGavm9J#scrollTo=tUY3F6v5qM96 "https://colab.research.google.com/drive/1Gh1p2MQXTThs134dRyLT6XqGNbGavm9J#scrollTo=tUY3F6v5qM96")  
  
### Linear Regression : [https://colab.research.google.com/drive/1NJ7EAJzKxcokEkQ0YNJlczDjnhONOXlT#scrollTo=XWRNUW68KD1N](https://colab.research.google.com/drive/1NJ7EAJzKxcokEkQ0YNJlczDjnhONOXlT#scrollTo=XWRNUW68KD1N "https://colab.research.google.com/drive/1NJ7EAJzKxcokEkQ0YNJlczDjnhONOXlT#scrollTo=XWRNUW68KD1N")  
  
  
  
### RESEARCH resources: 
[https://www.kaggle.com/code/subhradeep88/airbnb-analysis-eda/notebook](https://www.kaggle.com/code/subhradeep88/airbnb-analysis-eda/notebook "https://www.kaggle.com/code/subhradeep88/airbnb-analysis-eda/notebook")  
[https://www.kaggle.com/code/ivanovskia1/maximize-value-of-airbnb-rental](https://www.kaggle.com/code/ivanovskia1/maximize-value-of-airbnb-rental "https://www.kaggle.com/code/ivanovskia1/maximize-value-of-airbnb-rental")  
[https://towardsdatascience.com/how-to-maximize-profits-on-airbnb-data-based-approach-for-hosts-beaf08f26941](https://towardsdatascience.com/how-to-maximize-profits-on-airbnb-data-based-approach-for-hosts-beaf08f26941 "https://towardsdatascience.com/how-to-maximize-profits-on-airbnb-data-based-approach-for-hosts-beaf08f26941")

![](blob:https://web.telegram.org/2fefbf5c-0041-422a-a761-b077bad5ac1a)
