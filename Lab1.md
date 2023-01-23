
1. Створити змінні базових (atomic) типів. Базові типи: character, numeric, integer, complex, logical.
my_character <- "Hello"
my_numeric <- 3.14
my_integer <- 42
my_complex <- 3 + 4i
my_logical <- TRUE

2. Створити вектори, які: містить послідовність з 5 до 75; містить числа 3.14, 2.71, 0, 13; 100 значень TRUE.
my_vector1 <- 5:75
my_vector2 <- c(3.14, 2.71, 0, 13)
my_vector3 <- rep(TRUE, 100)

3. Створити наступну матрицю за допомогою matrix, та за допомогою cbind 
matrix(c(0.5, 1.3, 3.5, 3.9, 131, 2.8, 0, 2.2, 4.6, 2, 7, 5.1), nrow = 4, ncol = 3, byrow = TRUE)
cbind(c(0.5, 1.3, 3.5), c(3.9, 131, 2.8), c(0, 2.2, 4.6), c(2, 7, 5.1))

4. Створити довільний список (list), в який включити всі базові типи.
my_list <- list(my_character, my_numeric, my_integer, my_complex, my_logical)

5. Створити фактор з трьома рівнями «baby», «child», «adult».
my_factor <- factor(c("baby", "child", "adult", "child", "baby"), levels = c("baby", "child", "adult"))

6. Знайти індекс першого значення NA в векторі 1, 2, 3, 4, NA, 6, 7, NA, 9, NA, 11. Знайти кількість значень NA.
my_vector <- c(1, 2, 3, 4, NA, 6, 7, NA, 9, NA, 11)
first_na_index <- which(is.na(my_vector))[1]
na_count <- sum(is.na(my_vector))

7. Створити довільний data frame та вивести в консоль.
name <- c("Alice", "Bob", "Charlie")
age <- c(25, 30, 35)
gender <- c("F", "M", "M")
my_data_frame <- data.frame(name, age, gender)

8. Змінити імена стовпців цього data frame.
colnames(my_data_frame) <- c("Name", "Age", "Gender")
print(my_data_frame)
