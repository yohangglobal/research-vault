# New API for Defillama Data
#dev #Python 

Initial thread
https://twitter.com/coindataschool/status/1575302383810539520?s=20&t=JcLtRMmjaVNr10g6y767GQ

Stablecoin data demo
https://twitter.com/coindataschool/status/1575302394057003009?s=20&t=JcLtRMmjaVNr10g6y767GQ

GLP strats comp dashboard
https://github.com/coindataschool/GLP-strats-comp-dashboard

Python scripts repo for different code
https://github.com/coindataschool/mixture

## Defillama2 Python Client
https://github.com/coindataschool/defillama2

all requirements satisfied after doing pip install defillama2

start up is from defillama2 import DefiLlama once in python terminal

then do import pandas as pd
import numpy as np

This did not work so far, cant get it up and running on vs code, gonna try pycharm instead 

now working a bit better, got the python terminal set up and going thru each command. mainly can see that the "from" command works, getting instances work as well


 obj.get_defi_hist_tvl()

![](Pasted%20image%2020221005232025.png)

well most of it is most likely just plug and play, there isnt really anything that allows for auto pulling data without already knowing contract addresses

okay its a bit lame tbh, too much work and would be better off just using website

now trying out graphs
from defillama2 import DefiLlama
import pandas as pd
import matplotlib.pyplot as plt
from matplotlib.ticker import PercentFormatter, FuncFormatter

pd.set_option('display.max_columns', 15)
pd.set_option('display.max_rows', 50)
pd.options.display.float_format = '{:,.4f}'.format

%matplotlib inline
plt.rcParams['figure.figsize'] = (10, 6)
plt.style.use("fivethirtyeight")

Makes graphs crisp. Only use if you don't have a lot of points/lines on your graph.
%config InlineBackend.figure_formats = ['svg', 'retina'] # use svg, th

readme page looks smooth
and works well

