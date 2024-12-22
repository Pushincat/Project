import telebot
from bot_logic import gen_pass

bot = telebot.TeleBot("7939130627:AAFl8uCMoTuSKOXjYtsz3Z6NUJFs6JUoCUk")

@bot.message_handler(commands=['start'])
def send_welcome(message):
    bot.reply_to(message, "Привет пользователь! Я Pushinbot! Твой Ассистент, напиши что-то для продолжения")

@bot.message_handler(commands=['hello'])
def send_hello(message):
    bot.reply_to(message, "Привет! Чем могу помочь?")

@bot.message_handler(commands=['bye'])
def send_bye(message):
    bot.reply_to(message, "Пока пользователь!")

@bot.message_handler(commands=['password'])
def send_password(message):
    bot.reply_to(message, gen_pass(10))

@bot.message_handler(commands=['heh'])
def send_heh(message):
    count_heh = int(message.text.split()[1]) if len(message.text.split()) > 1 else 5
    bot.reply_to(message, "he" * count_heh)

@bot.message_handler(func=lambda message: True)
def echo_all(message):
    bot.reply_to(message, message.text)

bot.polling()
