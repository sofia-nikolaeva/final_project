# Final assignment 
##
### Source of data: from spb.real.estate dataset

> rent_df_cleaned = pd.read_csv('cleaned_dataset.csv')

### Stats:

median and mean price for renting apartments:
>rent_median_price = rent_df.last_price.median()
>rent_mean_price = rent_df.last_price.mean()
>print("Rent median price: {}".format(rent_median_price))
>print("Rent mean price: {}".format(rent_mean_price))

### After checking stats, assign outliers 
>outliers = rent_df[(rent_df.price_per_sq_m/rent_df.house_price_sqm_median) > 5]

Clean data from outliers
> sell_df_cleaned_spb = sell_df_cleaned_spb[~((sell_df_cleaned_spb.price_per_sq_m (median_price_per_sq_m_in_spb/2))
                                            & (sell_df_cleaned_spb.house_price_sqm_median/sell_df_cleaned_spb.price_per_sq_m >=2))]


Based on cleaned data set, let's visualise stats:

>fig, axes = plt.subplots(nrows=3,ncols=2, figsize = (25,25))
>for idx, feat in enumerate(categorical):
>    ax = axes[int(idx/2),idx%2]
>    sns.boxplot(x=feat, y='last_price', data=rent_df_cleaned, ax=ax)
>    ax.set_xlabel(feat)
>fig.tight_layout()

Heatmap:
>sns.heatmap(rent_df_cleaned[['area','rooms','renovation','last_price']].corr())

### Model of choice: regressor
Framework: based on the graphs (heatmap, scatter plot), let's pick our variables for prediction: open_plan, rooms, area, renovation

In POSTMAN in order to use prediction model, assign parameters to chosen features
(Using link: http://51.250.20.29:7789/predict_price)

Originally, the ML model code could be found on github (https://github.com/sofia-nikolaeva/final_project/blob/master/app.py)

All the requirements are dtored in the requirements.txt

## Build docker

nikolaeva1@nikolaeva1:~/final_project$ docker build -t st119498/e2e_final:v.0.1 .

> nikolaeva1@nikolaeva1:~$ docker run --network host -d st119498/e2e_final:v.0.1
>>bd70ab9004a85028c9db346735e66856d910edbd78ab4e37f40e35b7c110505f



