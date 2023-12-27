# Hakaton_1 Команда №5

Представляем Вашему вниманию работу по автосурдопереводчику основанному на предобученой модели Slovo.

Slovo — набор данных русского языка жестов. Набор видеоданных «Slovo» для задачи русского жестового языка. Размер набора данных Slovo составляет около 16 ГБ и содержит 20400 RGB-видео для 1000 жестов языка жестов от 194 человек. В каждом классе по 20 образцов. Набор данных разделен на обучающий набор и тестовый набор по темам user_id. Обучающий набор включает 15300 видеороликов, тестовый набор — 5100 видеороликов. Общее время записи видео составляет ~9,2 часа. Около 35% видеороликов записаны в формате HD, а 65% видео — в разрешении FullHD. Средняя продолжительность видео с жестом — 50 кадров.
Для получения дополнительной информации см. https://github.com/hukenovs/slovo

Файл аннотаций прост в использовании и содержит несколько полезных столбцов, см. annotations.csvфайл:

![image](https://github.com/osipov779/Hakaton_1/assets/151464254/663377c6-be86-48f6-86bd-804b69f8eec6)


где:\
attachment_id- имя видеофайла\
user_id- уникальный анонимизированный идентификатор пользователя\
width- ширина видео\
height- высота видео\
length- длина видео\
text- урок жестов на русском языке\
train- обучить или проверить логический флаг\
begin- начало жеста (для исходного набора данных)\
end- конец жеста (для исходного набора данных)\
\
Для удобства подготовлена сжатая версия датасета, в которой все видео обрабатываются с минимальной стороны min_side = 360. Ссылка для скачивания — slovo360p .  Обрезанные видео аннотируются с помощью MediaPipe и указываем ключевые точки руки в этом файле аннотаций .

## Модели
В качестве предварительно обученных моделей мы выбрали MViTv2-small-32-2

ONNX [weights](https://n-ws-620xz-pd11.s3pd11.sbercloud.ru/b-ws-620xz-pd11-jux/slovo/models/mvit/onnx/mvit32-2.onnx)\
TorchScript [weights](https://n-ws-620xz-pd11.s3pd11.sbercloud.ru/b-ws-620xz-pd11-jux/slovo/models/mvit/pt/mvit32-2.pt)

## Модели SignFlow

| Model Name | Desc                                                                                                                | ONNX                                                                                                    | Params |
|------------|---------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|
| SignFlow-A | **63.3 Top-1** Acc on  [WLASL-2000](https://paperswithcode.com/sota/sign-language-recognition-on-wlasl-2000) (SOTA) | [weights](https://n-ws-620xz-pd11.s3pd11.sbercloud.ru/b-ws-620xz-pd11-jux/slovo/models/SignFlow-A.onnx) | 36M    |
| SignFlow-R | Pre-trained on **~50000** samples, has **267** classes, tested with GigaChat (as-is and context-based modes)        | [weights](https://n-ws-620xz-pd11.s3pd11.sbercloud.ru/b-ws-620xz-pd11-jux/slovo/models/SignFlow-R.onnx) | 37M    |


## Демо
```console
usage: demo.py [-h] -p CONFIG [--mp] [-v] [-l LENGTH]

optional arguments:
  -h, --help            show this help message and exit
  -p CONFIG, --config CONFIG
                        Path to config
  --mp                  Enable multiprocessing
  -v, --verbose         Enable logging
  -l LENGTH, --length LENGTH
                        Deque length for predictions


python demo.py -p <PATH_TO_CONFIG>
```

![demo](images/demo.gif)

## Авторы
- Рушана: Тимлид
- Дмитрий: Клинический эксперт, консультант по работе поликлиники, бизнес-аналитик
- Виктория: Data инженер 
- Екатерина: Data инженер
- Денис: ML инженер
- Алексей: ML инженер 


## Citation
You can cite the paper using the following BibTeX entry:

    @inproceedings{kapitanov2023slovo,
        title={Slovo: Russian Sign Language Dataset},
        author={Kapitanov, Alexander and Karina, Kvanchiani and Nagaev, Alexander and Elizaveta, Petrova},
        booktitle={International Conference on Computer Vision Systems},
        pages={63--73},
        year={2023},
        organization={Springer}
    }

## Links
- [arXiv](https://arxiv.org/abs/2305.14527)
- [Kaggle](https://www.kaggle.com/datasets/kapitanov/slovo)
- [Habr](https://habr.com/ru/companies/sberdevices/articles/737018/)
- [Medium](https://medium.com/@nagadit/slovo-russian-sign-language-dataset-a8a8bd6fa17d)
- [Github](https://github.com/hukenovs/slovo)
- [Gitlab](https://gitlab.aicloud.sbercloud.ru/rndcv/slovo)
- [Paperswithcode](https://paperswithcode.com/paper/slovo-russian-sign-language-dataset)

## License
<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/88x31.png" /></a><br />This work is licensed under a variant of <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>.

Please see the specific [license](https://github.com/hukenovs/slovo/blob/master/license/en_us.pdf).
