# APPL-Forecasted-Data
*In this data we are taking the data of apple stock and doing the Forcasted analysis on it.*
<div id="header" align="center">
  <img src="https://github.com/tincharlie/APPL-Forecasted-Data/blob/main/ImpFile/giphy.gif" width="30%"/>
</div>
Here we will take past data like and get the output. This output will consider as a input and predict another forecasted value.

For Example:
200, 250, 300 -- 250
250, 300, 250 -- 267
300, 250, 267 -- 272


This is how it works and after completion of that process we will get that approximate forecasted stock price on the daywise.

Lets Assume a use case:
We have 3 burger points in the city.
If we want to predict the sales of each one of the point. So in the A Burger Point need 220 burger, B point need 200 Burger, and c point need 300 burger. So on an average for tomorrow how Burger much they will need in all the Burger Point that we can forecaste on the basis of previous data.

Similarly We will take the day wise data and will do sum and average of it then we will get the forecaste.

  {
   "cell_type": "code",
   "execution_count": 2,
   "id": "d7ce3353",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>High</th>\n",
       "      <th>Low</th>\n",
       "      <th>Open</th>\n",
       "      <th>Close</th>\n",
       "      <th>Volume</th>\n",
       "      <th>Adj Close</th>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>Date</th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>2010-12-31</th>\n",
       "      <td>11.552857</td>\n",
       "      <td>11.475357</td>\n",
       "      <td>11.533929</td>\n",
       "      <td>11.520000</td>\n",
       "      <td>193508000.0</td>\n",
       "      <td>9.836143</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2011-01-03</th>\n",
       "      <td>11.795000</td>\n",
       "      <td>11.601429</td>\n",
       "      <td>11.630000</td>\n",
       "      <td>11.770357</td>\n",
       "      <td>445138400.0</td>\n",
       "      <td>10.049909</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2011-01-04</th>\n",
       "      <td>11.875000</td>\n",
       "      <td>11.719643</td>\n",
       "      <td>11.872857</td>\n",
       "      <td>11.831786</td>\n",
       "      <td>309080800.0</td>\n",
       "      <td>10.102357</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2011-01-05</th>\n",
       "      <td>11.940714</td>\n",
       "      <td>11.767857</td>\n",
       "      <td>11.769643</td>\n",
       "      <td>11.928571</td>\n",
       "      <td>255519600.0</td>\n",
       "      <td>10.184996</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2011-01-06</th>\n",
       "      <td>11.973214</td>\n",
       "      <td>11.889286</td>\n",
       "      <td>11.954286</td>\n",
       "      <td>11.918929</td>\n",
       "      <td>300428800.0</td>\n",
       "      <td>10.176763</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "                 High        Low       Open      Close       Volume  Adj Close\n",
       "Date                                                                          \n",
       "2010-12-31  11.552857  11.475357  11.533929  11.520000  193508000.0   9.836143\n",
       "2011-01-03  11.795000  11.601429  11.630000  11.770357  445138400.0  10.049909\n",
       "2011-01-04  11.875000  11.719643  11.872857  11.831786  309080800.0  10.102357\n",
       "2011-01-05  11.940714  11.767857  11.769643  11.928571  255519600.0  10.184996\n",
       "2011-01-06  11.973214  11.889286  11.954286  11.918929  300428800.0  10.176763"
      ]
     },
     "execution_count": 2,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "start = '2011-01-01'\n",
    "end = '2020-12-31'\n",
    "\n",
    "\n",
    "df = data.DataReader(\"AAPL\", 'yahoo', start, end)\n",
    "df.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 3,
   "id": "a431fa15",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>High</th>\n",
       "      <th>Low</th>\n",
       "      <th>Open</th>\n",
       "      <th>Close</th>\n",
       "      <th>Volume</th>\n",
       "      <th>Adj Close</th>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>Date</th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>2020-12-24</th>\n",
       "      <td>133.460007</td>\n",
       "      <td>131.100006</td>\n",
       "      <td>131.320007</td>\n",
       "      <td>131.970001</td>\n",
       "      <td>54930100.0</td>\n",
       "      <td>130.620911</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2020-12-28</th>\n",
       "      <td>137.339996</td>\n",
       "      <td>133.509995</td>\n",
       "      <td>133.990005</td>\n",
       "      <td>136.690002</td>\n",
       "      <td>124486200.0</td>\n",
       "      <td>135.292648</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2020-12-29</th>\n",
       "      <td>138.789993</td>\n",
       "      <td>134.339996</td>\n",
       "      <td>138.050003</td>\n",
       "      <td>134.869995</td>\n",
       "      <td>121047300.0</td>\n",
       "      <td>133.491241</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2020-12-30</th>\n",
       "      <td>135.990005</td>\n",
       "      <td>133.399994</td>\n",
       "      <td>135.580002</td>\n",
       "      <td>133.720001</td>\n",
       "      <td>96452100.0</td>\n",
       "      <td>132.353012</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2020-12-31</th>\n",
       "      <td>134.740005</td>\n",
       "      <td>131.720001</td>\n",
       "      <td>134.080002</td>\n",
       "      <td>132.690002</td>\n",
       "      <td>99116600.0</td>\n",
       "      <td>131.333527</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "                  High         Low        Open       Close       Volume  \\\n",
       "Date                                                                      \n",
       "2020-12-24  133.460007  131.100006  131.320007  131.970001   54930100.0   \n",
       "2020-12-28  137.339996  133.509995  133.990005  136.690002  124486200.0   \n",
       "2020-12-29  138.789993  134.339996  138.050003  134.869995  121047300.0   \n",
       "2020-12-30  135.990005  133.399994  135.580002  133.720001   96452100.0   \n",
       "2020-12-31  134.740005  131.720001  134.080002  132.690002   99116600.0   \n",
       "\n",
       "             Adj Close  \n",
       "Date                    \n",
       "2020-12-24  130.620911  \n",
       "2020-12-28  135.292648  \n",
       "2020-12-29  133.491241  \n",
       "2020-12-30  132.353012  \n",
       "2020-12-31  131.333527  "
      ]
     },
     "execution_count": 3,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
