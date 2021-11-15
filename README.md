
# TASK
To make an API to fetch latest videos sorted in reverse chronological order of their publishing date-time from YouTube for a given tag/search query in a paginated response.

# Basic Requirements:
- Server should call the YouTube API continuously in background (async) with some interval (say 10 seconds) for fetching the latest videos for a predefined search query and should store the data of videos (specifically these fields - Video title, description, publishing datetime, thumbnails URLs and any other fields you require) in a database with proper indexes.
- A GET API which returns the stored video data in a paginated response sorted in descending order of published datetime.
- A basic search API to search the stored videos using their title and description.

## Instructions for Setup

Clone the repo and install Requirements :

```bash
git clone https://github.com/SrishtiGohain/fetch_youtube
cd path_to_fetch_youtube
pip3 install -r requirements.txt (Install the requirements preferrably in a Virtual environment)
```

Modify settings.py File - Remove the existing keys and add your own YouTube Data API keys in the form [key1, key2, ...]:

```bash
API_KEYS = ['YT_API_Key_1', 'YT_API_Key_2','YT_API_Key_3',] 
```

## Usage

Run the manage.py file:

```python
python3 manage.py runserver
```

To fetch new videos, visit the '/new' endpoint:

```bash
open http://127.0.0.1:8000/new 
to fetch the new videos in paginated and reverse chronological format
```

For watching added videos 

```bash
open http://127.0.0.1:8000
to see all the fetched videos related to cricket query posted in the past 5 minutes.
```

## CRON JOBS Support

Configure the settings.py as per django-cron and 
write a cron class hat extends the CronJobBase class in api_test.py inside api app file and 
call the getnewposts() function inside do(self) function as prescribed by documentation and set RUN_EVERY_MINS = 'Time_Duration'


This will automatically fetch the videos after every given duration time which removes the need for hitting '\new' endpoint:

