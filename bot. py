import logging
from aiogram import Bot, Dispatcher, executor, types
from PIL import Image
import io

API_TOKEN =8109350774:AAGhyFMgdVXD59y7k8x5Hwr6PIhzP1hM9xc 'ضع_توكن_البوت_هنا'

# إعدادات اللوق
logging.basicConfig(level=logging.INFO)

# إنشاء البوت والديسباتشر
bot = Bot(token=API_TOKEN)
dp = Dispatcher(bot)

@dp.message_handler(commands=['start'])
async def send_welcome(message: types.Message):
    await message.reply("مرحبًا! أرسل لي صورة وسأعطيك التوصيات بناءً على التحليل الفني.")

@dp.message_handler(content_types=['photo'])
async def handle_photo(message: types.Message):
    # تحميل الصورة
    photo = message.photo[-1]
    photo_bytes = await photo.download(destination=io.BytesIO())
    photo_bytes.seek(0)

    # فتح الصورة باستخدام PIL
    try:
        img = Image.open(photo_bytes)
        # تحليل بسيط (مثال فقط)
        width, height = img.size
        recommendation = "الصورة تم تحليلها بنجاح ✅\n"
        recommendation += f"الأبعاد: {width} × {height}\n"
        recommendation += "✅ التوصية: الاتجاه العام صاعد (مثال توضيحي)"

        await message.reply(recommendation)

    except Exception as e:
        await message.reply("حدث خطأ أثناء تحليل الصورة.")

if __name__ == '__main__':
    executor.start_polling(dp, skip_updates=True)
