# test
"""
1- qiladigon ishimiz

pip install aiogram

"""
import asyncio
from idlelib.undo import Command
from aiogram import F
from aiogram import Bot, Dispatcher, types
from aiogram.filters import CommandStart
from aiogram.types import Message

API_TOKEN = "7009470576:AAE2VnLyyyh54YDeXQhR-8WPrQXt4NCTNa4"
bot = Bot(token=API_TOKEN)
db = Dispatcher()


@db.message(CommandStart())
async def start_handlr(message: Message):
    await message.answer("Assalomu alaykum hush kelibsiz ✅✅")


@db.message(F.text.lower() == "salom")
async def salomga_alik(message: Message):
    await message.answer("Volekum assalom")


@db.message(F.text.lower() == "Abdilaziz")
async def abdulaziz(m: Message):
    await m.answer("Qalesa")


@db.message()
async def echo_handlar(message: Message):
    await message.answer("Man hali bunday narsani tushinmayman, Faqat Salom ni tushinaman")


@db.message(F.text.lower().in_({"nima gap", "qalesan", "dars bormi bugun"}))
async def javob(m: Message):
    a = {
        "nima gap": "Ishlaring yxhsimi",
        "qalesan":"mann yaxhsi o'zingchi",
        "dars bormi bugun":"ha boladi kech qolmelar"
    }
    text = m.text.lower()
    await m.reply(a.get(text, "😒"))


async def main():
    await db.start_polling(bot)


if __name__ == "__main__":
    asyncio.run(main())
