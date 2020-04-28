---
title: Уровни соответствия SQL (драйвер ODBC для Oracle) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- conformance levels [ODBC], SQL
- SQL conformance levels [ODBC]
- ODBC driver for Oracle [ODBC], conformance levels
ms.assetid: 077a6c6a-2c57-42c9-a4fd-4cf0e65cf7e2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e283bbc13f0d0dda055b047b027f7b9816502df5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300684"
---
# <a name="sql-conformance-levels-odbc-driver-for-oracle"></a>Уровень соответствия SQL (драйвер ODBC для Oracle)
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемый Oracle.  
  
 Драйвер ODBC для Oracle поддерживает минимальную грамматику SQL и основную грамматику SQL, а также поддерживает следующие расширения ODBC для SQL:  
  
-   Данные даты, времени и отметок времени  
  
-   Левые и правые внешние объединения  
  
-   Числовые функции:  
  
    |||||  
    |-|-|-|-|  
    |Abs|Журнал|round|tan|  
    |Ceiling|Log10|second|truncate|  
    |Cos|Mod|подписывание||  
    |Exp|Pi|sin||  
    |Этаж|Мощный|sqrt||  
  
-   Функции для работы с датами:  
  
    |||||  
    |-|-|-|-|  
    |CURDATE|DayOfWeek|MonthName|second|  
    |куртиме|День года|minute|week|  
    |дайнаме|Час|now|year|  
    |DayOfMonth|Месяц|квартал||  
  
-   Строковые функции:  
  
    |||||  
    |-|-|-|-|  
    |Ascii|Слева|right|укасе|  
    |Char|Длина|RTRIM||  
    |Concat|Ltrim|SOUNDEX||  
    |Lcase|Replace|substring||  
  
-   Функция преобразования типа:  
  
    ||  
    |-|  
    |Convert|  
  
-   Системные функции:  
  
    ||  
    |-|  
    |ифнулл|  
    |User (Пользователь)|
