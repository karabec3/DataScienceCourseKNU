1. Написати функцію pmean, яка обчислює середнє значення (mean)
забруднення сульфатами або нітратами серед заданого переліка
моніторів. Ця функція приймає три аргументи: «directory», «pollutant»,
«id». Directory – папка, в якій розміщені дані, pollutant – вид забруднення,
id – перелік моніторів. Аргумент id має значення за замовчуванням 1:332.
Функція повинна ігнорувати NA значення. Приклад роботи функції:
pmean("specdata", "sulfate", 1:10)
## [1] 4.064128

pmean <- function(directory, pollutant, id = 1:332){
  means <- numeric(length(id))
  
  for (i in id){
    file <- paste(directory, "/", formatC(i, width = 3, flag = "0"), ".csv", sep = "")
    data <- read.csv(file)
    
    means[i] <- mean(data[, pollutant], na.rm = TRUE)
  }
  
  return(means)
}

pmean("specdata", "sulfate", c(2, 4, 8, 10))

2. Написати функцію complete, яка виводить кількість повних спостережень
(the number of completely observed cases) для кожного файлу. Функція
приймає два аргументи: «Directory» та «id» та повертає data frame, в
якому перший стовпчик – ім’я файлу, а другий – кількість повних
спостережень.
complete <- function(directory, id) {
  files <- list.files(path = paste0(directory, "/"), pattern = paste0(id, ".csv"))
  data_list <- lapply(files, read.csv, header = TRUE)
  data_list <- lapply(data_list, function(x) x[!is.na(x$sulfate) & !is.na(x$nitrate),])
  nobs <- sapply(data_list, nrow)
  data_frame <- data.frame(id = id, nobs = nobs)
  return(data_frame)
}

3. Написати функцію corr, яка приймає два аргументи: directory (папка, де
знаходяться файли спостережень) та threshold (порогове значення, за
замовчуванням дорівнює 0) та обчислює кореляцію між сульфатами та
нітратами для моніторів, кількість повних спостережень для яких більше
порогового значення. Функція повинна повернути вектор значень
кореляцій. Якщо ні один монітор не перевищує порогового значення,
функція повинна повернути numeric вектор довжиною 0. Для обчислення
кореляції між сульфатами та нітратами використовуйте вбудовану функцію
«cor» з параметрами за замовчуванням.
corr <- function(directory, threshold = 0) {
    files <- list.files(directory, full.names = TRUE)
    data <- lapply(files, read.csv)
    complete_data <- data[sapply(data, function(x) sum(complete.cases(x)) > threshold)]
    cor_values <- sapply(complete_data, function(x) cor(x$sulfate, x$nitrate))
    return(cor_values)
}
