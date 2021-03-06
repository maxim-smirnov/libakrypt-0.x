# Перечень изменений

## Изменения в версии 0.6.5

 - Для функции ak_buffer_to_hexstr добавлен второй аргумент, управляющий порядком вывода байт
   (по аналогии с ak_ptr_to_hexstr)
 - Прогон санитайзера помог убрать некоторые проблемы с переполнением статических переменных
 - В процедуру сборки добавлен тест для проверки наличия операции умножения pcmulqdq
 - Отлажены и добавлены алгоритмы умножения элементов в полях Галуа большой размерности
   (необходимо для быстрой реализации российского aead-режима)
 - Сделана реализация режима шифрования с одновременной выработкой имитовставки
   (режим MGM), а таже набор тестов для проверки корректности реализации
 - Проведена успешная сборка и запуск консольного тестового приложения под Sailfish OS (arm32v7)


## Изменения в версии 0.6.4

 - Изменено поведение функции finalize() для контекстов бесключевого хеширования
   (теперь вызов функции не изменяет внутреннее состояние контекста, что позволяет
    после финализации продолжать далее обновлять состояния с помощью вызова update() )
 - Исправлен баг со значением контрольной суммы ключа при повторном использовании
   контекста секретного ключа (функция ak_skey_set_icode_xor())
 - Изменен механизм наименования примеров.
 - Добавлена цель make test для cmake. В батарею тестов включено тестирование
   арифметики больших чисел, а также все примеры с использованием внутреннего интерфейса.
 - Проведена первая успешная сборка библиотеки под MacOS.
 - Предпринята первая попытка привести документацию в порядок.
 - Изменен перечень тестовых примеров.


## Изменения в версии 0.6.3

 - Возвращена арифметика больших чисел и вычисления в группе точек
   эллиптической кривой (в короткой форме Вейерштрасса).
 - Исправлены ошибки в тестах проверки корректности реализации
   арифметических вычислений.
 - Тестирование вычислений на эллиптических кривых в короткой форме Вейерштрасса
   добавлено в вызов функции ak_libakrypt_create().
 - Уточнены поля структуры ak_oid_engine и работа функций, использующих данную структуру.
 - Предварительное описание функции проверки параметров контекста секретного ключа
   ak_skey_check() вынесено в заголовочный файл ak_skey.h
 - Подправлена реализация функции ak_wpoint_pow() - реализована лесенка Монтгомери,
   а также исправлен баг c изменением значений аргументов функции.
 - Реализованы функции создания контекстов секретного и открытого ключей
   электронной подписи, а также функции вычисления и проверки электронной подписи.
 - В вызов функции ak_libakrypt_create() добавлены тесты корректной работы
   для алгоритмов электронной подписи (выработка и проверка).


## Изменения в версии 0.6.2

 - Возвращена реализация алгоритма блочного шифрования Кузнечик.
   Теперь как с поддержкой 64-х битных операндов, так и 128-ми битных.
 - Изменена реализация функций выработки имитовставки, сделана единая структура
   для доступа к трем типам алгоритмов - hmac, на основе блочных шифров
   и электронной подписи.
 - Реализован механизм генерации секретных ключей для алгоритмов выработки имитовставки.
 - Проведена первая успешная сборка библиотеки под FreeBSD.


## Изменения в версии 0.6.1

 - Минимизирован перечень необходимых функций.
 - Протестирована сборка библиотеки для компиляторов gcc, clang, tcc, mingw и msvc


Версия 0.6 появилась в связи с изменением интерфейса пользовательских функций,
предназначенных для вычисления имитовставок и кодов целостности.
