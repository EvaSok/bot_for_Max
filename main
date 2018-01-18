import telebot
from telebot import types
import os
import time
import datetime
from random import shuffle
TOKEN = '467302460:AAG0LYzsBrVWOQfGNmk_iDNCT2Bh3hv66vo' # ïîëó÷åííûé ó @BotFather
bot = telebot.TeleBot(TOKEN)

global number
number = 3

global quiz_number
quiz_number = 10

@bot.message_handler(commands=['start'])
def start(message):
    sent = bot.send_message(message.chat.id, 'Привет! Как тебя зовут?')
    bot.register_next_step_handler(sent, hello)

def hello(message):
    bot.send_message(message.chat.id, 'Привет, {name}! Рада тебя видеть :-)'.format(name=message.text))


@bot.message_handler(commands=['see'])
def see(message):
    for file in os.listdir('C:\\Users\\e.sokolova\\Music\\'):
        if file.split('.')[-1] == 'ogg':
            f = open('C:\\Users\\Eva\\Music\\'+file, 'rb')
            msg = bot.send_voice(message.chat.id, f, None)
            time.sleep(10)
            sent = bot.send_message(message.chat.id, 'Âàø çàïðîñ ïðèíÿò. Æäèòå îòâåòà ;-)')


@bot.message_handler(commands=['super_prise'])
def super_prise(message):
    global number
    if number >= 0:
        sent = bot.send_message(message.chat.id, 'Ýòî òâîÿ âîçìîæíîñòü ïîëó÷èòü Ñóïåð Ïðèç îò Åâû. Îñòàëîñü {number} ïðèçîâ. Õî÷åøü ïðîäîëæèòü? (äà/íåò)'.format(number=number))
        bot.register_next_step_handler(sent, sup_prise_cont)

def sup_prise_cont(message):
    global number
    answer = message.text
    if not ("äà" in answer.lower() or "íåò" in answer.lower()):
        sent = bot.send_message(message.chat.id, 'Âû åùå íå îïðåäåëèëèñü? Ïðèõîäèòå ïîïîçæå ñ ÷åòêèì îòâåòîì :-)')
    elif  ("íåò" in answer.lower()):
        sent = bot.send_message(message.chat.id, 'È ïðàâèëüíî. Ñóïåð Ïðèçû íàäî áåðå÷ü :-)')
    elif ("äà" in answer.lower()):
        sent = bot.send_message(message.chat.id, 'Óâåðåííûé îòâåò, òîãäà ïðîäîëæèì :-)')
        if number == 3:
            sent = bot.send_message(message.chat.id,'Ìàêñèì, òû õî÷åøü ïîëó÷èòü ñâîé ïåðâûé Ñóïåð Ïðèç :-) \nÒåáå íóæíî âûïîëíèòü òðè æåëàíèÿ Åâû:\n1) Ïîäàðèòü Åâå öâåòû\n2) Íîñèòü Åâó íà ðóêàõ\n3) Ïîìî÷ü ïî ðàáîòå\nÊàê âûïîëíèøü âñå - ïîêàæè ýòî ñîîáùåíèå Åâå è îíà âðó÷èò òåáå òâîé ïåðâûé Ñóïåð Ïðèç - ðîìàíòè÷åñêèé âå÷åð :-)')
            number = number - 1
        elif number == 2:
            sent = bot.send_message(message.chat.id,'Ìàêñèì, òû õî÷åøü ïîëó÷èòü ñâîé âòîðîé Ñóïåð Ïðèç :-) \nÒåáå íóæíî âûïîëíèòü òðè æåëàíèÿ Åâû:\n1) Ïîäàðèòü Åâå ïîäàðîê\n2) Âñòðåòèòü ïîñëå ðàáîòû\n3) Ñâàðèòü êàøó Åâå íà çàâòðàê\nÊàê âûïîëíèøü âñå - ïîêàæè ýòî ñîîáùåíèå Åâå è îíà âðó÷èò òåáå òâîé âòîðîé Ñóïåð Ïðèç - íî÷íàÿ ïðîãóëêà ïî Ìîñêâå :-)')
            number = number - 1
        elif number == 1:
            sent = bot.send_message(message.chat.id,'Ìàêñèì, òû õî÷åøü ïîëó÷èòü ñâîé ïîñëåäíèé Ñóïåð Ïðèç :-) \nÑåãîäíÿ ó Åâû ïðåêðàñíîå íàñòðîåíèå è îíà âðó÷èò òåáå Ñóïåð Ïðèç áåç äîïîëíèòåëüíûõ ïðåãðàä ;-)\nÒâîé Ñóïåð Ïðèç .....\n\n\n\nÂûõîäíûå â Íåêðàñîâêå! :-)')
            number = number - 1
        elif number == 0:
            sent = bot.send_message(message.chat.id,'Ìàêñèì, òâîè Ñóïåð Ïðèçû çàêîí÷èëèñü. Òåïåðü òåáå íóæíî ñäåëàòü ÷òî-òî îñîáåííîå è Åâà ïîðàäóåò òåáÿ â îòâåò :-)')



@bot.message_handler(commands=['help'])
def help_message(message):
    sent = bot.send_message(message.chat.id, 'Я бот - сюрприз от Евы для Максима. \nЯ могу пожелать тебе доброе утро и спокойной ночи, когда Ева занята, а тебе не хватает ее внимания. Только напиши мне /good_morning или /good_night. \nЕсли ты хочешь увидеть Еву - набери /see. \nЕсли ты хочешь сыграть в Викторину - отправь мне /quiz. \nИ ты можешь получить 3 Супер Приза от Евы. Можешь начать прямо сейчас - /super_prise.')



@bot.message_handler(commands=['quiz'])
def quiz(message):
    global quiz_number
    sent = bot.send_message(message.chat.id, 'Ýòî âèêòîðèíà. Õî÷åøü íà÷àòü èãðó?')
    bot.register_next_step_handler(sent, quiz_cont)


def quiz_cont(message):
    global quiz_number
    answer = message.text
    if not ("äà" in answer.lower() or "íåò" in answer.lower()):
        sent = bot.send_message(message.chat.id, 'Î÷åíü íåóâåðåííî. Ïîïðîáóåòå åùå ðàç ïîïîçæå :-)')
    elif  ("íåò" in answer.lower()):
        sent = bot.send_message(message.chat.id, 'Áîèøüñÿ, ÷òî íå çíàåøü ïðàâèëüíûõ îòâåòîâ? ;-)')
    elif ("äà" in answer.lower()):
        sent = bot.send_message(message.chat.id, 'Íà÷í¸ì :-)')
        if quiz_number == 10:
            markup = generate_markup(['Âìåñòî Ôëèíñòîóíîâ', 'Îáåñïå÷èâàåò äâèæåíèå àâòîìîáèëÿ', 'Êðóòèò êîëåñà', 'Èíîãäà íå çàâîäèòñÿ'])
            sent = bot.send_message(message.chat.id,'Ïåðâûé âîïðîñ: \nÄâèãàòåëü - òà ÷àñòü ìàøèíû, êîòîðàÿ ...',reply_markup=markup)
            bot.register_next_step_handler(sent, question1)
        elif quiz_number == 9:
            markup = generate_markup(['7.2.1', '5.6.3', '5.9.8', '7.4.3'])
            sent = bot.send_message(message.chat.id, 'Âòîðîé âîïðîñ: \nÏîñëåäíÿÿ âåðñèÿ php:',reply_markup=markup)
            bot.register_next_step_handler(sent, question2)
        elif quiz_number == 8:
            markup = generate_markup(['08.01.1986', '13.08.1992', '25.04.1976', '30.11.1982'])
            sent = bot.send_message(message.chat.id, 'Òðåòèé âîïðîñ: \nÄàòà ïóáëèêàöèè Ìàíèôåñòà õàêåðà:', reply_markup=markup)
            bot.register_next_step_handler(sent, question3)
        elif quiz_number == 7:
            markup = generate_markup(['Accumulo', 'NoDB', 'Sophia', 'Bluemix'])
            sent = bot.send_message(message.chat.id, '×åòâåðòûé âîïðîñ: \nÂûáåðè NoSQL ÁÄ:', reply_markup=markup)
            bot.register_next_step_handler(sent, question4)
        elif quiz_number == 6:
            markup = generate_markup(['Nagios', 'SolarWinds', 'WhatsUp Gold', 'Tivoli', 'Âñå ÿâëÿþòñÿ'])
            sent = bot.send_message(message.chat.id, 'Ïÿòûé âîïðîñ: \nÍå ÿâëÿåòñÿ ñèñòåìîé ìîíèòîðèíãà:', reply_markup=markup)
            bot.register_next_step_handler(sent, question5)
        elif quiz_number == 5:
            markup = generate_markup(['DFM H30 Cross', 'Changan CX70', 'Chery Tiggo 5', 'Lifan X60'])
            sent = bot.send_message(message.chat.id, 'Øåñòîé âîïðîñ: \nÊàê íàçûâàåòñÿ ìàøèíà Åâû:', reply_markup=markup)
            bot.register_next_step_handler(sent, question6)
        elif quiz_number == 4:
            markup = generate_markup(['21', '20', '22', '24'])
            sent = bot.send_message(message.chat.id, 'Ñåäüìîé âîïðîñ: \nÍàäî ëîæèòüñÿ ñïàòü â ...:', reply_markup=markup)
            bot.register_next_step_handler(sent, question7)
        elif quiz_number == 3:
            markup = generate_markup(['$349', '$499', '$299', '$99'])
            sent = bot.send_message(message.chat.id, 'Âîñüìîé âîïðîñ: \nÑêîëüêî ñòîèò ïëàòíàÿ âåðñèÿ BurpSuite:', reply_markup=markup)
            bot.register_next_step_handler(sent, question8)
        elif quiz_number == 2:
            markup = generate_markup(['5', '14', '28', '17'])
            sent = bot.send_message(message.chat.id, 'Äåâÿòûé âîïðîñ: \nÊàêàÿ ãëàâà ÓÊ ÐÔ îïðåäåëÿåò íàêàçàíèÿ çà ïðåñòóïëåíèÿ â ñôåðå êîìïüþòåðíîé èíôîðìàöèè:', reply_markup=markup)
            bot.register_next_step_handler(sent, question9)
        elif quiz_number == 1:
            markup = generate_markup(['Òåïåðü - ÷àé :)', 'Coca-Cola', 'Mountain Dew', 'Iron Brew'])
            sent = bot.send_message(message.chat.id, 'Âòîðîé âîïðîñ: \nÌîé ëþáèìûé íàïèòîê:', reply_markup=markup)
            bot.register_next_step_handler(sent, question10)



def question1(message):
    keyboard_hider = types.ReplyKeyboardRemove()
    global quiz_number
    answer = message.text
    if answer == "Âìåñòî Ôëèíñòîóíîâ":
        sent = bot.send_message(message.chat.id, 'Ïðàâèëüíî!', reply_markup=keyboard_hider)
        quiz_number = quiz_number - 1
        sent = bot.send_sticker(message.chat.id, 'https://s.tcdn.co/fdb/2c3/fdb2c3d5-ae19-3b60-8ffc-7b3b8099cfe5/192/2.png')
    else:
        sent = bot.send_message(message.chat.id, 'Íåïðàâèëüíî.', reply_markup=keyboard_hider)

def question2(message):
    keyboard_hider = types.ReplyKeyboardRemove()
    global quiz_number
    answer = message.text
    if answer == "7.2.1":
        sent = bot.send_message(message.chat.id, 'Ïðàâèëüíî!', reply_markup=keyboard_hider)
        quiz_number = quiz_number - 1
        sent = bot.send_sticker(message.chat.id,'https://s.tcdn.co/5ba/fb7/5bafb75c-6bee-39e0-a4f3-a23e523feded/16.png')
    else:
        sent = bot.send_message(message.chat.id, 'Íåïðàâèëüíî.', reply_markup=keyboard_hider)

def question3(message):
    keyboard_hider = types.ReplyKeyboardRemove()
    global quiz_number
    answer = message.text
    if answer == "08.01.1986":
        sent = bot.send_message(message.chat.id, 'Ïðàâèëüíî! Íî âñå ðàâíî íèêàêèõ îáíèìàøåê :-)', reply_markup=keyboard_hider)
        quiz_number = quiz_number - 1
        sent = bot.send_sticker(message.chat.id,'https://s.tcdn.co/fdb/2c3/fdb2c3d5-ae19-3b60-8ffc-7b3b8099cfe5/18.png')
    else:
        sent = bot.send_message(message.chat.id, 'Íåïðàâèëüíî.', reply_markup=keyboard_hider)

def question4(message):
    keyboard_hider = types.ReplyKeyboardRemove()
    global quiz_number
    answer = message.text
    if answer == "Accumulo":
        sent = bot.send_message(message.chat.id, 'Ïðàâèëüíî! Íî ñíà÷àëà çàðÿäêà, ïîòîì îáíèìó :-)', reply_markup=keyboard_hider)
        quiz_number = quiz_number - 1
    else:
        sent = bot.send_message(message.chat.id, 'Íåïðàâèëüíî.', reply_markup=keyboard_hider)

def question5(message):
    keyboard_hider = types.ReplyKeyboardRemove()
    global quiz_number
    answer = message.text
    if answer == "Âñå ÿâëÿþòñÿ":
        sent = bot.send_message(message.chat.id, 'Ïðàâèëüíî! Îòìåòèì ýòî ÷àåì? ;-)', reply_markup=keyboard_hider)
        quiz_number = quiz_number - 1
    else:
        sent = bot.send_message(message.chat.id, 'Íåïðàâèëüíî.', reply_markup=keyboard_hider)

def question6(message):
    keyboard_hider = types.ReplyKeyboardRemove()
    global quiz_number
    answer = message.text
    if answer == "DFM H30 Cross":
        sent = bot.send_message(message.chat.id, 'Ïðàâèëüíî! Íî òû ãàäàë ñëèøêîì äîëãî... Ïîðà áðàòüñÿ çà äåëî.', reply_markup=keyboard_hider)
        quiz_number = quiz_number - 1
    else:
        sent = bot.send_message(message.chat.id, 'Íåïðàâèëüíî.', reply_markup=keyboard_hider)

def question7(message):
    keyboard_hider = types.ReplyKeyboardRemove()
    global quiz_number
    answer = message.text
    if answer == "21":
        sent = bot.send_message(message.chat.id, 'Ïðàâèëüíî!', reply_markup=keyboard_hider)
        quiz_number = quiz_number - 1
        sent = bot.send_sticker(message.chat.id, 'https://wallbox.ru/wallpapers/main/201546/b09d460a0822a8a.jpg')
    else:
        sent = bot.send_message(message.chat.id, 'Íåïðàâèëüíî.', reply_markup=keyboard_hider)

def question8(message):
    keyboard_hider = types.ReplyKeyboardRemove()
    global quiz_number
    answer = message.text
    if answer == "$349":
        sent = bot.send_message(message.chat.id, 'Ïðàâèëüíî! Óãîâîðèë. Ìû ïîñìîòðèì òîò ôèëüì, êîòîðûé òû õî÷åøü :-)', reply_markup=keyboard_hider)
        quiz_number = quiz_number - 1
    else:
        sent = bot.send_message(message.chat.id, 'Íåïðàâèëüíî.', reply_markup=keyboard_hider)

def question9(message):
    keyboard_hider = types.ReplyKeyboardRemove()
    global quiz_number
    answer = message.text
    if answer == "28":
        sent = bot.send_message(message.chat.id, 'Ïðàâèëüíî! Ëàäíî, ëàäíî - ïîñïèì åùå ÷àñ :-)', reply_markup=keyboard_hider)
        quiz_number = quiz_number - 1
    else:
        sent = bot.send_message(message.chat.id, 'Íåïðàâèëüíî.', reply_markup=keyboard_hider)

def question10(message):
    keyboard_hider = types.ReplyKeyboardRemove()
    global quiz_number
    answer = message.text
    if answer == "Òåïåðü - ÷àé :)":
        sent = bot.send_message(message.chat.id, 'Ïðàâèëüíî! Íà ñåãîäíÿ ÿ îòäàì òåáå ñâîþ ëþáèìóþ ïîäóøêó :-)', reply_markup=keyboard_hider)
    else:
        sent = bot.send_message(message.chat.id, 'Íåïðàâèëüíî.', reply_markup=keyboard_hider)
    sent = bot.send_message(message.chat.id,'Ìàêñèì, ýòî áûë òâîé ïîñëåäíèé âîïðîñ â Âèêòîðèíå. Òû ìîæåøü ïîâòîðèòü èãðó, åñëè õî÷åøü :-)')
    quiz_number = 10



def generate_markup(list_of_answers):
    markup = types.ReplyKeyboardMarkup(one_time_keyboard=True, resize_keyboard=True)
    # Õîðîøåíüêî ïåðåìåøàåì âñå ýëåìåíòû
    shuffle(list_of_answers)
    # Çàïîëíÿåì ðàçìåòêó ïåðåìåøàííûìè ýëåìåíòàìè
    for item in list_of_answers:
        markup.add(item)
    return markup


now = datetime.datetime.now()
hour = now.hour
@bot.message_handler(commands=['good_morning'])
def good_morning(message):
    if 6 <= hour < 12:
        sent = bot.send_message(message.chat.id, 'Äîáðîå óòðî, Ìàêñèì!')
    else:
        sent = bot.send_message(message.chat.id, 'Óæå íå óòðî. Òû îïÿòü âñå ïðîñïàë? ;-)')


@bot.message_handler(commands=['good_night'])
def good_night(message):
    if 18 <= hour < 22:
        sent = bot.send_message(message.chat.id, 'Ñïîêîéíîé íî÷è, Ìàêñèì! Ìîëîäåö, ÷òî ðàíî ëîæèøüñÿ :-)')
    elif 22 <= hour < 24:
        sent = bot.send_message(message.chat.id, 'Ñïîêîéíîé íî÷è, Ìàêñèì!')
    else:
        sent = bot.send_message(message.chat.id, 'Ñïîêîéíîé íî÷è, Ìàêñèì! Íå ïðîñïè áóäèëüíèê ;-)')


bot.polling()
