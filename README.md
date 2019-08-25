# NTSB App for Splunk
A Splunk app to process NTSB Safety Data

# Install app on Splunk Enterprise (standalone)
1. Click the Settings gear icon next to **Apps** on the Launcher homepage.
2. Click **Install app from file**.
3. Navigate to **ntsb_app_for_splunk.tar.gz**.
4. Click **Upload**.
5. Restart Splunk.

# Add the NTSB Data
1. Click **Add Data** on the Launcher homepage.
2. Click **Upload files from my computer**.
3. Click **Select File**.
4. Navigate to the location of the **AviationData.csv** data file. This file will be in **$REPO_HOME\\jupyter_for_all_ntsb\\output\\** directory if you used the data download and cleanse workflow.
5. Click **Next**.
6. For **Source type**, click **Custom**, then select **ntsb_csv**.
7. Click **Next**.
8. For **Index**, click **Create a new index**, set **Index Name** to **ntsb_csv**, set **Max Size of Entire Index** to **50MB**, set **App** to **NTSB App for Splunk**.
9. Click **Save**.
10. Click **Review**.
11. Click **Submit**.

# Access the main Dashboard
1. Select **Apps** | **NTSB App for Splunk**.

# Data Download and Cleanse Workflow
To use this app, the raw data file from NTSB needs to be downloaded and reformatted. There are two Jupyter Notebooks to assist with the data cleanup. The app assumes the cleanup Jupyter Notebook has been run against the base CSV download.
1. [data_set_download.ipynb](https://github.com/csyvenky/jupyter_for_all_ntsb/blob/master/data_set_download.ipynb) - used to download the raw data file from NTSB.
2. [data_set_cleanup.ipynb](https://github.com/csyvenky/jupyter_for_all_ntsb/blob/master/data_set_cleanup.ipynb) - used to process the raw data file, specifically reconfiguring the date format and parsing the Location field into separate City and State fields.
The notebook is available from [Github](https://github.com/csyvenky/jupyter_for_all_ntsb)

# Credit for External Lookup Data
The airport details data has been downloaded from **OurAirports.com**. More information on the project and the Public Domain license can be found [here](http://ourairports.com/data/).

# Build details (for OS X)
1. Clone github repo `git clone https://github.com/csyvenky/ntsb_app_for_splunk`.
2. Make your enhancements and increase the Build and Version numbers in the ./default/app.conf file.
3. Make a tarball of the app folder `tar --exclude='ntsb_app_for_splunk/.git' -czvf ntsb_app_for_splunk.tar.gz ntsb_app_for_splunk/`.
4. Run AppInspect validation via Postman `http://dev.splunk.com/view/appinspect/SP-CAAAFDU`.
5. Test the app installation on clean instance of Splunk.
