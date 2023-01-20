# Connect Notion to Ayshare API

Using this script, you can use post data from a Notion database to make posts to your social networks. 

## Create a Notion database
In Notion, create a database in table view with the following column names and column types:

* **Post** as Title column type (you don’t have a choice here with the column type)
* **Platforms** as Multi Select column type with values: facebook, instagram, twitter, linkedin, reddit, and telegram
* **Images** as Files & Media column type 
* **Profile Keys** as Text column type
* **Status** as Text column type
* **Schedule Date** as Date column type with Date Format Month/Day/Year, Time Format 24 Hours, and include time

These fields will be used in the script specified later in this page. 

See a live Notion example: https://ayrshare-example.notion.site/607c15ce7872456a879adbb0a5f17fdf?v=ee9f65a4afb24033813f245a45bc9e83 
 

### Enter in Test Post Data

We need some sample data to test the post. Here is a suggestion:

* **Post**: Enter - Happy New Year 2023
* **Platforms**: select one or more networks you have linked. Please be sure the name is lowercase.
* **Images**: Attach an image. We like this one you can download and attach: https://img.ayrshare.com/012/gb.jpg
* **Profile Keys**: If you are on the Business Plan and want to post to a client's profile, enter their * Profile Key. Otherwise, leave blank.
* **Status**: Enter - pending. The script only grabs records that are set to pending. Please be sure "pending” is lowercase.
* **Schedule Date**: Leave blank since we'll just test immediate posting right now. Later you can select a future date to schedule the post.

## Create Internal Integration in Notion

Go to the My Integrations page in Notion: https://www.notion.so/my-integrations and click on New Integration. 

You can name the integration ‘Ayrshare’ to identify it easily and choose the appropriate workspace that will have the post data.
 
Finally, the default capabilities that have been selected for you will do. Submit to create the integration. 

If successful, an internal integration token will be available to you. Note this for future steps in this page. 

## Connect the Notion database to the Internal Integration

Open the Notion database that you created earlier. Click on the ellipsis on the top right corner of the page and go to ‘Add Connection’. 

Here you can search for the internal integration you created in the previous step by the name that you chose for it. 

Once you click on the internal integration, you have now connected this Notion database to the  integration. 

## Run script to Make Posts from Notion

You can now run a script in your local environment that will read data from the Notion database and make a post through the Ayrshare API for each row in it with status of ‘pending’. 

Make sure to set the following environment variables used in the script:

* API_KEY: this is API Key you get from Ayrshare
* NOTION_DATABASE_ID: Open the database you created earlier in this page and get the database ID from the URL. It will be in this format: https://www.notion.so/<NOTION_DATABASE_ID>?v=ee9f65a4afb24033813f245a45bc9e83
* NOTION_KEY: internal integration token from earlier

Run the script. You can run it at [Heroku](https://www.heroku.com/), [Digital Ocean](https://www.digitalocean.com/), or [Vercel](https://vercel.com/) for example. If successful, all ‘pending’ status columns will be changed to ‘success’ and the posts will have been made to the appropriate social networks.
