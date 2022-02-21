# Домашнее задание №1
Пирожкина Мария группа 4

#Обязательная часть <br>
[Ссылка](https://colab.research.google.com/drive/1n5dTlufNcaYD5fvBnv3vS5gC3E8_0vt4?usp=sharing) на гугл-колаб

a) Cводная таблица, в которой записано число ридов, закартированных на участки 11347700-11367700; 40185800-40195800
![Снимок экрана 2022-02-18 в 13 26 55](https://user-images.githubusercontent.com/34075090/154694825-d67561ac-dcb8-4651-ae3d-592be4bcaf1e.png)
<br>
b) Сколько процентов прочтений дуплицированно в каждом из образцов? <br>
![Снимок экрана 2022-02-18 в 13 44 53](https://user-images.githubusercontent.com/34075090/154694991-c20e27a8-7f66-4d4c-b1b9-709a9b0b6235.png)<br>
c) в коллабе<br>
d)загружено в общую директорию <br>
8cell - CpG ~43% <br>
Cкриншот M-bias plot<br>
![Снимок экрана 2022-02-21 в 23 46 57](https://user-images.githubusercontent.com/34075090/155024401-9de74c02-ccdf-4bcd-ad80-a6b96a315823.png)
![Снимок экрана 2022-02-21 в 23 42 12](https://user-images.githubusercontent.com/34075090/155024413-98c402b6-b32a-485f-a34d-74a0c7dbf0ab.png)
<br>
ICM - CpG ~24% <br>
Cкриншот M-bias plot<br>
![Снимок экрана 2022-02-21 в 23 46 45](https://user-images.githubusercontent.com/34075090/155024456-4ce40bec-1963-45c5-ab17-dfe7e301c6dc.png)
![Снимок экрана 2022-02-21 в 23 47 52](https://user-images.githubusercontent.com/34075090/155024471-86b05203-c1db-4962-b2cd-4c372893ced3.png)

epiblast - CpG ~78% <br>
Cкриншот M-bias plot<br>
![Снимок экрана 2022-02-21 в 23 48 30](https://user-images.githubusercontent.com/34075090/155024604-119712a3-005b-44f1-9423-868241e4427e.png)
![Снимок экрана 2022-02-21 в 23 48 30](https://user-images.githubusercontent.com/34075090/155024630-0cab3d50-f37d-428c-b534-eebe8ec6a4c4.png)
![Снимок экрана 2022-02-21 в 23 48 23](https://user-images.githubusercontent.com/34075090/155024631-78e3a269-8147-49a9-9372-a24f3eb61adb.png)
<br>


e) Гистограмма распределения метилирования цитозинов по хромосоме ( насколько часто метилируются цитозины в данном образце: по X процент метилированных цитозинов, по Y - частота)<br>
![Снимок экрана 2022-02-18 в 15 57 41](https://user-images.githubusercontent.com/34075090/154695515-02fda26d-cd42-4334-a9e0-aff1deb1a84a.png)
![Снимок экрана 2022-02-18 в 15 58 27](https://user-images.githubusercontent.com/34075090/154695527-0023f80c-90fe-4252-bbf8-563bf118e3e0.png)
![Снимок экрана 2022-02-18 в 15 59 02](https://user-images.githubusercontent.com/34075090/154695528-14dd4af9-1f56-491b-b885-34b939b6f077.png)<br>
Выводы: на гисторграмах видно, что в 8cell частота метилированных цитозинов имеет пик в нулевом проценте и 100%. Чаще всего цитозины метилируются в образце epiblast, стадия в примерно 6.5 дней после оплодотворения яйцеклетки, где достаточно ярко видны после 50%. Самая высокая частота метилирования цитозинов в координате равной нулю находит в образце ICM. Что доказывает следующую гипотезу: на ранних стадиях CpG метилирование уменьшается до некоторого минимума (около 25%), а затем по мере дифференцировки тканей, оно сильно увеличивается (около 90%).
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

