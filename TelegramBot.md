# TelegramBot

## Caracteristicas Principales
- Envvio Automatico de felicitaciones
- Seleccion semanal de Equipo de limpieza
- Recordatorios de Nuevos eventos ("halloween, San Valentin, Inicio de vacaciones, Recordatorio de fecas importante s de la FI, etc)

### Posible implementación de los Cumpleaños
```Python
import telebot
import datetime
import schedule
import time

bot_token = 'TOKEN_DEL_BOT'
group_id = 'ID_DEL_GRUPO'

birthdays = {
    "Rafa": "11-01-2000",
     "Ronin": "06-08-1999",
    "Andres": "18-02-1998",
    "Lis": "15-02-1999",
    "Uriel": "06-08-1999",
    "Ing Sergio": "18-02-1998"
}

bot = telebot.TeleBot(bot_token)

def felicitar_cumple():
    fecha_actual = datetime.datetime.now().strftime('%d-%m')

    for nombre, fecha_nacimiento in birthdays.items():
        if fecha_nacimiento == fecha_actual:
            mensaje = f'¡Feliz cumpleaños, {nombre}!'
            bot.send_message(group_id, mensaje)

# Programar la ejecución de la función a las 8:00 am todos los días
schedule.every().day.at("08:00").do(felicitar_cumple)

while True:
    schedule.run_pending()
    time.sleep(600)  # Esperar 10 minutos (600 segundos)



```
