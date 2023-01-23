1. Функція add2(x, y), яка повертає суму двох чисел.
add2 <- function(x, y) {
  return (x + y)
}

result <- add2(3, 5) 

2. Функція above(x, n), яка приймає вектор та число n, та повертає всі елементі вектору, які більше n. По замовчуванню 
n = 10.
above <- function(x, n = 10) {
  return (x[x > n])
}

result <- above(c(1, 2, 3, 15, 20, 25)) 

3. Функція my_ifelse(x, exp, n), яка приймає вектор x, порівнює всі його елементи за допомогою exp з n, та повертає елементи вектору, які відповідають умові expression. Наприклад, my_ifelse(x, “>”, 0) повертає всі елементи x, які більші 0. Exp може дорівнювати “<”, “>”, “<=”, “>=”, “==”. Якщо exp не співпадає ні з одним з цих виразів, повертається вектор x.
my_ifelse <- function(x, exp, n) {
  if (exp == ">") {
    return(x[x > n])
  } else if (exp == "<") {
    return(x[x < n])
  } else if (exp == ">=") {
    return(x[x >= n])
  } else if (exp == "<=") {
    return(x[x <= n])
  } else if (exp == "==") {
    return(x[x == n])
  } else {
    return(x)
  }
}

result <- my_ifelse(c(1, 2, 3, 15, 20, 25), ">", 10) 

4. Функція columnmean(x, removeNA), яка розраховує середнє значення (mean) по кожному стовпцю матриці, або data frame. Логічний параметр removeNA вказує, чи видаляти NA значення. По замовчуванню він дорівнює TRUE.
columnmean <- function(x, removeNA = TRUE) {
  if (removeNA == TRUE) {
    sapply(x, function(col) mean(col, na.rm = TRUE))
  } else {
    sapply(x, mean)
  }
}

mat <- matrix(c(1, 2, 3, 4, 5, NA, 7, 8, 9), nrow = 3, ncol = 3)
df <- data.frame(a = c(1, 2, NA), b = c(3, 4, 5))

columnmean(mat)
columnmean(df)

columnmean(mat, removeNA = FALSE)
columnmean(df, removeNA = FALSE)
