# Домашнее задание №1
Пирожкина Мария группа 4

#Обязательная часть <br>
[Ссылка](https://colab.research.google.com/drive/1n5dTlufNcaYD5fvBnv3vS5gC3E8_0vt4?usp=sharing) на гугл-колаб

Cводная таблица, в которой записано число ридов, закартированных на участки 11347700-11367700; 40185800-40195800
![Снимок экрана 2022-02-18 в 13 26 55](https://user-images.githubusercontent.com/34075090/154694825-d67561ac-dcb8-4651-ae3d-592be4bcaf1e.png)

Сколько процентов прочтений дуплицированно в каждом из образцов? <br>
![Снимок экрана 2022-02-18 в 13 44 53](https://user-images.githubusercontent.com/34075090/154694991-c20e27a8-7f66-4d4c-b1b9-709a9b0b6235.png)

Cкриншот M-bias plot<br>
На скриншоте видно...

Гистограмма распределения метилирования цитозинов по хромосоме ( насколько часто метилируются цитозины в данном образце: по X процент метилированных цитозинов, по Y - частота)
![Снимок экрана 2022-02-18 в 15 57 41](https://user-images.githubusercontent.com/34075090/154695515-02fda26d-cd42-4334-a9e0-aff1deb1a84a.png)
![Снимок экрана 2022-02-18 в 15 58 27](https://user-images.githubusercontent.com/34075090/154695527-0023f80c-90fe-4252-bbf8-563bf118e3e0.png)
![Снимок экрана 2022-02-18 в 15 59 02](https://user-images.githubusercontent.com/34075090/154695528-14dd4af9-1f56-491b-b885-34b939b6f077.png)
Выводы ...
Код построения:
```
! ls *bedGraph.gz | xargs -tI{} gzip -d {}
! head s_SRR5836473_1_bismark_bt2_pe.deduplicated.bedGraph
import pandas as pd

df = pd.read_csv("s_SRR5836473_1_bismark_bt2_pe.deduplicated.bedGraph", delimiter='\t', skiprows=1, header=None)
df.head()
import matplotlib.pyplot as plt

plt.figure(figsize=[10, 6])
plt.title("Распределение метилирования 8cell", fontsize=14)
plt.hist(df[3], bins=100, density=True)
plt.show()

df2 = pd.read_csv("s_SRR3824222_1_bismark_bt2_pe.deduplicated.bedGraph", delimiter='\t', skiprows=1, header=None)

plt.figure(figsize=[10, 6])
plt.title("Распределение метилирования Epiblast", fontsize=14)
plt.hist(df2[3], bins=100, density=True)
plt.show()

df3 = pd.read_csv("s_SRR5836475_1_bismark_bt2_pe.deduplicated.bedGraph", delimiter='\t', skiprows=1, header=None)

plt.figure(figsize=[10, 6])
plt.title("Распределение метилирования ICM", fontsize=14)
plt.hist(df3[3], bins=100, density=True)
plt.show()
```
f) Метилирование:![image](https://user-images.githubusercontent.com/34075090/155022244-39082b14-8b34-46b9-9a75-01ee0d2cc033.png)
<br>
Покрытие:![image2](https://user-images.githubusercontent.com/34075090/155022254-8de8cce2-5964-4f7e-b72b-36304d0604df.png)

