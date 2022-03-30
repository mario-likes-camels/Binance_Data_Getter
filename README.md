# Binance_Data_Getter
Used to extract and process data from Binance

# INSTRUCTIONS:

## BASE_FOLDER: This is the folder we wish to save the FINAL data in. And is therefore the filder we set for ALL operations from here on out. 


## STEP1: Download the data you want
This is done using the binance functions. 

NOTE: you may wish to refer to https://github.com/binance/binance-public-data/tree/master/python 

To create custom candles you will need to use download-trade.py 

Otherwise - when we only use "Unpack_Zips.py" We can use download-kline.py, download-aggTrade.py. BUt we would only end up moving these files - we wouldn't do any of the merging - this will be done in a later update...maybe... :P 

### Running with arguments
| Argument        | Explanation |         
| --------------- | ---------------- |
| -h              | show help messages| 
| -s              | Single **symbol** or multiple **symbols** separated by space | 
| -y              | Single **year** or multiple **years** separated by space| 
| -m              | Single **month** or multiple **months** separated by space | 
| -d              | single **date** or multiple **dates** separated by space    | 
| -startDate      | **Starting date** to download in [YYYY-MM-DD] format    | 
| -endDate        | **Ending date** to download in [YYYY-MM-DD] format     | 
| -folder         | **Directory** to store the downloaded data    | 
| -c              | 1 to download **checksum file**, default 0       | 
| -i              | single kline **interval** or multiple **intervals** separated by space      |
| -t              | Trading type: **spot**, **um** (USD-M Futures), **cm** (COIN-M Futures)    |

Example Usage: 

        python3 download-trade.py -s LTCBTC -startDate 2020-01-01 -endDate 2020-02-02 -folder '/home/Desktop/Coin_Data'
	

## STEP 2: Move the Zip files into the correct folder - and save as feathers
Used to unzip and then save data in a python readable format. Saved as Feather files to save space.

### Running with arguments
| Argument        | Explanation |         
| --------------- | ---------------- |
| -base_folder    | Where you wish to store all of your data - Note this should be the same as used above| 
| -coin           | Binance trading symbol for desired currency pair |

Example Usage: 

        python3 Unpack_Zips.py --base_folder '/home/Desktop/Coin_Data' --coin 'LTCBTC'



## STEP 3: Create the candles that we want
Used to create the candles. 

### Running with arguments
| Argument                   | Explanation |         
| ---------------            | ---------------- |
| -base_folder               | Where you wish to store all of your data - Note this should be the same as used above| 
| -candle_size               | Size of candle groupings - Must be specified in **minutes** | 
| -remove_temp_file          | Removes any file that were created in the interim processes - Previously created feather files|
| -remove_intermediate_files | Removes any file that were created in the interim processes  - Back-up Candle files|



Example Usage: 

        python3 Create_Candles.py --base_folder '/home/Desktop/Coin_Data' --coin 'LTCBTC' --candle_size 25 --remove_temp_file True --remove_intermediate_files True








