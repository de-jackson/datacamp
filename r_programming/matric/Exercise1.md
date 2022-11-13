# Exercise 1. What's a matrix?

In R, a matrix is a collection of elements of the same data type (numeric, character, or logical) arranged into a fixed number of rows and columns. Since you are only working with rows and columns, a matrix is called two-dimensional.

You can construct a matrix in R with the ``matrix()`` function. Consider the following example:
```
matrix(1:9, byrow = TRUE, nrow = 3)
```

In the matrix() function:

* The first argument is the collection of elements that R will arrange into the rows and columns of the matrix. Here, we use 1:9 which is a shortcut for c(1, 2, 3, 4, 5, 6, 7, 8, 9).
* The argument byrow indicates that the matrix is filled by the rows. If we want the matrix to be filled by the columns, we just place byrow = FALSE.
* The third argument nrow indicates that the matrix should have three rows.

## Instructions

Construct a matrix with 3 rows containing the numbers 1 up to 9, filled row-wise.

## Solution

```
matrix(1:9, byrow = TRUE, nrow = 3)
```

# Exercise 2. Analyze matrices, you shall

It is now time to get your hands dirty. In the following exercises you will analyze the box office numbers of the Star Wars franchise. May the force be with you!

In the editor, three vectors are defined. Each one represents the box office numbers from the first three Star Wars movies. The first element of each vector indicates the US box office revenue, the second element refers to the Non-US box office (source: Wikipedia).

In this exercise, you'll combine all these figures into a single vector. Next, you'll build a matrix from this vector.

## Instructions
* Use ``c(new_hope, empire_strikes, return_jedi)`` to combine the three vectors into one vector. Call this vector ``box_office``.
* Construct a matrix with 3 rows, where each row represents a movie. Use the ``matrix()`` function to do this. The first argument is the vector ``box_office``, containing all box office figures. Next, you'll have to specify ``nrow = 3`` and ``byrow = TRUE``. Name the resulting matrix ``star_wars_matrix``.

## Solution

```
# Box office Star Wars (in millions!)
new_hope <- c(460.998, 314.4)
empire_strikes <- c(290.475, 247.900)
return_jedi <- c(309.306, 165.8)

# Create box_office
box_office <- c(new_hope, empire_strikes, return_jedi)

# Construct star_wars_matrix
star_wars_matrix <- matrix(box_office, byrow = TRUE, nrow = 3)
```

# Exercise 3. Naming a matrix

To help you remember what is stored in ``star_wars_matrix``, you would like to add the names of the movies for the rows. Not only does this help you to read the data, but it is also useful to select certain elements from the matrix.

Similar to vectors, you can add names for the rows and the columns of a matrix
```
rownames(my_matrix) <- row_names_vector
colnames(my_matrix) <- col_names_vector
```

We went ahead and prepared two vectors for you: ``region``, and ``titles``. You will need these vectors to name the columns and rows of ``star_wars_matrix``, respectively.

## Instructions

* Use ``colnames()`` to name the columns of ``star_wars_matrix`` with the ``region`` vector.
* Use ``rownames()`` to name the rows of ``star_wars_matrix`` with the ``titles`` vector.
* Print out ``star_wars_matrix`` to see the result of your work.

## Solution

```
# Box office Star Wars (in millions!)
new_hope <- c(460.998, 314.4)
empire_strikes <- c(290.475, 247.900)
return_jedi <- c(309.306, 165.8)

# Construct matrix
star_wars_matrix <- matrix(c(new_hope, empire_strikes, return_jedi), nrow = 3, byrow = TRUE)

# Vectors region and titles, used for naming
region <- c("US", "non-US")
titles <- c("A New Hope", "The Empire Strikes Back", "Return of the Jedi")

# Name the columns with region
colnames(star_wars_matrix) <- region

# Name the rows with titles
rownames(star_wars_matrix) <- titles

# Print out star_wars_matrix
star_wars_matrix
```

# Exercise 4. Calculating the worldwide box office

The single most important thing for a movie in order to become an instant legend in Tinseltown is its worldwide box office figures.

To calculate the total box office revenue for the three Star Wars movies, you have to take the sum of the US revenue column and the non-US revenue column.

In R, the function ``rowSums()`` conveniently calculates the totals for each row of a matrix. This function creates a new vector:
```
rowSums(my_matrix)
```

## Instructions

Calculate the worldwide box office figures for the three movies and put these in the vector named worldwide_vector.

```
# Construct star_wars_matrix
box_office <- c(460.998, 314.4, 290.475, 247.900, 309.306, 165.8)
region <- c("US", "non-US")
titles <- c("A New Hope", 
                 "The Empire Strikes Back", 
                 "Return of the Jedi")
               
star_wars_matrix <- matrix(box_office, 
                      nrow = 3, byrow = TRUE,
                      dimnames = list(titles, region))

# Calculate worldwide box office figures
worldwide_vector <- 
```

## Solution

```
# Calculate worldwide box office figures
worldwide_vector <- rowSums(star_wars_matrix)
```

# Exercise 5. Adding a column for the Worldwide box office

In the previous exercise you calculated the vector that contained the worldwide box office receipt for each of the three Star Wars movies. However, this vector is not yet part of ```star_wars_matrix```.

You can add a column or multiple columns to a matrix with the ``cbind()`` function, which merges matrices and/or vectors together by column. For example:
```
big_matrix <- cbind(matrix1, matrix2, vector1 ...)
```

## Instructions

Add ``worldwide_vector`` as a new column to the ``star_wars_matrix`` and assign the result to ``all_wars_matrix``. Use the ``cbind()`` function.

## Solution

```
# Construct star_wars_matrix
box_office <- c(460.998, 314.4, 290.475, 247.900, 309.306, 165.8)
region <- c("US", "non-US")
titles <- c("A New Hope", 
            "The Empire Strikes Back", 
            "Return of the Jedi")
               
star_wars_matrix <- matrix(box_office, 
                      nrow = 3, byrow = TRUE,
                      dimnames = list(titles, region))

# The worldwide box office figures
worldwide_vector <- rowSums(star_wars_matrix)

# Bind the new variable worldwide_vector as a column to star_wars_matrix
all_wars_matrix <- cbind(star_wars_matrix, worldwide_vector)
```