# 📊 Statistics with R — Examination-Ready Notes

### *A complete, syllabus-aligned revision guide for first-time learners*

[![R](https://img.shields.io/badge/Language-R-276DC3?style=for-the-badge&logo=r&logoColor=white)](https://www.r-project.org/) [![RStudio](https://img.shields.io/badge/IDE-RStudio-75AADB?style=for-the-badge&logo=rstudio&logoColor=white)](https://posit.co/products/open-source/rstudio/) [![Syllabus Coverage](https://img.shields.io/badge/Syllabus-100%25-success?style=for-the-badge)](#) [![Units](https://img.shields.io/badge/Units-3-blueviolet?style=for-the-badge)](#-table-of-contents) [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](LICENSE) [![Made by NDxGenius](https://img.shields.io/badge/Maintained%20by-NDxGenius-0A66C2?style=for-the-badge&logo=github)](https://github.com/NishantDas0079)

*Covers data extraction → R fundamentals → descriptive statistics → regression → time series, with runnable R code, formulas, exam tips, and mnemonics baked into every section.*

---

## 📌 About This Repository

This repo is a **single-source revision guide** for a *Statistics with R* course — built so you can go from "what is a data frame?" to "how do I diagnose heteroscedasticity in a regression model?" without leaving one document.

Every topic follows the same four-beat structure:

| Beat | What you get |
| --- | --- |
| 💡 **Idea** | A one-line, plain-English explanation of the concept |
| 💻 **Syntax** | Copy-paste-ready R code in fenced, highlighted blocks |
| 📐 **Reference** | Tables, formulas, and decision rules for exam answers |
| 🧠 **Memory Aid** | A mnemonic or tip callout to lock it in before the exam |

> **Audience:** Undergraduates / first-time R learners · **Scope:** 3 Units · **Class Hours:** 60

---

## 🗺️ How to Use This Repository

```mermaid
flowchart LR
    A[Unit 1<br/>Where data comes from] --> B[Unit 2<br/>Learn the R language]
    B --> C[Unit 3<br/>Apply R to Statistics]
    C --> D[📋 Cheat Sheet<br/>Final revision]

    style A fill:#1e3a8a,color:#fff
    style B fill:#1d4ed8,color:#fff
    style C fill:#2563eb,color:#fff
    style D fill:#f59e0b,color:#111
```

> **📘 Reading tip:** Finish **Unit 2** fully before **Unit 3** — almost every regression and time-series concept depends on data frames, vectors, and `dplyr`. **Unit 1** is a standalone "where does data come from?" chapter and can be read any time.

---

## 📑 Table of Contents

- [Unit 1 · Data Extraction and Spreadsheet Exploration](#unit-1--data-extraction-and-spreadsheet-exploration)
  - [1.1 Major Financial & Economic Data Sources](#11--major-financial--economic-data-sources)
  - [1.2 Saving and Exporting Data to R](#12--saving-and-exporting-data-to-the-r-environment)
- [Unit 2 · Basics of R-language](#unit-2--basics-of-r-language)
  - [2.1 Overview, Installation & Packages](#21--overview-of-the-r-language)
  - [2.2 Data Types](#22--data-types-in-r)
  - [2.3 Data Structures — Vectors, Matrices, Arrays](#23--data-structures--vectors-matrices-arrays)
  - [2.4 Factors](#24--factors)
  - [2.5 Lists](#25--lists)
  - [2.6 Data Frames & `dplyr`](#26--data-frames--dplyr-manipulation)
  - [2.7 Programming Fundamentals](#27--programming-fundamentals)
  - [2.8 Creating Functions](#28--creating-functions-in-r)
  - [2.9 Reading & Writing Data](#29--reading--writing-data-in-r)
- [Unit 3 · Basic Statistics and Regression](#unit-3--basic-statistics-and-regression)
  - [3.1 Descriptive Statistics](#31--descriptive-statistics)
  - [3.2 Data Cleaning & Missing Values](#32--data-cleaning--missing-values)
  - [3.3 EDA & Visualisation](#33--exploratory-data-analysis-eda--visualisation)
  - [3.4 Regression Analysis](#34--regression-analysis)
  - [3.5 CNLRM Assumptions & Diagnostics](#35--assumptions-of-cnlrm--diagnostic-tests)
  - [3.6 Time Series Basics](#36--time-series--basics)
- [🧠 Mnemonics & Memory Aids](#-mnemonics--memory-aids)
- [📋 One-Page Cheat Sheet](#-one-page-cheat-sheet)
- [🎯 Exam Strategy](#-exam-strategy)
- [🤝 Contributing](#-contributing)
- [📄 License](#-license)

---

## Unit 1 · Data Extraction and Spreadsheet Exploration

`⏱ 12 Hours` · **One-line idea:** Any statistical analysis is only as good as the data behind it — this unit covers where to get reliable data and how to land it inside R.

### 1.1 · Major Financial & Economic Data Sources

| Source | What it gives you | Typical use |
| --- | --- | --- |
| **ProwessIQ** (CMIE) | Financial performance of Indian listed companies (P&L, balance sheet, ratios) | Company-level finance research, ratio analysis |
| **RBI Database** (DBIE) | Macroeconomic indicators of India — interest rates, money supply, forex, GDP, inflation | Macroeconomics, monetary policy study |
| **IMF Data** (WEO / IFS) | Cross-country macro data — GDP, CPI, BoP, exchange rates, reserves | Comparative country studies, international finance |
| **World Bank Open Data** | Development indicators across 200+ countries — poverty, education, health, trade | Development economics, panel data studies |

🧠 **Mnemonic — "P-R-I-W on the world"**

**P**rowessIQ · **R**BI · **I**MF · **W**orld Bank — coverage scales up from one firm → one country → many countries → global development.

**Common workflow:**

1. Visit the chosen database's website (e.g. `dbie.rbi.org.in`)
2. Browse / search for the indicator (e.g. *"Repo Rate"*, *"WPI Inflation"*)
3. Filter by frequency (Daily / Monthly / Quarterly / Annual) and date range
4. Download as **CSV / Excel / TXT** — formats R can read directly

> ✅ **Exam tip:** "Which database for company-level financial data of Indian firms?" → **ProwessIQ**. Macro India → **RBI**. Cross-country → **IMF or World Bank**.

### 1.2 · Saving and Exporting Data to the R Environment

```r
# ---- Reading a CSV file (most common) ----
setwd("C:/Users/YourName/Documents")        # set working directory
data <- read.csv("rbi_data.csv", header = TRUE, sep = ",")
head(data)

# ---- Reading an Excel file ----
install.packages("readxl")                  # once only
library(readxl)
data <- read_excel("worldbank_data.xlsx", sheet = 1)
```

| File source | R function | Package needed |
| --- | --- | --- |
| CSV | `read.csv()` | Base R |
| TXT (tab/space separated) | `read.table()` / `read.delim()` | Base R |
| Excel (`.xlsx`) | `read_excel()` | `readxl` |
| R-native format | `saveRDS()` / `readRDS()` | Base R |

```r
# ---- Saving R data for future use ----
save(data, file = "my_data.RData");  load("my_data.RData")
saveRDS(data, "my_data.rds");        data2 <- readRDS("my_data.rds")
```

> ⚠️ **Remember:** CSV is the universal export format; `.RData` preserves R object types exactly. Always set the working directory (`setwd()`) or use full file paths first.

---

## Unit 2 · Basics of R-language

`⏱ 28 Hours` · **One-line idea:** R is the workbench on which you'll clean, model, and visualise data — this unit covers the language, its data types, structures, control flow, and I/O.

### 2.1 · Overview of the R Language

R is a **free, open-source programming language** built for statistical computing and graphics, widely used in data science, econometrics, and research.

| Tool | Purpose |
| --- | --- |
| **R (base)** | The core engine — install from `cran.r-project.org` |
| **RStudio** | IDE with 4 panes: Script, Console, Environment, Plots/Help |
| **Scripts** | `.R` files where code is saved |
| **Text editors** | Notepad++, VS Code, Sublime — alternatives to RStudio |
| **GUIs for R** | R Commander (`Rcmdr`), Deducer, Rattle — point-and-click for beginners |

```r
getwd()                       # see current working directory
setwd("D:/MyFolder")          # change working directory
ls()                           # list all objects in workspace
install.packages("dplyr")     # install a package (once, from CRAN)
library(dplyr)                 # load the package into the session
```

> 📝 **Package vs Library:** *Package* = the bundle of code on disk. *Library* = the folder where packages live. `library(dplyr)` loads the package into the session — install once, `library()` every session.

```r
# ---- Mathematical operations ----
5 + 3      # Addition      → 8
10 - 4     # Subtraction   → 6
6 * 7      # Multiplication→ 42
20 / 5     # Division      → 4
2 ^ 3      # Power         → 8
17 %% 5    # Modulus       → 2
17 %/% 5   # Integer div.  → 3

sqrt(16); log(10); log10(100); exp(2); abs(-5); round(3.14159, 2)
```

### 2.2 · Data Types in R

| Type | Example | Used for | Check with |
| --- | --- | --- | --- |
| Numeric (double) | `3.14`, `42` | Any number, integer or decimal | `typeof(3.14)` → `"double"` |
| Integer | `5L` | Whole numbers — memory-efficient | `typeof(5L)` → `"integer"` |
| Character | `"Hello"`, `'R'` | Text — names, labels, categories | `typeof("R")` → `"character"` |
| Logical | `TRUE`, `FALSE` | Boolean conditions / comparisons | `typeof(TRUE)` → `"logical"` |
| Complex | `3 + 2i` | Imaginary numbers (rare in stats) | `typeof(3+2i)` → `"complex"` |
| Missing | `NA`, `NaN`, `NULL`, `Inf` | Absent / undefined values | `is.na(x)`, `is.null(x)` |

> **Differences:** `NA` = missing data (any type) · `NaN` = impossible math op (`0/0`) · `NULL` = an empty object · `Inf`/`-Inf` = infinity (`1/0`).

```r
x <- 42.5
class(x); is.numeric(x); is.character(x)

# ---- Coercion ----
as.integer(42.5)    # → 42 (truncates)
as.character(42)    # → "42"
as.numeric("3.14")  # → 3.14
as.logical(0)       # → FALSE (0 → FALSE, anything else → TRUE)
```

### 2.3 · Data Structures — Vectors, Matrices, Arrays

#### 2.3.1 Vectors — 1-D sequence of same-type values

```r
v <- c(10, 20, 30, 40)
names <- c("Aman", "Riya", "Kabir")

1:10                          # 1 to 10
seq(0, 1, by = 0.25)          # 0, 0.25, 0.5, 0.75, 1
seq(0, 1, length.out = 5)     # 0, 0.25, 0.5, 0.75, 1
rep(5, times = 4)             # 5 5 5 5
rep(c(1,2), each = 3)         # 1 1 1 2 2 2

# ---- Element-wise arithmetic ----
v + 5; v * 2; v ^ 2; sum(v); mean(v); length(v)

# ---- Subsetting ----
v2 <- c("A","B","C","D","E")
v2[1]; v2[c(1,3,5)]; v2[-2]; v2[v2 == "C"]

# ---- Sorting ----
sort(c(3,1,2)); sort(c(3,1,2), decreasing = TRUE); order(c(3,1,2))
```

#### 2.3.2 Matrix and Arrays

```r
m <- matrix(1:6, nrow = 2, ncol = 3)   # 2x3 matrix, filled column-wise
cbind(c(1,2), c(3,4))                   # column-bind
rbind(c(1,3), c(2,4))                   # row-bind

m + 10; m * 2; m %*% t(m)               # arithmetic & matrix multiplication

m[1, 2]   # row 1, col 2 → 3
m[1, ]    # entire row 1 → 1 3 5
m[, 2]    # entire col 2 → 3 4

arr <- array(1:12, dim = c(2, 3, 2))    # array = matrix in 3+ dimensions
dim(arr)                                 # 2 3 2
```

> 📎 **`drop` gotcha:** Selecting a single row/column of a matrix returns a vector by default. Use `m[1, , drop = FALSE]` to keep it as a 1×3 matrix.

### 2.4 · Factors

A **factor** stores categorical data (gender, region, grade) as integers + a levels table — saving memory and enabling correct sorting/plotting.

```r
gender <- factor(c("Male","Female","Female","Male"))
levels(gender)                          # "Female" "Male"

grade <- factor(c("A","B","A","C"),
                 levels = c("C","B","A"),
                 labels = c("Poor","Good","Best"))

rating <- factor(c("Low","High","Medium"),
                  levels = c("Low","Medium","High"),
                  ordered = TRUE)        # ordinal data
```

| Function | What it does |
| --- | --- |
| `factor(x)` | Convert vector to factor |
| `levels(x)` | View / set category names |
| `labels =` | Replace category names with custom labels |
| `ordered = TRUE` | Treat the factor as having meaningful order |
| `nlevels(x)` | Count of distinct categories |

### 2.5 · Lists

A **list** holds any mix of types and structures — even other lists. Model outputs (e.g. `lm()`) are lists.

```r
my_list <- list(name = "Riya", age = 21,
                 scores = c(85, 90, 78), passed = TRUE)

my_list$name          # "Riya"      — by name
my_list[[2]]           # 21          — by position, returns the element
my_list[1]              # a sub-list  — returns a LIST, not the element

my_list$city <- "Mumbai"    # add an element
my_list$passed <- NULL      # remove an element
unlist(my_list)              # flatten to a single vector
```

> 📝 **Memory aid:** `[ ]` returns a *sub-list*. `[[ ]]` returns the *actual element*. `$` is shorthand for `[["name"]]`.

### 2.6 · Data Frames & `dplyr` Manipulation

A **data frame** is R's spreadsheet — a 2-D table where columns can differ in type but all rows share the same length.

```r
df <- data.frame(Name = c("Aman","Riya","Kabir"),
                  Age  = c(22, 21, 23),
                  Marks = c(85, 90, 78),
                  Passed = c(TRUE, TRUE, FALSE))

str(df); summary(df); nrow(df); ncol(df)

# ---- Add / remove rows & columns ----
df$Grade <- c("A","A+","B")
df <- rbind(df, data.frame(Name="Sara", Age=22, Marks=88, Passed=TRUE, Grade="A"))
df$Grade <- NULL             # remove a column
df <- df[, -4]                # OR drop by index

# ---- Access & subset ----
df$Age
df[1, ]                               # 1st row
df[, "Marks"]                          # Marks column
df[df$Age > 21, ]                     # conditional rows
df[df$Passed, c("Name","Marks")]      # condition + column select

# ---- split-apply-combine ----
aggregate(Marks ~ Passed, data = df, FUN = mean)
tapply(df$Marks, df$Passed, mean)
```

#### `dplyr` — the "grammar of data manipulation"

| Verb | Purpose | Example |
| --- | --- | --- |
| `select()` | Pick columns by name | `select(df, Name, Marks)` |
| `filter()` | Pick rows by condition | `filter(df, Age > 21)` |
| `arrange()` | Sort rows | `arrange(df, desc(Marks))` |
| `mutate()` | Create / modify columns | `mutate(df, Pct = Marks/100)` |
| `group_by()` | Group rows for summarising | `group_by(df, Passed)` |
| `summarise()` | Per-group summary | `summarise(mean(Marks))` |

```r
# ---- Pipe operator %>% — reads top-to-bottom like a recipe ----
df %>%
  filter(Age >= 21) %>%
  group_by(Passed) %>%
  summarise(avg_marks = mean(Marks))
```

🧠 **Mnemonic — "S-F-A-M-G-S"**

**S**elect · **F**ilter · **A**rrange · **M**utate · **G**roup_by · **S**ummarise — the `dplyr` verbs in the order you'll most often chain them.

### 2.7 · Programming Fundamentals

#### 2.7.1 Logical / Comparison Operators

| Operator | Meaning | Example |
| --- | --- | --- |
| `==` | Equal to | `x == 5` |
| `!=` | Not equal to | `x != 5` |
| `>`, `<` | Greater / less than | `x > 5` |
| `>=`, `<=` | Greater / less or equal | `x >= 5` |
| `&` | Element-wise AND | `x>0 & y<10` |
| `\|` | Element-wise OR | `x<0 \| x>10` |
| `!` | NOT | `!is.na(x)` |
| `&&`, `\|\|` | Single-value AND/OR | used inside `if()` |
| `%in%` | Membership | `x %in% c(1,2,3)` |

#### 2.7.2 Conditional Statements

```r
x <- 85
if (x >= 90) {
  print("Distinction")
} else if (x >= 60) {
  print("Pass")
} else {
  print("Fail")
}

ifelse(x > 50, "Pass", "Fail")   # vectorised version
```

#### 2.7.3 Loops

```r
# ---- for: known number of iterations ----
for (i in 1:5) print(paste("Iteration", i))

# ---- while: repeat until condition is false ----
i <- 1
while (i <= 5) { print(i); i <- i + 1 }

# ---- repeat: infinite loop, break out explicitly ----
i <- 1
repeat { print(i); i <- i + 1; if (i > 5) break }
```

> 💡 **When to use which?** `for` = known repeats · `while` = repeat while a condition holds · `repeat` = repeat until you manually `break`. In R, **vectorised operations are usually faster than loops.**

### 2.8 · Creating Functions in R

```r
greet <- function(name) paste("Hello,", name, "!")
greet("Riya")                    # "Hello, Riya !"

power <- function(x, p = 2) x ^ p    # default argument
power(3)                          # 9  (uses default p = 2)
power(3, p = 3)                   # 27

stats <- function(x) {            # return multiple values via a list
  list(mean = mean(x), sd = sd(x), n = length(x))
}
```

```
Function template:  name <- function(arg1, arg2, ...) { ... ; return(value) }
```

### 2.9 · Reading & Writing Data in R

| Action | CSV | TXT | Excel |
| --- | --- | --- | --- |
| **Read** | `read.csv("f.csv")` | `read.delim("f.txt")` | `readxl::read_excel("f.xlsx")` |
| **Write** | `write.csv(df, "f.csv")` | `write.table(df, "f.txt")` | `writexl::write_xlsx(df, "f.xlsx")` |

```r
df <- read.csv("data.csv", header = TRUE)
df <- read.delim("data.txt")
df <- read_excel("data.xlsx", sheet = 1)

write.csv(df, "out.csv", row.names = FALSE)
write.table(df, "out.txt", sep = "\t")
write_xlsx(df, "out.xlsx")

print("Hello"); print(head(df))
```

> ⚠️ **Common mistake:** Always pass `row.names = FALSE` when writing a CSV, otherwise R adds a row-number column on re-read.

📘 **Unit 2 Recap**

- **Data Types** = the flavour of one value (numeric, character…)
- **Data Structures** = containers (vector, matrix, list, data frame)
- **`dplyr` verbs** (S-F-A-M-G-S) + the pipe `%>%` = the modern way to wrangle data

---

## Unit 3 · Basic Statistics and Regression

`⏱ 20 Hours` · **One-line idea:** Now that you know R, this unit turns the language into statistics — summarising, cleaning, visualising, modelling, diagnosing, and forecasting data.

### 3.1 · Descriptive Statistics

#### 3.1.1 Measures of Central Tendency

| Measure | What it captures | R function | When to use |
| --- | --- | --- | --- |
| **Mean** | Arithmetic average | `mean(x)` | Symmetric data, no outliers |
| **Median** | Middle value (50th percentile) | `median(x)` | Skewed data, has outliers |
| **Mode** | Most frequent value | `table(x)` → pick largest | Categorical / discrete data |

$$\\bar{x} = \\frac{x_1 + x_2 + \\dots + x_n}{n} \\qquad s^2 = \\frac{\\sum (x_i - \\bar{x})^2}{n - 1} \\qquad s = \\sqrt{s^2}$$

#### 3.1.2 Skewness

| Skewness | Interpretation | Tail |
| --- | --- | --- |
| ≈ 0 | Symmetric (mean ≈ median) | Even |
| > 0 (positive) | Right-skewed | Long tail right (income, house prices) |
| \< 0 (negative) | Left-skewed | Long tail left (exam scores if most pass) |

#### 3.1.3 Five-Point Summary

```r
x <- c(2,5,8,9,12,15,20)
summary(x)                                # Min Q1 Median Q3 Max
fivenum(x)                                 # Tukey's version
quantile(x, probs = c(0.25, 0.5, 0.75))

library(moments)
mean(x); median(x); var(x); sd(x); skewness(x); kurtosis(x); summary(x)
```

> 📝 **Median vs Mean:** With outliers, the median is the safer "typical value." On roughly symmetric data with no outliers, the mean uses all the information and is preferred.

### 3.2 · Data Cleaning & Missing Values

| Action | R code | Notes |
| --- | --- | --- |
| Detect missing values | `is.na(x)`, `sum(is.na(x))` | Counts `NA`s |
| Remove rows with any `NA` | `na.omit(df)` | Simplest, but loses data |
| Compute with `NA` removed | `mean(x, na.rm = TRUE)` | Add `na.rm = TRUE` |
| Replace `NA` with mean/median | `x[is.na(x)] <- mean(x, na.rm=TRUE)` | Imputation |

```r
library(dplyr); library(tidyr)

df <- distinct(df)                           # drop duplicates
df <- rename(df, Revenue = rev)               # rename columns
df <- filter(df, !is.na(Marks))               # filter out NA rows

long <- pivot_longer(df, cols = c("Q1","Q2"), names_to="Quarter", values_to="Sales")
wide <- pivot_wider(long, names_from = Quarter, values_from = Sales)

df <- df %>% distinct() %>% filter(!is.na(Marks)) %>% mutate(Pct = Marks/100)
```

### 3.3 · Exploratory Data Analysis (EDA) & Visualisation

#### 3.3.1 Charts in base R

| Chart | Use to show | R code |
| --- | --- | --- |
| Pie chart | Composition (% share) | `pie(table(df$Region))` |
| Bar chart | Comparison across categories | `barplot(table(df$Region))` |
| Line chart | Trend over time | `plot(x, y, type="l")` |
| Histogram | Distribution of a numeric variable | `hist(df$Marks)` |
| Box plot | 5-point summary + outliers | `boxplot(df$Marks)` |
| Scatter plot | Relationship between two numerics | `plot(df$X, df$Y)` |
| Normal Q-Q plot | Compare sample vs Normal distribution | `qqnorm(x); qqline(x)` |

#### 3.3.2 `ggplot2` — the grammar of graphics

```r
library(ggplot2)

ggplot(df, aes(x = Marks)) + geom_histogram(bins = 20, fill = "steelblue")
ggplot(df, aes(x = Region)) + geom_bar(fill = "tomato")
ggplot(df, aes(x = Year, y = Sales)) + geom_line(colour = "darkgreen")
ggplot(df, aes(x = Group, y = Marks)) + geom_boxplot(fill = "skyblue")
ggplot(df, aes(x = Height, y = Weight)) +
  geom_point(color = "purple") + geom_smooth(method = "lm", se = FALSE)
ggplot(df, aes(sample = Marks)) + stat_qq() + stat_qq_line()
```

> 💡 **Exam tip:** Be able to draw any chart in **both** base R and `ggplot2`. Base-R `hist()`/`plot()` are one-liners; `ggplot2` needs `data + aes + geom` layers.

### 3.4 · Regression Analysis

#### 3.4.1 Regression vs Correlation

|  | Correlation | Regression |
| --- | --- | --- |
| **Measures** | Strength & direction of linear relationship | Equation of the best-fit line |
| **Output** | A single number `r ∈ [−1, 1]` | An equation `Y = a + bX + ε` |
| **Symmetry** | Symmetric: `corr(X,Y) = corr(Y,X)` | Asymmetric — Y~~X ≠ X~~Y |
| **R function** | `cor(x, y)` | `lm(y ~ x)` |

#### 3.4.2 Simple Linear Regression

$$Y_i = \\beta_0 + \\beta_1 X_i + \\varepsilon_i$$

- **β₀** = intercept (Y when X = 0) · **β₁** = slope (ΔY per unit ΔX) · **εᵢ** = residual error

> **OLS** chooses β₀ and β₁ to minimise `Σ(Yᵢ − Ŷᵢ)²`. `lm()` uses OLS by default.

```r
model <- lm(Y ~ X, data = df)

summary(model)              # coefficients, R², F, p-values
coef(model); confint(model) # β's and 95% confidence intervals

newdata <- data.frame(X = c(5, 10, 15))
predict(model, newdata)

resid(model)                 # residuals (Yᵢ − Ŷᵢ)
plot(df$X, df$Y); abline(model, col = "red", lwd = 2)
```

#### 3.4.3 Multiple Regression

$$Y = \\beta_0 + \\beta_1 X_1 + \\beta_2 X_2 + \\dots + \\beta_k X_k + \\varepsilon$$

```r
model <- lm(Y ~ X1 + X2 + X3, data = df)
model <- lm(Y ~ ., data = df)          # all other columns as predictors
model <- lm(Y ~ X1 * X2, data = df)     # include interaction terms
```

#### 3.4.4 Reading the `summary()` Table

| Component | Meaning |
| --- | --- |
| Coefficients | Estimated β's |
| Std. Error | Standard error of each coefficient |
| t value | Coefficient ÷ Std. Error |
| `Pr(>\|t\|)` | p-value — significance of each predictor |
| Multiple R² | % of variation in Y explained by X's |
| Adjusted R² | R² penalised for extra predictors (preferred for multiple regression) |
| F-statistic | Overall significance of the model |

> 🧠 **Decision rule:** A predictor is **statistically significant** if `p-value < 0.05`. R prints significance stars: `*** < 0.001`, `** < 0.01`, `* < 0.05`, `. < 0.1`.

```r
library(corrplot)
M <- cor(df[, sapply(df, is.numeric)])
corrplot(M, method = "circle"); corrplot(M, method = "number")
```

### 3.5 · Assumptions of CNLRM & Diagnostic Tests

**CNLRM** = Classical Normal Linear Regression Model. For OLS estimates to be valid:

| # | Assumption | Test / Check | R function |
| --- | --- | --- | --- |
| 1 | **Linearity** — Y is linearly related to X | Scatter plot of Y vs each X | `plot(y ~ x)` |
| 2 | **Normality of residuals** — ε \~ N(0, σ²) | Histogram / Q-Q plot of residuals | `qqnorm(resid(model))`, `car::qqPlot(model)` |
| 3 | **Homoscedasticity** — constant error variance | Residuals vs Fitted plot; Breusch–Pagan | `lmtest::bptest(model)`, `car::ncvTest(model)` |
| 4 | **No autocorrelation** of residuals | ACF plot; Durbin–Watson test | `acf(resid(model))`, `lmtest::dwtest(model)` |
| 5 | **No multicollinearity** among X's | Correlation matrix, VIF | `corrplot(cor(X))`, `car::vif(model)` |
| 6 | **No endogeneity** / measurement error | Domain knowledge, theory | — |

```r
# ---- Normality ----
qqnorm(resid(model)); qqline(resid(model), col = "red")
library(car); qqPlot(model)

# ---- Multicollinearity ----
cor(df[, c("X1","X2","X3")])
library(car); vif(model)

# ---- Autocorrelation ----
acf(resid(model))
library(lmtest); dwtest(model)     # H0: no autocorrelation

# ---- Heteroscedasticity ----
plot(model, which = 1)
library(lmtest); library(car)
bptest(model); ncvTest(model)
```

> **VIF rule of thumb:** `VIF = 1` → no correlation · `VIF > 5` → moderate (worry) · `VIF > 10` → severe (action required). **Durbin–Watson:** ranges 0–4. `≈ 2` → no autocorrelation · `→ 0` → positive autocorrelation · `→ 4` → negative autocorrelation.

#### Impact of Violations & Remedies

| Violation | Effect | Remedy |
| --- | --- | --- |
| Non-linearity | Biased estimates | Transform X/Y (log, sqrt); add polynomial / interaction terms |
| Non-normal residuals | Invalid t & F tests (small samples) | Bootstrap, robust SE, or transform variables |
| Heteroscedasticity | Biased SEs → wrong p-values | Robust/White SE: `coeftest(model, vcov = vcovHC)` (`sandwich`) |
| Autocorrelation | Underestimated SEs | Newey–West SE, or fit a time-series model (ARIMA) |
| Multicollinearity | Inflated SE; unstable coefficients | Drop a correlated variable, or combine via PCA |

### 3.6 · Time Series — Basics

A **time series** is a sequence of observations recorded at regular intervals (daily, monthly, yearly…) — e.g. monthly sales, daily stock price, yearly GDP.

#### 3.6.1 Components

| Component | Meaning |
| --- | --- |
| **Trend (T)** | Long-term upward or downward movement |
| **Seasonality (S)** | Repeating pattern within a year/week/day |
| **Cyclical (C)** | Longer wave-like fluctuations, not of fixed period |
| **Irregular (I)** | Unpredictable noise |

$$\\text{Additive: } Y(t) = T(t) + S(t) + I(t) \\qquad \\text{Multiplicative: } Y(t) = T(t) \\times S(t) \\times I(t)$$

> 🧠 **Which model?** Seasonal swings growing larger over time → **multiplicative**. Staying roughly the same → **additive**.

```r
sales <- ts(df$Sales, start = c(2018, 1), frequency = 12)   # Jan 2018, monthly
plot(sales, main = "Monthly Sales", col = "blue", lwd = 2)

sales_diff <- diff(sales)                 # difference to remove trend
plot(sales_diff)

trend_model <- lm(sales ~ time(sales))     # fit a linear trend
summary(trend_model); abline(trend_model, col = "red", lwd = 2)
```

#### 3.6.4 Stationarity

A series is **stationary** if its mean, variance, and autocovariance **do not change over time** — most models (ARIMA, etc.) require this.

| Property | Stationary | Non-Stationary |
| --- | --- | --- |
| Mean | Constant over time | Trends up/down |
| Variance | Constant over time | Changes over time |
| Autocovariance | Depends only on lag, not time | Depends on time |

🧠 **Mnemonic — "M-V-A"**

**M**ean, **V**ariance, **A**utocovariance must stay constant for a series to be stationary. Check via plot/ACF, formal tests (ADF, KPSS), or transform with `diff()` / `log()`.

📘 **Unit 3 Recap**

**Flow:** Describe → Clean → Visualise → Model (`lm`) → Diagnose (CNLRM assumptions) → Act on violations → Forecast (time series). Keep this order in mind for any data project.

---

## 🧠 Mnemonics & Memory Aids

| Mnemonic | Stands for |
| --- | --- |
| **P-R-I-W** | **P**rowessIQ · **R**BI · **I**MF · **W**orld Bank (data sources) |
| **S-F-A-M-G-S** | **S**elect · **F**ilter · **A**rrange · **M**utate · **G**roup_by · **S**ummarise (`dplyr` verbs) |
| **`[ ]` / `[[ ]]` / `$`** | sub-list / element / access-by-name (list indexing) |
| **LN-HA-M-N** | **L**inearity · **N**ormality · **H**omoscedasticity · **A**utocorrelation-free · **M**ulticollinearity-free · **N**o endogeneity (CNLRM assumptions) |
| **T-S-C-I** | **T**rend · **S**easonality · **C**yclical · **I**rregular (time series components) |
| **M-V-A** | **M**ean · **V**ariance · **A**utocovariance (stationarity) |

---

## 📋 One-Page Cheat Sheet

### Most-used R functions by topic

| Topic | Key R functions |
| --- | --- |
| **I/O** | `read.csv`, `read_excel`, `write.csv`, `saveRDS` |
| **Structures** | `c`, `matrix`, `array`, `list`, `data.frame`, `factor` |
| **dplyr** | `select`, `filter`, `arrange`, `mutate`, `group_by`, `summarise`, `%>%` |
| **Stats** | `mean`, `median`, `var`, `sd`, `summary`, `cor`, `skewness` |
| **Plots** | `hist`, `boxplot`, `barplot`, `plot`, `qqnorm` |
| **ggplot2** | `ggplot`, `geom_xxx` (point, line, bar, boxplot, hist, smooth, qq) |
| **Regression** | `lm`, `summary`, `predict`, `resid`, `abline` |
| **Diagnostics** | `car::vif`, `car::qqPlot`, `lmtest::bptest`, `lmtest::dwtest`, `acf`, `corrplot` |
| **Time series** | `ts`, `diff`, `time`, `acf` |

### Quick facts

- **VIF thresholds:** `5` = worry, `10` = act
- **Durbin–Watson:** `2` = good, `0` = positive autocorrelation, `4` = negative
- **Skew sign:** Positive skew → long right tail → mean > median

---

## 🎯 Exam Strategy

| Question type | Approach |
| --- | --- |
| **Long answer** | Define → Formula → R code → Assumption/Interpretation → One-line application |
| **Short answer** | One-line definition + one function name |
| **Practical** | Always `setwd()` first → check `head()` and `str()` → `summary()` before any model |

---

## 🤝 Contributing

Found an error, an outdated function, or want to add a topic (e.g. ARIMA forecasting, GLMs)? Contributions are welcome:

1. Fork this repository
2. Create a branch (`git checkout -b topic/your-addition`)
3. Commit your changes (`git commit -m "Add: <topic>"`)
4. Open a Pull Request

---

## 📄 License

This project is licensed under the **MIT License** — feel free to fork, adapt, and use it for your own revision.

**Statistics with R · Examination-Ready Notes · v1.0**

Maintained by [**NDxGenius**](https://github.com/NishantDas0079) · ⭐ Star this repo if it helped you revise!
