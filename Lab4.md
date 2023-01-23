data <- read.csv("hw1_data.csv")

1. Які назвис товпців файлу даних?
colnames(data)

2. Виведіть перші 6 строк фрейму даних.
head(data, 6)

3. Скільки спостерігань (строк) в датафреймі?
nrow(data)

4. Виведіть останні 10 строк датафрейму.
tail(data, 10)


5. Як багато значень «NA» встовпці «Ozone»?

sum(is.na(data$Ozone))

6. Якесереднє(mean)стовпця«Ozone».Виключити«NA»значення.

mean(data$Ozone, na.rm = TRUE)

7. Виведіть частину набору даних (subset) зі значенням «Ozone» > 31 та
«Temp» > 90. Яке середнє (mean) значень «Solar.R» в цьому наборі даних
(subset)?

subset_data <- data[data$Ozone > 31 & data$Temp > 90,]
mean(subset_data$Solar.R, na.rm = TRUE)

8. Яке середнє значення(mean)для«Temp»для червня(«Month»дорівнює
6)?

mean(data$Temp[data$Month == 6], na.rm = TRUE)

9. Яке максимальне значення «Ozone» для травня («Month» дорівнює 5)?
10. 
max(data$Ozone[data$Month == 5], na.rm = TRUE)
