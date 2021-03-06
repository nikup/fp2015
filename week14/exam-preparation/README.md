# Подготовка за второ конторлно

## Задача 1 

Напишете функцията `mergeAndSortDigits :: Int -> Int -> Int`, която взима две цели числа, `X` и `Y` и връща ново число `N`, такова че:

* То се състои от цифрите на `X` и `Y`, без повторения в цифрите (само уникални цифри)
* Цифрите на `N` трябва да са сортирани във възходящ или низходящ ред, спрямо следното условие:
* Ако `sumDigits X <= sumDigits Y`, то трябва да са във възходящ ред
* Otherwise - във низходящ ред.
* Ако в някое от числата `X` или `Y` се среща нула, тя се премахва и изобщо не участва в схемата!

Примери:

```haskell
> mergeAndSortDigits 11 111
1 -- Защото искаме резултатното число да няма повтарящи се цифри.
> mergeAndSortDigits 123 456
123456 -- сумата на 1+2+3 е <= от сумата на 4+5+6
> mergeAndSortDigits 456 123
654321 -- тук имаме обратния вариант
```

## Задача 2

Напишете функция `balance :: Int -> [Int] -> Int`, която взима число `N`, списък с числа `numbers` и връща **минималния брой** на премахванията на елементи от списъка, такъв че сумата на числата в списъка да стане `<= N` или пък списъкът не остане празен.

`N` няма да бъде отрицателно число.

Примери:

```haskell
balance 50 [45, 5, 100]
1 -- Трябва да махнем 100, за да получим сума 50
balance 3 [2, 10, 15]
2 -- Тук трябва да махнем 10 и 15
balance 1 [5, 10, 15, 36]
4 -- Тук трябва да махнем всички елементи от списъка
```

## Задача 3

Напишете функция `repeater :: String -> (Int -> String -> String)`, която взима низ `str` и връща функция на два аргумента.

Когато извикате върнатата функция с число `count` и низ `glue`, се получава низ, който представлява `count`- кратно повтаряне на низа `str`, при което между всеки две съседни повторения на `str` стои низът `glue`.

Примери:

```haskell
> let haskellRepeat = repeater "I love Haskell"
> haskellRepeat 3 " "
"I love Haskell I love Haskell I love Haskell"
> repeater "Quack" 5 "!"
"Quack!Quack!Quack!Quack!Quack"
```

## Задача 4

Да се дефинира тип `Order`, който моделира поръчка на продукт. 

Типът да има `2` `value` констуктора - `Online Float Int Int` (цена на стоката, номер на поръчката и брой часове до доставка) и `Offline Float` (цена на стоката)

- да се дефинира функция `isOnline :: Order -> Bool`, която връща дали дадена поръчка е направена онлайн.
- да се дефинира функция `timeUntilReceiving :: Order -> Int`, която връща след колко часа поръчката ще бъде получена
- да се дефинира функция `totalPrice :: [Order] -> Float`, която връща общата цена на списък от поръчки
- да се дефинира функция `onlineOrders :: [Order] -> Int`, която връща броят на онлайн поръчки в даден списък.
- да се дефинира функция `isExpensive :: Order -> Bool`, която проверява дали цената на поръчаната стока надвишава 100.
- да се направи `Order` инстанция на `Show` и `Eq`.

## Задачa 5

Имаме следното представяне на двоично дърво:

```haskell
data Tree a = Empty | Node a (Tree a) (Tree a)
```

Казваме, че едно двоично дърво е конус, ако сумата на елементите на всяко ниво в дървото е по-голяма от сумата на елементите на предишното ниво.

a) Да се дефинира функция `levelSum :: Int -> Tree Int -> Int`, която намира сумата на елементите на ниво *level* в дървото *tree*.

b) Да се дефинира функция `cone :: Tree Int -> Bool`, която проверява дали дървото *tree* е конус.

Приемаме, че коренът на дървото е на ниво 1. Да се използва следната дефиниция на двоично дърво:

**Примери:**

```haskell
levelSum Empty 0 -> 0
levelSum (Node 1 (Node 2 Empty Empty) (Node 3 Empty Empty)) 0 -> 1
levelSum (Node 1 (Node 2 Empty Empty) (Node 3 Empty Empty)) 1 -> 5
levelSum (Node 1 (Node 2 Empty Empty) (Node 3 Empty Empty)) 2 -> 0

cone Empty -> True
cone (Node 1 (Node 2 Empty Empty) (Node 3 Empty Empty)) -> True
cone (Node 5 (Node 2 Empty Empty) (Node 3 Empty Empty)) -> False
cone (Node 1 (Node 2 Empty Empty) (Node 3 Empty (Node 4 Empty Empty))) -> False
```
