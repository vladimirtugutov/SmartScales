# SmartScales
Проект по распознавания вида фруктов и овощей, а также их веса
Аннотация

Суть проекта заключается в распознавании фруктов и овощей, а также их массы на весах. На основании этих данных выводится сумма покупки. Пример работы продемонстрирован ниже.

![](https://github.com/vladimirtugutov/SmartScales/blob/main/web_gif.gif)
Формирование датасета

Для обучения модели мы собрали датасет изображений фруктов и овощей. Было решено взять 8 популярных видов весовых продуктов, а именно: яблоки, бананы, апельсины, лимоны, морковь, томаты, картофель и брокколи. Для каждого класса были отобраны 300-350 фотографий, затем с помощью сервиса Make Sence эти фотографии были размечены для каждого класса. В итоге наш датасет содержал примерно 2500 фотографий и файлов разметки.
Обучение модели

Для распознавания продуктов на весах мы использовали нейросеть YOLOv4, которую обучили на наших классах овощей и фруктов. Выбор нейросети YOLOv4 был обусловлен тем, что на датасете Microsoft COCO данная нейросеть показала самый точный результата по метрике AP50. При обучении модели использовался фреймворк Darknet. Обучение происходило в Google Colaboratory с помощью видеокарты Tesla K80. Обучение заняло в общей сложности 57 часов и результат оценки модели с помощью метрики mAP составляет 70%. В папке training лежат все необходимые файлы для обучения, в том числе файл для обучения в Colab.
Распознавание цифр на весах

При распозновании данных с весов решалась задача оптического распознования символов. Из фотографии, полученной с веб-камеры, выделялась область с показаниями весов. В этой области с помощью библиотеки PyTesseract выводился вес продукта на весах.
Создание web-сервиса

Backend был осуществлен с помощью фреймворка Flask. На главной странице сайта ведется трансляция с веб-камеры, направленной на весы. По нажатию кнопки делается фото и отправляется на предикт в модель. После этого осуществляется переход на страницу с результатом, а именно вид продукта на весах и его стоимость. Frontend разработали с помощью HTML/CSS и фреймворка Bootstrap.
Авторы

https://github.com/Nik1-L

https://github.com/arinashkanova

https://github.com/vladimirtugutov

P. S. Для запуска нашей модели локально необходимо локально установить Darknet и в нем поменять папки cfg и data на наши, а также в корень darknet загрузить веса модели. В папке web лежит все, что касается frontend, в папке utilites - backend.
