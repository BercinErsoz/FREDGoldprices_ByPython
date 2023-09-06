# FREDGoldprices_ByPython
Pyhton Function for getting daily gold prices 


NOTE THAT: This solution no longer works. Because FRED delisted Gold prices in Jan 2022:
https://news.research.stlouisfed.org/2022/01/ice-benchmark-administration-ltd-iba-data-to-be-removed-from-fred/


def get_gold_price(date):
     
                   
    # web link is created according to the API manual of FRED.
    # params has the dictionary for this web link.
    # json is a good way to do this in Python.
    
    data = requests.get("https://api.stlouisfed.org/fred/series/observations",
                        params={
                            "series_id": "GOLDAMGBD228NLBM",
                            "api_key": "33c9d0fd144f3c128cfe8e9a95a34c99",
                            "file_type": "json",
                            "limit": "300",
                            "sort_order": "desc",
                        },
                         verify=False)
    
    # Since I'm only interested in the content of the data object, I'm redefining this content as json.
    data = json.loads(data.content)
    
    # We create a dataframe with the "observations" dictionary in the content.
    df = pd.DataFrame(data["observations"])
