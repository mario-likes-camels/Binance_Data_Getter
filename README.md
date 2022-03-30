# Binance_Data_Getter
Used to extract and process data from Binance

# INSTRUCTIONS:

## BASE_FOLDER: This is the folder we wish to save the FINAL data in. And is therefore the filder we set for ALL operations from here on out. 


## STEP1: Download the data you want
This is done using the binance functions. 
NOTE: you may wish to refer to https://github.com/binance/binance-public-data/tree/master/python
To create custom candles you will need to use download-trade.py
Otherwise - when we only use "Unpack_Zips.py" We can use download-kline.py, download-aggTrade.py. BUt we would only end up moving these files - we wouldn't do any of the merging - this will be done in a later update...maybe... :P 
Example Usage: 

        python3 download-trade.py -s LTCBTC -startDate 2020-01-01 -endDate 2020-02-02 -folder '/home/Desktop/Coin_Data'
	

## STEP 2: Move the Zip files into the correct folder - and save as feathers
Example Usage: 

        python3 Unpack_Zips.py --base_folder '/home/Desktop/Coin_Data' --coin 'LTCBTC'



## STEP 3: Create the candles that we want
Example Usage: 

        python3 Create_Candles.py --base_folder '/home/Desktop/Coin_Data' --coin 'LTCBTC' --candle_size 25 --remove_temp_file True --remove_intermediate_files True








