# Trade_Guru_bot
Telegram bot for stock updates
import os
import telegram
import schedule
import time
from datetime import datetime

BOT_TOKEN = os.environ.get("BOT_TOKEN")
CHAT_ID = os.environ.get("CHAT_ID")

bot = telegram.Bot(token=BOT_TOKEN)

def send_market_update():
    message = "📈 *Aaj ka Market Update:*\n\nNifty 50: 17750\nBank Nifty: 41500\n\n*Stay tuned for more updates!*"
    bot.send_message(chat_id=CHAT_ID, text=message, parse_mode=telegram.ParseMode.MARKDOWN)

schedule.every().day.at("08:30").do(send_market_update)

while True:
    schedule.run_pending()
    time.sleep(60)
