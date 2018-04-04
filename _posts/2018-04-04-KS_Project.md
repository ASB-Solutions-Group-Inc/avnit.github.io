

```python
# modules we'll use
import pandas as pd
import numpy as np

# read in all our data
ks_data = pd.read_csv("data/ks-data.csv")


ks_data.head(100)
```

    None





<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ID</th>
      <th>name</th>
      <th>category</th>
      <th>main_category</th>
      <th>currency</th>
      <th>deadline</th>
      <th>goal</th>
      <th>launched</th>
      <th>pledged</th>
      <th>state</th>
      <th>backers</th>
      <th>country</th>
      <th>usd pledged</th>
      <th>usd_pledged_real</th>
      <th>usd_goal_real</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1000002330</td>
      <td>The Songs of Adelaide &amp; Abullah</td>
      <td>Poetry</td>
      <td>Publishing</td>
      <td>GBP</td>
      <td>2015-10-09</td>
      <td>1000.0</td>
      <td>2015-08-11 12:12:28</td>
      <td>0.00</td>
      <td>failed</td>
      <td>0</td>
      <td>GB</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>1533.95</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1000003930</td>
      <td>Greeting From Earth: ZGAC Arts Capsule For ET</td>
      <td>Narrative Film</td>
      <td>Film &amp; Video</td>
      <td>USD</td>
      <td>2017-11-01</td>
      <td>30000.0</td>
      <td>2017-09-02 04:43:57</td>
      <td>2421.00</td>
      <td>failed</td>
      <td>15</td>
      <td>US</td>
      <td>100.00</td>
      <td>2421.00</td>
      <td>30000.00</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1000004038</td>
      <td>Where is Hank?</td>
      <td>Narrative Film</td>
      <td>Film &amp; Video</td>
      <td>USD</td>
      <td>2013-02-26</td>
      <td>45000.0</td>
      <td>2013-01-12 00:20:50</td>
      <td>220.00</td>
      <td>failed</td>
      <td>3</td>
      <td>US</td>
      <td>220.00</td>
      <td>220.00</td>
      <td>45000.00</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1000007540</td>
      <td>ToshiCapital Rekordz Needs Help to Complete Album</td>
      <td>Music</td>
      <td>Music</td>
      <td>USD</td>
      <td>2012-04-16</td>
      <td>5000.0</td>
      <td>2012-03-17 03:24:11</td>
      <td>1.00</td>
      <td>failed</td>
      <td>1</td>
      <td>US</td>
      <td>1.00</td>
      <td>1.00</td>
      <td>5000.00</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1000011046</td>
      <td>Community Film Project: The Art of Neighborhoo...</td>
      <td>Film &amp; Video</td>
      <td>Film &amp; Video</td>
      <td>USD</td>
      <td>2015-08-29</td>
      <td>19500.0</td>
      <td>2015-07-04 08:35:03</td>
      <td>1283.00</td>
      <td>canceled</td>
      <td>14</td>
      <td>US</td>
      <td>1283.00</td>
      <td>1283.00</td>
      <td>19500.00</td>
    </tr>
    <tr>
      <th>5</th>
      <td>1000014025</td>
      <td>Monarch Espresso Bar</td>
      <td>Restaurants</td>
      <td>Food</td>
      <td>USD</td>
      <td>2016-04-01</td>
      <td>50000.0</td>
      <td>2016-02-26 13:38:27</td>
      <td>52375.00</td>
      <td>successful</td>
      <td>224</td>
      <td>US</td>
      <td>52375.00</td>
      <td>52375.00</td>
      <td>50000.00</td>
    </tr>
    <tr>
      <th>6</th>
      <td>1000023410</td>
      <td>Support Solar Roasted Coffee &amp; Green Energy!  ...</td>
      <td>Food</td>
      <td>Food</td>
      <td>USD</td>
      <td>2014-12-21</td>
      <td>1000.0</td>
      <td>2014-12-01 18:30:44</td>
      <td>1205.00</td>
      <td>successful</td>
      <td>16</td>
      <td>US</td>
      <td>1205.00</td>
      <td>1205.00</td>
      <td>1000.00</td>
    </tr>
    <tr>
      <th>7</th>
      <td>1000030581</td>
      <td>Chaser Strips. Our Strips make Shots their B*tch!</td>
      <td>Drinks</td>
      <td>Food</td>
      <td>USD</td>
      <td>2016-03-17</td>
      <td>25000.0</td>
      <td>2016-02-01 20:05:12</td>
      <td>453.00</td>
      <td>failed</td>
      <td>40</td>
      <td>US</td>
      <td>453.00</td>
      <td>453.00</td>
      <td>25000.00</td>
    </tr>
    <tr>
      <th>8</th>
      <td>1000034518</td>
      <td>SPIN - Premium Retractable In-Ear Headphones w...</td>
      <td>Product Design</td>
      <td>Design</td>
      <td>USD</td>
      <td>2014-05-29</td>
      <td>125000.0</td>
      <td>2014-04-24 18:14:43</td>
      <td>8233.00</td>
      <td>canceled</td>
      <td>58</td>
      <td>US</td>
      <td>8233.00</td>
      <td>8233.00</td>
      <td>125000.00</td>
    </tr>
    <tr>
      <th>9</th>
      <td>100004195</td>
      <td>STUDIO IN THE SKY - A Documentary Feature Film...</td>
      <td>Documentary</td>
      <td>Film &amp; Video</td>
      <td>USD</td>
      <td>2014-08-10</td>
      <td>65000.0</td>
      <td>2014-07-11 21:55:48</td>
      <td>6240.57</td>
      <td>canceled</td>
      <td>43</td>
      <td>US</td>
      <td>6240.57</td>
      <td>6240.57</td>
      <td>65000.00</td>
    </tr>
    <tr>
      <th>10</th>
      <td>100004721</td>
      <td>Of Jesus and Madmen</td>
      <td>Nonfiction</td>
      <td>Publishing</td>
      <td>CAD</td>
      <td>2013-10-09</td>
      <td>2500.0</td>
      <td>2013-09-09 18:19:37</td>
      <td>0.00</td>
      <td>failed</td>
      <td>0</td>
      <td>CA</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>2406.39</td>
    </tr>
    <tr>
      <th>11</th>
      <td>100005484</td>
      <td>Lisa Lim New CD!</td>
      <td>Indie Rock</td>
      <td>Music</td>
      <td>USD</td>
      <td>2013-04-08</td>
      <td>12500.0</td>
      <td>2013-03-09 06:42:58</td>
      <td>12700.00</td>
      <td>successful</td>
      <td>100</td>
      <td>US</td>
      <td>12700.00</td>
      <td>12700.00</td>
      <td>12500.00</td>
    </tr>
    <tr>
      <th>12</th>
      <td>1000055792</td>
      <td>The Cottage Market</td>
      <td>Crafts</td>
      <td>Crafts</td>
      <td>USD</td>
      <td>2014-10-02</td>
      <td>5000.0</td>
      <td>2014-09-02 17:11:50</td>
      <td>0.00</td>
      <td>failed</td>
      <td>0</td>
      <td>US</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>5000.00</td>
    </tr>
    <tr>
      <th>13</th>
      <td>1000056157</td>
      <td>G-Spot Place for Gamers to connect with eachot...</td>
      <td>Games</td>
      <td>Games</td>
      <td>USD</td>
      <td>2016-03-25</td>
      <td>200000.0</td>
      <td>2016-02-09 23:01:12</td>
      <td>0.00</td>
      <td>failed</td>
      <td>0</td>
      <td>US</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>200000.00</td>
    </tr>
    <tr>
      <th>14</th>
      <td>1000057089</td>
      <td>Tombstone: Old West tabletop game and miniatur...</td>
      <td>Tabletop Games</td>
      <td>Games</td>
      <td>GBP</td>
      <td>2017-05-03</td>
      <td>5000.0</td>
      <td>2017-04-05 19:44:18</td>
      <td>94175.00</td>
      <td>successful</td>
      <td>761</td>
      <td>GB</td>
      <td>57763.78</td>
      <td>121857.33</td>
      <td>6469.73</td>
    </tr>
    <tr>
      <th>15</th>
      <td>1000064368</td>
      <td>Survival Rings</td>
      <td>Design</td>
      <td>Design</td>
      <td>USD</td>
      <td>2015-02-28</td>
      <td>2500.0</td>
      <td>2015-01-29 02:10:53</td>
      <td>664.00</td>
      <td>failed</td>
      <td>11</td>
      <td>US</td>
      <td>664.00</td>
      <td>664.00</td>
      <td>2500.00</td>
    </tr>
    <tr>
      <th>16</th>
      <td>1000064918</td>
      <td>The Beard</td>
      <td>Comic Books</td>
      <td>Comics</td>
      <td>USD</td>
      <td>2014-11-08</td>
      <td>1500.0</td>
      <td>2014-10-09 22:27:52</td>
      <td>395.00</td>
      <td>failed</td>
      <td>16</td>
      <td>US</td>
      <td>395.00</td>
      <td>395.00</td>
      <td>1500.00</td>
    </tr>
    <tr>
      <th>17</th>
      <td>1000068480</td>
      <td>Notes From London: Above &amp; Below</td>
      <td>Art Books</td>
      <td>Publishing</td>
      <td>USD</td>
      <td>2015-05-10</td>
      <td>3000.0</td>
      <td>2015-04-10 21:20:54</td>
      <td>789.00</td>
      <td>failed</td>
      <td>20</td>
      <td>US</td>
      <td>789.00</td>
      <td>789.00</td>
      <td>3000.00</td>
    </tr>
    <tr>
      <th>18</th>
      <td>1000070642</td>
      <td>Mike Corey's Darkness &amp; Light Album</td>
      <td>Music</td>
      <td>Music</td>
      <td>USD</td>
      <td>2012-08-17</td>
      <td>250.0</td>
      <td>2012-08-02 14:11:32</td>
      <td>250.00</td>
      <td>successful</td>
      <td>7</td>
      <td>US</td>
      <td>250.00</td>
      <td>250.00</td>
      <td>250.00</td>
    </tr>
    <tr>
      <th>19</th>
      <td>1000071625</td>
      <td>Boco Tea</td>
      <td>Food</td>
      <td>Food</td>
      <td>USD</td>
      <td>2012-06-02</td>
      <td>5000.0</td>
      <td>2012-05-03 17:24:32</td>
      <td>1781.00</td>
      <td>failed</td>
      <td>40</td>
      <td>US</td>
      <td>1781.00</td>
      <td>1781.00</td>
      <td>5000.00</td>
    </tr>
    <tr>
      <th>20</th>
      <td>1000072011</td>
      <td>CMUK. Shoes: Take on Life Feet First.</td>
      <td>Fashion</td>
      <td>Fashion</td>
      <td>USD</td>
      <td>2013-12-30</td>
      <td>20000.0</td>
      <td>2013-11-25 07:06:11</td>
      <td>34268.00</td>
      <td>successful</td>
      <td>624</td>
      <td>US</td>
      <td>34268.00</td>
      <td>34268.00</td>
      <td>20000.00</td>
    </tr>
    <tr>
      <th>21</th>
      <td>1000081649</td>
      <td>MikeyJ clothing brand fundraiser</td>
      <td>Childrenswear</td>
      <td>Fashion</td>
      <td>AUD</td>
      <td>2017-09-07</td>
      <td>2500.0</td>
      <td>2017-08-08 01:20:20</td>
      <td>1.00</td>
      <td>failed</td>
      <td>1</td>
      <td>AU</td>
      <td>0.00</td>
      <td>0.81</td>
      <td>2026.10</td>
    </tr>
    <tr>
      <th>22</th>
      <td>1000082254</td>
      <td>Alice in Wonderland in G Minor</td>
      <td>Theater</td>
      <td>Theater</td>
      <td>USD</td>
      <td>2014-06-15</td>
      <td>3500.0</td>
      <td>2014-05-16 10:10:38</td>
      <td>650.00</td>
      <td>failed</td>
      <td>12</td>
      <td>US</td>
      <td>650.00</td>
      <td>650.00</td>
      <td>3500.00</td>
    </tr>
    <tr>
      <th>23</th>
      <td>1000087442</td>
      <td>Mountain brew: A quest for alcohol sustainability</td>
      <td>Drinks</td>
      <td>Food</td>
      <td>NOK</td>
      <td>2015-02-25</td>
      <td>500.0</td>
      <td>2015-01-26 19:17:33</td>
      <td>48.00</td>
      <td>failed</td>
      <td>3</td>
      <td>NO</td>
      <td>6.18</td>
      <td>6.29</td>
      <td>65.55</td>
    </tr>
    <tr>
      <th>24</th>
      <td>1000091520</td>
      <td>The Book Zoo - A Mini-Comic</td>
      <td>Comics</td>
      <td>Comics</td>
      <td>USD</td>
      <td>2014-11-12</td>
      <td>175.0</td>
      <td>2014-10-23 17:15:50</td>
      <td>701.66</td>
      <td>successful</td>
      <td>66</td>
      <td>US</td>
      <td>701.66</td>
      <td>701.66</td>
      <td>175.00</td>
    </tr>
    <tr>
      <th>25</th>
      <td>1000102741</td>
      <td>Matt Cavenaugh &amp; Jenny Powers make their 1st a...</td>
      <td>Music</td>
      <td>Music</td>
      <td>USD</td>
      <td>2011-01-06</td>
      <td>10000.0</td>
      <td>2010-12-07 23:16:50</td>
      <td>15827.00</td>
      <td>successful</td>
      <td>147</td>
      <td>US</td>
      <td>15827.00</td>
      <td>15827.00</td>
      <td>10000.00</td>
    </tr>
    <tr>
      <th>26</th>
      <td>1000103948</td>
      <td>Superhero Teddy Bear</td>
      <td>DIY</td>
      <td>Crafts</td>
      <td>GBP</td>
      <td>2016-01-05</td>
      <td>12000.0</td>
      <td>2015-12-06 20:09:06</td>
      <td>0.00</td>
      <td>failed</td>
      <td>0</td>
      <td>GB</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>17489.65</td>
    </tr>
    <tr>
      <th>27</th>
      <td>1000104688</td>
      <td>Permaculture Skills</td>
      <td>Webseries</td>
      <td>Film &amp; Video</td>
      <td>CAD</td>
      <td>2014-12-14</td>
      <td>17757.0</td>
      <td>2014-11-14 18:02:00</td>
      <td>48905.00</td>
      <td>successful</td>
      <td>571</td>
      <td>CA</td>
      <td>43203.25</td>
      <td>42174.03</td>
      <td>15313.04</td>
    </tr>
    <tr>
      <th>28</th>
      <td>1000104953</td>
      <td>Rebel Army Origins: The Heroic Story Of Major ...</td>
      <td>Comics</td>
      <td>Comics</td>
      <td>GBP</td>
      <td>2016-01-28</td>
      <td>100.0</td>
      <td>2015-12-29 16:59:29</td>
      <td>112.38</td>
      <td>successful</td>
      <td>27</td>
      <td>GB</td>
      <td>167.70</td>
      <td>160.60</td>
      <td>142.91</td>
    </tr>
    <tr>
      <th>29</th>
      <td>100011318</td>
      <td>My Moon - Animated Short Film</td>
      <td>Animation</td>
      <td>Film &amp; Video</td>
      <td>USD</td>
      <td>2017-05-03</td>
      <td>50000.0</td>
      <td>2017-04-03 17:11:33</td>
      <td>57577.31</td>
      <td>successful</td>
      <td>840</td>
      <td>US</td>
      <td>10120.00</td>
      <td>57577.31</td>
      <td>50000.00</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>70</th>
      <td>1000260691</td>
      <td>Gizbee™ Unlimited Removable Storage for Your T...</td>
      <td>Gadgets</td>
      <td>Technology</td>
      <td>USD</td>
      <td>2016-03-25</td>
      <td>87000.0</td>
      <td>2016-02-29 20:30:27</td>
      <td>2030.00</td>
      <td>canceled</td>
      <td>15</td>
      <td>US</td>
      <td>2030.00</td>
      <td>2030.00</td>
      <td>87000.00</td>
    </tr>
    <tr>
      <th>71</th>
      <td>1000261018</td>
      <td>Diposta - liberating people from their postal ...</td>
      <td>Web</td>
      <td>Technology</td>
      <td>USD</td>
      <td>2016-08-23</td>
      <td>100000.0</td>
      <td>2016-07-24 13:18:36</td>
      <td>141.00</td>
      <td>failed</td>
      <td>3</td>
      <td>US</td>
      <td>100.00</td>
      <td>141.00</td>
      <td>100000.00</td>
    </tr>
    <tr>
      <th>72</th>
      <td>1000268182</td>
      <td>My Future Just Passed - Debut CD - Jazz Trio</td>
      <td>Jazz</td>
      <td>Music</td>
      <td>USD</td>
      <td>2014-12-03</td>
      <td>4000.0</td>
      <td>2014-11-03 21:11:44</td>
      <td>4795.00</td>
      <td>successful</td>
      <td>95</td>
      <td>US</td>
      <td>4795.00</td>
      <td>4795.00</td>
      <td>4000.00</td>
    </tr>
    <tr>
      <th>73</th>
      <td>1000278154</td>
      <td>Loot and Recruit - A quirky, combative, deck b...</td>
      <td>Tabletop Games</td>
      <td>Games</td>
      <td>USD</td>
      <td>2015-04-10</td>
      <td>13000.0</td>
      <td>2015-03-10 13:19:18</td>
      <td>2453.00</td>
      <td>canceled</td>
      <td>65</td>
      <td>US</td>
      <td>2453.00</td>
      <td>2453.00</td>
      <td>13000.00</td>
    </tr>
    <tr>
      <th>74</th>
      <td>1000282287</td>
      <td>Babe Ruth's Family Kitchen - Gourmet Hot Dogs ...</td>
      <td>Food</td>
      <td>Food</td>
      <td>USD</td>
      <td>2015-10-13</td>
      <td>25000.0</td>
      <td>2015-09-08 00:59:36</td>
      <td>0.00</td>
      <td>canceled</td>
      <td>0</td>
      <td>US</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>25000.00</td>
    </tr>
    <tr>
      <th>75</th>
      <td>1000291122</td>
      <td>VOTE (anyone but) TRUMP Candle</td>
      <td>Product Design</td>
      <td>Design</td>
      <td>GBP</td>
      <td>2016-08-24</td>
      <td>500.0</td>
      <td>2016-07-12 17:31:42</td>
      <td>218.00</td>
      <td>failed</td>
      <td>6</td>
      <td>GB</td>
      <td>174.83</td>
      <td>288.03</td>
      <td>660.62</td>
    </tr>
    <tr>
      <th>76</th>
      <td>1000291263</td>
      <td>"It's Complicated" by Ariana Salome</td>
      <td>Ready-to-wear</td>
      <td>Fashion</td>
      <td>USD</td>
      <td>2016-06-09</td>
      <td>68000.0</td>
      <td>2016-05-10 22:52:00</td>
      <td>0.00</td>
      <td>failed</td>
      <td>0</td>
      <td>US</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>68000.00</td>
    </tr>
    <tr>
      <th>77</th>
      <td>1000294559</td>
      <td>Secular Solstice 2014</td>
      <td>Festivals</td>
      <td>Theater</td>
      <td>USD</td>
      <td>2014-10-27</td>
      <td>7500.0</td>
      <td>2014-10-02 01:50:58</td>
      <td>8157.01</td>
      <td>successful</td>
      <td>164</td>
      <td>US</td>
      <td>8157.01</td>
      <td>8157.01</td>
      <td>7500.00</td>
    </tr>
    <tr>
      <th>78</th>
      <td>1000320473</td>
      <td>Uncommon Rhythm - Season One</td>
      <td>Film &amp; Video</td>
      <td>Film &amp; Video</td>
      <td>USD</td>
      <td>2013-09-13</td>
      <td>29700.0</td>
      <td>2013-08-15 11:16:24</td>
      <td>10410.00</td>
      <td>failed</td>
      <td>76</td>
      <td>US</td>
      <td>10410.00</td>
      <td>10410.00</td>
      <td>29700.00</td>
    </tr>
    <tr>
      <th>79</th>
      <td>1000328150</td>
      <td>Legacy of Svarog | a Unique 3D Action RPG and ...</td>
      <td>Video Games</td>
      <td>Games</td>
      <td>USD</td>
      <td>2015-10-30</td>
      <td>50000.0</td>
      <td>2015-08-31 06:33:31</td>
      <td>1410.00</td>
      <td>failed</td>
      <td>38</td>
      <td>US</td>
      <td>1410.00</td>
      <td>1410.00</td>
      <td>50000.00</td>
    </tr>
    <tr>
      <th>80</th>
      <td>1000328328</td>
      <td>ANVIL Beard</td>
      <td>Fashion</td>
      <td>Fashion</td>
      <td>GBP</td>
      <td>2015-02-06</td>
      <td>2000.0</td>
      <td>2014-12-15 19:13:37</td>
      <td>61.00</td>
      <td>failed</td>
      <td>9</td>
      <td>GB</td>
      <td>95.87</td>
      <td>93.44</td>
      <td>3063.58</td>
    </tr>
    <tr>
      <th>81</th>
      <td>1000331311</td>
      <td>AWE - Antediluvian Wars: Extermination Tactica...</td>
      <td>Tabletop Games</td>
      <td>Games</td>
      <td>USD</td>
      <td>2014-08-31</td>
      <td>13000.0</td>
      <td>2014-08-01 00:02:17</td>
      <td>1811.00</td>
      <td>failed</td>
      <td>34</td>
      <td>US</td>
      <td>1811.00</td>
      <td>1811.00</td>
      <td>13000.00</td>
    </tr>
    <tr>
      <th>82</th>
      <td>1000332383</td>
      <td>Road to the Shire</td>
      <td>Documentary</td>
      <td>Film &amp; Video</td>
      <td>USD</td>
      <td>2012-02-14</td>
      <td>4000.0</td>
      <td>2012-01-11 20:13:55</td>
      <td>4045.00</td>
      <td>successful</td>
      <td>29</td>
      <td>US</td>
      <td>4045.00</td>
      <td>4045.00</td>
      <td>4000.00</td>
    </tr>
    <tr>
      <th>83</th>
      <td>1000333671</td>
      <td>Spiral Electric Skylab Recording</td>
      <td>Rock</td>
      <td>Music</td>
      <td>USD</td>
      <td>2015-02-26</td>
      <td>500.0</td>
      <td>2015-02-04 18:54:23</td>
      <td>1540.00</td>
      <td>successful</td>
      <td>31</td>
      <td>US</td>
      <td>1540.00</td>
      <td>1540.00</td>
      <td>500.00</td>
    </tr>
    <tr>
      <th>84</th>
      <td>1000334074</td>
      <td>The Locals Only Shirt</td>
      <td>Fashion</td>
      <td>Fashion</td>
      <td>USD</td>
      <td>2012-05-18</td>
      <td>500.0</td>
      <td>2012-05-01 07:11:25</td>
      <td>754.82</td>
      <td>successful</td>
      <td>36</td>
      <td>US</td>
      <td>754.82</td>
      <td>754.82</td>
      <td>500.00</td>
    </tr>
    <tr>
      <th>85</th>
      <td>1000335422</td>
      <td>"Where is Home?" Anthology</td>
      <td>Anthologies</td>
      <td>Comics</td>
      <td>CAD</td>
      <td>2014-07-10</td>
      <td>4000.0</td>
      <td>2014-06-10 00:09:47</td>
      <td>4944.50</td>
      <td>successful</td>
      <td>153</td>
      <td>CA</td>
      <td>4523.37</td>
      <td>4646.65</td>
      <td>3759.05</td>
    </tr>
    <tr>
      <th>86</th>
      <td>1000338818</td>
      <td>Diet! No thanks, I'd rather lose weight</td>
      <td>Publishing</td>
      <td>Publishing</td>
      <td>EUR</td>
      <td>2016-10-30</td>
      <td>10000.0</td>
      <td>2016-08-31 18:13:01</td>
      <td>88.00</td>
      <td>failed</td>
      <td>9</td>
      <td>DE</td>
      <td>22.35</td>
      <td>97.62</td>
      <td>11092.99</td>
    </tr>
    <tr>
      <th>87</th>
      <td>1000339877</td>
      <td>The Onrust Project and Two Row Treaty of 1613</td>
      <td>Theater</td>
      <td>Theater</td>
      <td>USD</td>
      <td>2013-06-16</td>
      <td>5000.0</td>
      <td>2013-04-17 00:58:02</td>
      <td>110.00</td>
      <td>failed</td>
      <td>2</td>
      <td>US</td>
      <td>110.00</td>
      <td>110.00</td>
      <td>5000.00</td>
    </tr>
    <tr>
      <th>88</th>
      <td>1000340977</td>
      <td>My Coffee Box</td>
      <td>Drinks</td>
      <td>Food</td>
      <td>USD</td>
      <td>2014-06-16</td>
      <td>3000.0</td>
      <td>2014-05-17 22:43:36</td>
      <td>1027.00</td>
      <td>failed</td>
      <td>18</td>
      <td>US</td>
      <td>1027.00</td>
      <td>1027.00</td>
      <td>3000.00</td>
    </tr>
    <tr>
      <th>89</th>
      <td>1000344383</td>
      <td>¿Tu Sabes? (You Know?) a music collaboration b...</td>
      <td>Music</td>
      <td>Music</td>
      <td>USD</td>
      <td>2012-12-13</td>
      <td>4500.0</td>
      <td>2012-10-30 08:53:03</td>
      <td>409.00</td>
      <td>failed</td>
      <td>10</td>
      <td>US</td>
      <td>409.00</td>
      <td>409.00</td>
      <td>4500.00</td>
    </tr>
    <tr>
      <th>90</th>
      <td>1000348690</td>
      <td>The Silence of Hollowind - Urban Fantasy RPG</td>
      <td>Tabletop Games</td>
      <td>Games</td>
      <td>EUR</td>
      <td>2017-11-23</td>
      <td>5000.0</td>
      <td>2017-10-24 16:58:01</td>
      <td>11238.00</td>
      <td>successful</td>
      <td>346</td>
      <td>IT</td>
      <td>5509.51</td>
      <td>13347.43</td>
      <td>5938.52</td>
    </tr>
    <tr>
      <th>91</th>
      <td>1000348776</td>
      <td>P/O/V Comic and Literary Anthology</td>
      <td>Comics</td>
      <td>Comics</td>
      <td>USD</td>
      <td>2012-03-06</td>
      <td>4289.0</td>
      <td>2012-01-21 18:25:26</td>
      <td>474.00</td>
      <td>failed</td>
      <td>14</td>
      <td>US</td>
      <td>474.00</td>
      <td>474.00</td>
      <td>4289.00</td>
    </tr>
    <tr>
      <th>92</th>
      <td>1000354338</td>
      <td>"Little Shop of Horrors" at the Browncoat Thea...</td>
      <td>Theater</td>
      <td>Theater</td>
      <td>USD</td>
      <td>2012-08-14</td>
      <td>2000.0</td>
      <td>2012-06-30 20:05:26</td>
      <td>2075.00</td>
      <td>successful</td>
      <td>40</td>
      <td>US</td>
      <td>2075.00</td>
      <td>2075.00</td>
      <td>2000.00</td>
    </tr>
    <tr>
      <th>93</th>
      <td>10003650</td>
      <td>Glyscian Debut Album Recording (Canceled)</td>
      <td>Rock</td>
      <td>Music</td>
      <td>USD</td>
      <td>2012-05-26</td>
      <td>15000.0</td>
      <td>2012-03-27 04:25:46</td>
      <td>151.00</td>
      <td>canceled</td>
      <td>4</td>
      <td>US</td>
      <td>151.00</td>
      <td>151.00</td>
      <td>15000.00</td>
    </tr>
    <tr>
      <th>94</th>
      <td>1000374001</td>
      <td>The Dark Waters Project</td>
      <td>Indie Rock</td>
      <td>Music</td>
      <td>USD</td>
      <td>2013-04-07</td>
      <td>10000.0</td>
      <td>2013-02-20 01:48:42</td>
      <td>10414.00</td>
      <td>successful</td>
      <td>113</td>
      <td>US</td>
      <td>10414.00</td>
      <td>10414.00</td>
      <td>10000.00</td>
    </tr>
    <tr>
      <th>95</th>
      <td>1000386601</td>
      <td>Los Angeles International Student Film Festival</td>
      <td>Film &amp; Video</td>
      <td>Film &amp; Video</td>
      <td>USD</td>
      <td>2014-04-03</td>
      <td>1500.0</td>
      <td>2014-03-04 17:24:51</td>
      <td>1932.99</td>
      <td>successful</td>
      <td>29</td>
      <td>US</td>
      <td>1932.99</td>
      <td>1932.99</td>
      <td>1500.00</td>
    </tr>
    <tr>
      <th>96</th>
      <td>1000389241</td>
      <td>Bob Contemplates Ending It All</td>
      <td>Shorts</td>
      <td>Film &amp; Video</td>
      <td>USD</td>
      <td>2014-01-27</td>
      <td>3000.0</td>
      <td>2013-12-18 20:54:02</td>
      <td>3755.00</td>
      <td>successful</td>
      <td>52</td>
      <td>US</td>
      <td>3755.00</td>
      <td>3755.00</td>
      <td>3000.00</td>
    </tr>
    <tr>
      <th>97</th>
      <td>1000392220</td>
      <td>The Girls Bathroom</td>
      <td>Webseries</td>
      <td>Film &amp; Video</td>
      <td>USD</td>
      <td>2011-07-31</td>
      <td>2000.0</td>
      <td>2011-07-06 16:35:45</td>
      <td>2252.99</td>
      <td>successful</td>
      <td>45</td>
      <td>US</td>
      <td>2252.99</td>
      <td>2252.99</td>
      <td>2000.00</td>
    </tr>
    <tr>
      <th>98</th>
      <td>100039820</td>
      <td>Best Spray Bottle Ever - SureShot</td>
      <td>Gadgets</td>
      <td>Technology</td>
      <td>CAD</td>
      <td>2015-03-07</td>
      <td>25000.0</td>
      <td>2015-02-05 16:57:21</td>
      <td>3.00</td>
      <td>failed</td>
      <td>3</td>
      <td>CA</td>
      <td>2.41</td>
      <td>2.36</td>
      <td>19632.48</td>
    </tr>
    <tr>
      <th>99</th>
      <td>1000399155</td>
      <td>New Lasagna</td>
      <td>Restaurants</td>
      <td>Food</td>
      <td>USD</td>
      <td>2014-10-17</td>
      <td>5000.0</td>
      <td>2014-08-18 11:13:15</td>
      <td>0.00</td>
      <td>failed</td>
      <td>0</td>
      <td>US</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>5000.00</td>
    </tr>
  </tbody>
</table>
<p>100 rows × 15 columns</p>
</div>


