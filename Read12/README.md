# class12

## pandas

### object creation

* creating series
<br>
<img src='https://i.stack.imgur.com/prcbg.png'/>

* creating data_range
<br>
 data = pd.date_range("20130101", periods=6)
 <br>
 DatetimeIndex(['2013-01-01', '2013-01-02', '2013-01-03', '2013-01-04',
               '2013-01-05', '2013-01-06'],
              dtype='datetime64[ns]', freq='D')
* creating DataFrame
<br>
<img src='https://miro.medium.com/max/1400/1*vzmPwGDPh5ZeTJdqvWKZ9g.png'/>

<br>
If you’re using IPython, tab completion for column names (as well as public attributes) is automatically enabled. Here’s a subset of the attributes that will be completed

---

#### viewing Data

* head()
* tail()
<img src='https://shanelynnwebsite-mid9n9g1q9y8tt.netdna-ssl.com/wp-content/uploads/2017/12/pandas-dataframe-head-tail.png'/>
<br>
* index
* columns
* to_numpy() :pandas will find the NumPy dtype that can hold all of the dtypes in the DataFram
* descripe():  shows a quick statistic summary of your data:
* T : Transposing your data
* sort_index(axis=1, ascending=False) : Sorting by an axis
* sort_values(by="B") : sorting by value

---

#### Getting

* df["A"] : Selecting a single column, which yields a Series, equivalent to df.A
* df[0:3] : Selecting via [], which slices the rows.
* df.loc[dates[0]] : For getting a cross section using a label
* df.loc[:, ["A", "B"]] : Selecting on a multi-axis by label
* df.loc["20130102":"20130104", ["A", "B"]] : Showing label slicing, both endpoints are included
* df.loc["20130102", ["A", "B"]] : Reduction in the dimensions of the returned objec
* df.loc[dates[0], "A"] : For getting a scalar value:
* df.at[dates[0], "A"] : For getting fast access to a scalar (equivalent to the prior method)

---

#### Selection by position

* df.iloc[3] : Select via the position of the passed integers:
* df.iloc[3:5,0:2] : By integer slices, acting similar to NumPy/Python:
* df.iloc[[1, 2, 4], [0, 2]] : By lists of integer position locations
* df.iloc[1:3, :] : For slicing rows explicitly:
* df.iloc[:, 1:3] : For slicing columns explicitly:
* df.iloc[1, 1] : For getting a value explicitly
* df.iat[1, 1] : For getting fast access to a scalar

---

#### Boolean indexing

* df[df["A"] > 0] : Using a single column’s values to select data.
* df[df > 0] : Selecting values from a DataFrame where a boolean condition is met.
* df2[df2["E"].isin(["two", "four"])] : Using the isin() method for filtering
