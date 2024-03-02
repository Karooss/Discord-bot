import discord
import deneme1

# ayricaliklar (intents) değişkeni botun ayrıcalıklarını depolayacak
intents = discord.Intents.default()
# Mesajları okuma ayrıcalığını etkinleştirelim
intents.message_content = True
# client (istemci) değişkeniyle bir bot oluşturalım ve ayrıcalıkları ona aktaralım
client = discord.Client(intents=intents)

@client.event
async def on_ready():
    print(f'{client.user} olarak giriş yaptık.')

@client.event
async def on_message(message):
    if message.author == client.user:
        return
    if message.content.startswith('merhaba'):
        await message.channel.send("Selam!")
    elif message.content.startswith('bye'):
        await message.channel.send("\U0001f642")
    elif message.content.startswith("şifre"):
        await message.channel.send(deneme1.deneme(7))

    else:
        await message.channel.send(message.content)

client.run("MTIxMzQwMTAzNjkyMDg1NjYwNg.GMi6TZ.oj9IReOM93Azgy0tsqH_dIUqoOOOoCTRFiHrbY")
