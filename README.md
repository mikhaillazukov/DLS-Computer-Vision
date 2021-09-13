# Прохождение продвинутого потока по Computer Vision от MIPT DLS

Тематики мини-проектов:
1. ML задача
2. Классификация
3. Сегментация. Семантическая сегментация медицинских снимков
4. Автоэнкодеры
5. ГАН

# ML задача 
Предсказание оттока пользователей. Ссылка задачи на Kaggle:
https://www.kaggle.com/c/advanced-dls-spring-2021/

Решение задачи состоит из анализа данных с последующим применением линейных моделей. Для достижения наилучших результатов использовался градиентный бустинг, а в частности библиотека catboost.

Результат: ROC AUC 0.85186

# Классификация
Задача классификации персонажей Симпсонов. Ссылка задачи на Kaggle: https://www.kaggle.com/c/journey-springfield

Для решения использовалась предобученная сеть ResNet 50. Применялась аугментация данных (повороты, отзеркаливание, гауссовский шум). 

Точность: 0.99787

<img src="https://raw.githubusercontent.com/mikhaillazukov/DLS-Computer-Vision/main/images/simpsons.png?raw=true">

# Сегментация
Задача сегментации медицинских снимков. Производится семантическая сегментация двух типов поражений кожи: меланома и родинки. Ссылка на набор данных: https://www.fc.up.pt/addi/ph2%20database.html

Для решения задачи были реализованы две архитектуры нейронных сетей: SegNet и UNet, а также были произведены эксперименты с различными функциями потерь. 

Наилучший результат был достигнут при использовании сети Unet с качеством на тестовой выборке 0.8104

<img src="https://raw.githubusercontent.com/mikhaillazukov/DLS-Computer-Vision/main/images/unet_example.png?raw=true">

# Автоэнкодеры

Проводились эксперименты по создание и обучению AE, VAE и CVAE.

Автоэнкодер обучался воссоздавать лица. Латентный вектор равен 128. Полученные изображения восстанавливаются довольно размытыми, но при этом сохраняются очертания исходного изображения.

<img src="https://raw.githubusercontent.com/mikhaillazukov/DLS-Computer-Vision/main/images/ae_face.png?raw=true">

После чего был выделен вектор улыбки, при добавлении которого к латентному вектору исходного изображения к нему добавляется улыбка. К сожалению, большинство улыбчивых изображений в выборке - женщины, поэтому изображения не только начинают улыбаться, но и меняют пол на женский.

<img src="https://raw.githubusercontent.com/mikhaillazukov/DLS-Computer-Vision/main/images/ae_smiling.png?raw=true">

Вариационные автоэнкодер обучался на наборе данных MNIST.

<img src="https://raw.githubusercontent.com/mikhaillazukov/DLS-Computer-Vision/main/images/VAE.png?raw=true">

CVAE также обучался на данных MNIST, но благодаря своим особенностям мы можем управлять тем, какая цифра будет сгенерирована.

Восстановленные изображения.
<img src="https://raw.githubusercontent.com/mikhaillazukov/DLS-Computer-Vision/main/images/CVAE1.png?raw=true">

Сгенерированные изображения конкретных цифр.
<img src="https://raw.githubusercontent.com/mikhaillazukov/DLS-Computer-Vision/main/images/CVAE2.png?raw=true">

# ГАН

Создание и обучение ГАН для генерации лиц.

<img src="https://raw.githubusercontent.com/mikhaillazukov/DLS-Computer-Vision/main/images/dcgan.png?raw=true">

