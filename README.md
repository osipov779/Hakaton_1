# Hakaton_1 Команда №5
#Представляем Вашему вниманию работу по автосурдопереводчику основанному на предобученой модели Slovo.

Slovo — набор данных русского языка жестов. Набор видеоданных «Slovo» для задачи русского жестового языка. Размер набора данных Slovo составляет около 16 ГБ и содержит 20400 RGB-видео для 1000 жестов языка жестов от 194 человек. В каждом классе по 20 образцов. Набор данных разделен на обучающий набор и тестовый набор по темам user_id. Обучающий набор включает 15300 видеороликов, тестовый набор — 5100 видеороликов. Общее время записи видео составляет ~9,2 часа. Около 35% видеороликов записаны в формате HD, а 65% видео — в разрешении FullHD. Средняя продолжительность видео с жестом — 50 кадров.
Для получения дополнительной информации см. https://github.com/hukenovs/slovo

Файл аннотаций прост в использовании и содержит несколько полезных столбцов, см. annotations.csvфайл:

![image](https://github.com/osipov779/Hakaton_1/assets/151464254/663377c6-be86-48f6-86bd-804b69f8eec6)

где:
attachment_id- имя видеофайла
user_id- уникальный анонимизированный идентификатор пользователя
width- ширина видео
height- высота видео
length- длина видео
text- урок жестов на русском языке
train- обучить или проверить логический флаг
begin- начало жеста (для исходного набора данных)
end- конец жеста (для исходного набора данных)
Для удобства подготовлена сжатая версия датасета, в которой все видео обрабатываются с минимальной стороны min_side = 360. Ссылка для скачивания — slovo360p .  Обрезанные видео аннотируются с помощью MediaPipe и указываем ключевые точки руки в этом файле аннотаций .

Модели
В качестве предварительно обученных моделей мы выбрали MViTv2-small-32-2


Vjhjhgjhgjhg