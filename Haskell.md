

## ⚙️ GHCi Essentials

### `:l file_name`
Loads a Haskell file into GHCi for testing.

```haskell
:l Say.hs
```

### `:r`
Reloads the currently loaded modules after saving edits.

### `:quit`
Exits GHCi.

```haskell
:quit
```

### 🗂️ File Structure
Make sure your files are in the same directory before loading them in GHCi:

```
C:\Users\<you>\Documents\HaskellProjects\
│
├── Say.hs
├── Hello.hs
└── ChristmasTree.hs
```

Then in GHCi:
```haskell
:l Hello.hs
```

---

## 🧩 Normal Order Evaluation

### Concept
In **normal order evaluation** (also called *outermost-first*), Haskell:

- expands function definitions **before** doing inner arithmetic,
- only evaluates expressions when it **really needs to** (lazy evaluation).

Instead of working **inside-out** like in math, Haskell works **top-down**:

> expand → substitute → reduce when necessary

### Example
```haskell
double :: Integer -> Integer
double x = incr (incr 0)
  where incr y = x + y
```

Evaluating `double 5` in normal order:

1. Expand `incr (incr 0)`
2. Substitute the definition of `incr`
3. Delay numeric computation until needed  

This shows Haskell’s **lazy evaluation** and **normal-order** expansion.

---

## 🧮 Exercise 5 — Function and Evaluation Order

### Code
```haskell
double :: Integer -> Integer
double x = incr (incr 0)
  where
    incr y = x + y
```

### Explanation
- `incr` is a local helper function that adds `x` to another number.
- The expression `incr (incr 0)` applies it twice.
- **Normal-order evaluation** expands outermost expressions first, delaying computation.
- Haskell’s laziness means it doesn’t compute inner values until they are required.

---

## 🧠 Exercise 6 — Database.hs

The exercise focused on manipulating a list of students represented as tuples:
```haskell
type Person = (String, Integer, String)
```

### 1. Increment the age of all students by two
```haskell
increaseAge :: Person -> Person
increaseAge (nm, ag, c) = (nm, ag + 1, c)

incAllByTwo :: [Person]
incAllByTwo = map (increaseAge . increaseAge) students
```

### 2. Promote all students by prefixing `"dr."`
```haskell
promoteAll :: [Person]
promoteAll = map promote students
  where
    promote (nm, ag, c) = ("dr. " ++ nm, ag, c)
```

### 3. Find all students named *Frits*
```haskell
findFrits :: [Person]
findFrits = filter (\p -> name p == "Frits") students
```

### 4. Find students in their twenties
```haskell
inTwenties :: [Person]
inTwenties = filter (\p -> let a = age p in a >= 20 && a <= 29) students
```

### 5. Compute the average age
```haskell
averageAge :: Integer
averageAge = total `div` count
  where
    total = sum (map age students)
    count = toInteger (length students)
```

### 6. Promote students whose favourite course is *Functional Programming*
```haskell
promoteFP :: [Person]
promoteFP = map promoteIfFP students
  where
    promoteIfFP (nm, ag, c)
      | c == "Functional Programming" = ("dr. " ++ nm, ag, c)
      | otherwise                     = (nm, ag, c)
```

---

## 🔢 Exercise 7 — Say.hs (Numbers to Words)

### 🎯 Goal
Convert integers `< 1,000,000` into English words.

### 💡 Logic
The logic divides numbers into four ranges:

| Range | Helper Function | Example |
|--------|-----------------|----------|
| 0–19 | `small` | `say 13 → "thirteen"` |
| 20–99 | `tens` | `say 42 → "forty two"` |
| 100–999 | `hundreds` | `say 305 → "three hundred five"` |
| 1,000–999,999 | `thousands` | `say 123456 → "one hundred twenty three thousand four hundred fifty six"` |

---

### ✅ Final Code
```haskell
module Say where

say :: Integer -> String
say n
  | n < 0        = error "negative numbers not supported"
  | n < 20       = small n
  | n < 100      = tens n
  | n < 1000     = hundreds n
  | n < 1000000  = thousands n
  | otherwise    = error "number too large"
```

*(Code continues with `small`, `tens`, `hundreds`, and `thousands` functions as explained above)*

---

### 🧩 Optional / Extra Task — Hello.hs Integration

Goal: modify `Hello.hs` to reuse the `say` function instead of `show`.

```haskell
module Main where

import Say

lyrics :: Integer -> String
lyrics 0 = "no more seats in the lecture hall!\n"
lyrics n =
  say n ++ " seats in the lecture hall!\n" ++
  "A student walks in, and sits down, now there are\n" ++
  lyrics (n - 1)

main :: IO ()
main = putStr (lyrics 5)
```

**Explanation:**  
By importing `Say`, I reused the existing `say` function without copy–pasting it.  
This keeps the program modular and prints numbers as natural language (e.g., *five*, *four*, *three*).

---

## 🎄 Exercise 8 — Christmas Tree

### 💭 Thought Process
1. **Visualize** the shape (triangles stacked together).
2. **Find patterns** in one triangle:
   - Stars = `2 * i - 1`
   - Spaces = `n - i`
3. **Create one line** using `replicate`.
4. **Combine lines** into one triangle.
5. **Stack triangles** to build the full tree.

### ✅ Code
```haskell
line :: Integer -> Integer -> String
line n i =
  let spaces = n - i
      stars  = 2 * i - 1
  in replicate (fromInteger spaces) ' '
     ++ replicate (fromInteger stars) '*'
     ++ "\n"

triangle :: Integer -> String
triangle n = concat [ line n i | i <- [1..n] ]

christmasTree :: Integer -> String
christmasTree n = concat [ triangle k | k <- [1..n] ]
```

---

## 🔑 Key Haskell Concepts Recap

| Concept | Description |
|----------|--------------|
| **Normal Order Evaluation** | Expands outermost expressions before inner ones (lazy). |
| **Lazy Evaluation** | Values are computed only when needed. |
| **Guards** | `| condition = result` used for readable branching. |
| **Recursion** | Functions calling themselves on smaller inputs. |
| **let ... in ...** | Defines local variables within expressions. |
| **Modules** | Reusable files imported using `import`. |
| **Pure vs IO** | Pure = returns value; IO = interacts with the outside world. |



