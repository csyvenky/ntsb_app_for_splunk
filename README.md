# NTSB App for Splunk
Splunk app to process NTSB Safety Data

*This is a work in progress.*

# Setup on local Splunk Enterprise
1. Create an index on your Splunk instance, I called mine "*ntsb_csv*".
2. Head over to the NTSB and get the  [CSV data](http://app.ntsb.gov/aviationquery/Download.ashx?type=csv).
3. Point your file input monitor at your data folder; select "*ntsb_csv*" as the sourcetype.
4. Install the app.

# Install to Splunk Enterprise
1. Click the Settings gear icon next to Apps.
2. Click Install app from file.

# Full data download workflow
The raw data file can be downloaded and reformated to work with this app. There are two Jupyter Notebooks to assist with the data cleanup. The app assumes the cleanup Jupyter Notebook has been run against the base CSV download. This notebook does some data cleansing, specifically reconfiguring the date formant and parsing the Location field into seperate City and State fields.
1. [data_set_download.ipynb] - used to download the raw data file.
2. [data_set_cleanup.ipynb] - used to clean up the raw data file and export a data file for Splunk.
The notebook is available from [Github here](https://github.com/csyvenky/jupyter_for_all_ntsb)

# Cleaning up the data


# Credit for External Lookup Data
The airport details data has been downloaded from OurAirports.com. More information on the project and the Public Domain licence can be found here: http://ourairports.com/data/

# Build details (for OS X)
1. Clone github repo `git clone https://github.com/csyvenky/ntsb_app_for_splunk`.
2. Make a tarball of the app folder `tar --exclude='ntsb_app_for_splunk/.git' -czvf ntsb_app_for_splunk.tar.gz ntsb_app_for_splunk/`.
3. Run AppInspect validation via Postman `http://dev.splunk.com/view/appinspect/SP-CAAAFDU`.
4. Test installation on clean instance of Splunk.
