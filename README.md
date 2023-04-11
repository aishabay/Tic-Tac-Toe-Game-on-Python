![alt text](https://media.licdn.com/dms/image/C5616AQEIEO2de4okeQ/profile-displaybackgroundimage-shrink_200_800/0/1658214369734?e=2147483647&v=beta&t=ri-kNm2i5ikJvgLkQ1NSqVEit0gzS1WWtcjknFg-kk0 "Logo Zimran")
# Finnhub News Parser
## What is it?
**Finnhub News Parser** is a Django-based application completed as part of an assignment provided by [Zimran](https://zimran.io/ "Zimran's Homepage") company to assess the candidate applying for a Junior Python developer position. The current version is a revised solution that is better suited for testing in a "production" environment than the initial version, which can be accessed via the [link](https://github.com/aishabay/Stock-News-Tracker.git "First version").
## Built With
* Python
* Django
* Django REST framework
* Celery
* Redis
* PostgreSQL
* Gunicorn
* Docker
## Description of the Assignment
### **TASK: To develop a microservice to parse and store Stock market news on the tickers once an hour to the database.**
* Tickers that should be parsed: **TSLA, META, AMZN, TWTR, NFLX**
* Data must be taken through the API in Finnhub.io. For example, [https://finnhub.io/api/v1/company-news?symbol=NFLX&from=2023-04-06&to=2023-04-07&token=cb36h0aad3i3uh8votcg](https://finnhub.io/api/v1/company-news?symbol=NFLX&from=2023-04-06&to=2023-04-07&token=cb36h0aad3i3uh8votcg "Finnhub")
* Documentation for the desired Finnub endpoint: [https://finnhub.io/docs/api/company-news](https://finnhub.io/docs/api/company-news "Documentation")
* Create an endpoint to retrieve saved news via the REST API on the microservice itself. For example: `https://some.api/news/stock/TSLA`
* Add the logic of filtering by dates. For example: `https://some.api/news/stock/TSLA?date_from=2022-06-01&date_to=2022-06-28`
## Getting Started
#### Before starting to do the following steps make sure that you have Docker Desktop installed on your computer. If not, do it by following the installation instructions [here](https://docs.docker.com/desktop/install/mac-install/ "Docker")
* Open a terminal/Command Prompt on your computer.
* Run this command inside your terminal to reach a desired directory: `cd your-directory`. For example, `cd Desktop`.
* Copy the URL for the repository as shown in the example below: 
![alt text](https://drive.google.com/uc?export=view&id=1qL2W3VYUKULTTr0isZOQwdKd57H4eGZw "Sample for cloning")
* Type `git clone` in the terminal, paste the URL you copied earlier, and then run the command. 
Now you should see that the project from GitHub was cloned into folder "Stock-News-Tracker" in your directory.
* Run this command to move into the folder "Stock-News-Tracker": `cd Stock-News-Tracker/`
* Launch Docker Desktop on your computer
* Run the command `docker-compose up -d --build`
* Run the command `docker-compose exec web python manage.py migrate`
* Paste this URL in your browser: `http://0.0.0.0:8000/news/stock/TSLA/`. If the page opens and you see "News List", then you have followed all the steps correctly. Congratulations!
* When you are done, just run `docker-compose down`. This will stop the server and remove the container. To start the server again, run `docker-compose up`.
### Note:
You may not immediately see data. In other words, data accessed via the API endpoints might return empty lists. It's because the APScheduler is set to run its jobs once an hour. You will see data in 1 hour. Grab your snacks and be patient!
#### Good News:
If you don't want to wait, you can modify the content of the following news_updater.py file that is located inside news_scheduler folder.
For example, you can set minutes to 1 instead of 60. This will run jobs every minute.

![alt text](https://drive.google.com/uc?export=view&id=1-IuWSUfcUMZXRIOoZsKYADj6wEaX4ZxP "Change from 60 to 1")
## Description of API endpoints
#### To check if all the endpoints of this application work correctly you can use either browser or a software such as [Postman](https://www.postman.com/downloads/ "Download Postman") or [Insomnia](https://insomnia.rest/download "Download Insomnia").
* If you choose to use browser, just paste the provided URLs and check
* If you prefer to use an API platform, launch Postman/Insomnia on your laptop. The below-presented example will be used to explain how to use Insomnia for this.

![alt text](https://drive.google.com/uc?export=view&id=1C_majKmO275WJfjGHyDGFn7qzZiz49TJ "Insomnia")
#### Paste the following URLs in the field between "GET" dropdown and "Send" button and click on "Send". You should see data on the right side displayed in JSON format. These are the news for a specific ticker for the last 2 days.
* `http://0.0.0.0:8000/news/stock/TSLA/`
* `http://0.0.0.0:8000/news/stock/META/`
* `http://0.0.0.0:8000/news/stock/AMZN/`
* `http://0.0.0.0:8000/news/stock/TWTR/`
* `http://0.0.0.0:8000/news/stock/NFLX/`
* `http://0.0.0.0:8000/news/stock/META?date_from=2023-04-06&date_to=2023-04-06`
##### As you can see in the last URL, you can also filter news for a specific ticker by changing the date query parameters, i.e. date_from and date_to. Try entering other dates in the format "YYYY-MM-DD".
### I sincerely hope that everything run smoothly. That's it. You are cool if you managed to read all these instructions. Thank you for your time ;)
##### If you encountered any problem, feel free to contact me via Telegram: [https://t.me/f1nal_fantasy](https://t.me/f1nal_fantasy "Aisha Telegram")
