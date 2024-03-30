# sirius,dop.zadanie
import cv2
import cvlib as cv
from cvlib.object_detection import draw_bbox
import os
import matplotlib.pyplot as plt
image_path = r'image2.png.'

# Проверяем,существует ли файл
if not os.path.exists(image_path):
    print(f"Файл не найден: {image_path}")
else:
    image = cv2.imread(image_path)
#Мы не смогли вывести результат на экран,по причине проблемы пути изображения.Для этого создали цикл проверки.
    if image is None:
        print(f"Не удалось загрузить изображение по пути: {image_path}")
    else:
        box, label, c_score = cv.detect_common_objects(image)
        output_image = draw_bbox(image, box, label, c_score)

        plt.imshow(cv2.cvtColor(output_image, cv2.COLOR_BGR2RGB))
        plt.show()

        print('Количество обнаруженных людей на изображении:', label.count('person'))
