## Описание машины

Машина Тьюринга описывается 8 параметрами.

1. Множество символов, из которых может состоять входной слово (далее алфавит)
2. Множество символов, из которые не встречаются во входных словах, но которые может печатать машина(в дополнение к символам из алфавита, далее называется как 'расширение алфавита')
3. Пробельный символ, причём он должен лежать в расширении
4. Множество состояний детерменированного управляющего автомата (далее States).
5. Начальное состояние
6. Допускающие состояния
7. Отвергающие состояния
8. Функция перехода

## Ключевые слова

* Alphabet
* ExtraAlphabet
* States
* Function
* Success
* Fail
* Start
* Blank
* left
* right
* stay


## Комментарии

Коментарии реализованы как в C++, двух типов: однострочные, после ```//```, и многострочные, между ```/* */```. Многострочный комментарий может содержать подстроку `/*`, но не может содержать подстроку `*/`.

Корректные комментарии:

```
/* Comment */
/* Comments with '/*' */
```

Некорректный комментарий:

`/* Comment with '*/' */`


## Идентефикаторы

Идентификатор сивола - строка из латинских букв(строчных и заглавных) и цифр, начинающаяся со строчного латинского символа. Исключения: `left` `right` и `stay`, они не являются идентификаторами символов.

Идентификатор состояния - строка из латинских букв(строчных и заглавных) и цифр, начинающаяся с заглавного латинского символа.

Примеры:

`char char1 abacaba` - символы

`State1 Bad Good` - состояния

## Переходы

Описания переход начинается с открывающей круглой скобки. Далее идут идентификаторы состояния и символа, разделённые пробельными символами, далее идёт "оператор" ```->```, после которого идут состояния, символ, одно из трёх ключевых слов: `left`, ```right``` или ```stay```, описывающее движение пишушей головки, и закрывающая круглая скобка.

Примеры:

`(State1 char1 -> State2 char2 right)`

## Последовательности идентификаторов

Последовательность начинается с открывающей фигурной скобки ```{```. Далее идут идентификаторы одного типа(символ, состояние, переход), разделённые пробельными символами и/или переносами строк. Завершается последовательность закрывающей фигурной скобкой. Длина последовательности - количество идентификаторов, входящих в неё.

## Описание алфавитов и состояний

Алфавит и расширение алфавита - последовательности сиволов, перед открывающей фигурной скобкой которых стоят ключевые слова `Alphabet` и `ExtraAlphabet` соответсвенно(без пробелов).

Аналогично состояния - последовательность состояний, перед которой стоит ключевое слово `States`.

Функция перехода - последовательность переходов, перед которой стоит ключевое слово `Function`.

Пробельный символ - последовательность символов длины 1, перед которой стоит ключевое слово `Blank`, причём, этот символ также должен входить в расширение алфавита.

Стартовое состояние - последовательность состояний длины 1, перед которой стоит ключевой слово `Start`, причём состояние входит в множество состояний.

Отвергающие состояния - последовательность состояний, перед которой стоит ключевое слово `Fail`. Состояния также должны входить в States.

Аналогично отвергающим описываются допускающие состояния (вместо ключевого слова `Fail` слово `Success`).

## Примеры

Примеры находятся в директории `Description/examples`

`incr.tmd`

```
// Add 1 to number in binary system

Alphabet{zero one}

ExtraAlphabet{blank}

States{S R Y N}

Blank{blank}

Start{S}

Fail{N}

Success{Y}

Function{
    (S zero /*such comments can be everywhere*/ -> R one stay)
    (S one -> S zero right)
    (S blank -> R blank left)
    (R zero -> R zero left)
    (R one -> R one left)
    (R blank -> Y blank right)
}
```

`comments.tmd`

```
// machiene does nothing, just comments demo

States{ // can be defined before Alphabet
Alphabet // correct  
Function // correct
S Y N
Y1 Y2 N1 N2
S // correct, but analyzer warns
}

Start{S /*F*/} // error if uncomment F
/* Blank{} */ // error if uncomment

Alphabet{
    c
    a b
    c // correct, but warn
    char1 /* another comment */ char2
}

ExtraAlphabet{e1 e2 blank}

Blank{blank}

Start{S}
Fail{N N1 N2}
Success{Y Y1 Y2 S}
Function{
    (/* ok */ S /*ok*/ c /*ok*/ -> /*ok*/ S /* ok */ c /* ok */ stay /* ok */) 
} // Function
```

`palindrom.tmd`
```
//check if binary word is a palindrom

Alphabet{one zero}
ExtraAlphabet{blank}
Blank{blank}
States{S F0 F1 B0 B1 R Y N}
Start{S}
Success{Y}
Fail{N}
Function{
    (S zero -> F0 blank right)
    (F0 zero -> F0 zero right)
    (F1 zero -> F1 zero right)
    (B0 zero -> R blank left)
    (B1 zero -> N zero stay)
    (R zero -> R zero left)

    (S one -> F1 blank right)
    (F0 one -> F0 one right)
    (F1 one -> F1 one right)
    (B0 one -> N one stay)
    (B1 one -> R blank left)
    (R one -> R one left)

    (S blank -> Y blank stay)
    (F0 blank -> B0 blank left)
    (F1 blank -> B1 blank left)
    (B0 blank -> Y blank stay)
    (B1 blank -> Y blank stay)
    (R blank -> S blank right)
    // Note, that there are no (Y char -> ...) or (N char -> ...) 
}
```
