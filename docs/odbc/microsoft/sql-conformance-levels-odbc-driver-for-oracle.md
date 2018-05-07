---
title: Уровни согласованности SQL (драйвер ODBC для Oracle) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- conformance levels [ODBC], SQL
- SQL conformance levels [ODBC]
- ODBC driver for Oracle [ODBC], conformance levels
ms.assetid: 077a6c6a-2c57-42c9-a4fd-4cf0e65cf7e2
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6124577353292209f2bcbd2ca35b6b33add34ca6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sql-conformance-levels-odbc-driver-for-oracle"></a>Уровни согласованности SQL (драйвер ODBC для Oracle)
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 Драйвер ODBC для Oracle поддерживает минимальную SQL-грамматику и грамматику SQL ядра и также поддерживает следующие расширения ODBC SQL:  
  
-   Данные даты, времени и отметок времени  
  
-   Слева и правые внешние соединения  
  
-   Числовые функции:  
  
    |||||  
    |-|-|-|-|  
    |Abs|Журнал|round|tan|  
    |Функция CEILING|Log10|second|truncate|  
    |Cos|Mod|Вход||  
    |Exp|PI|sin||  
    |функция FLOOR|Power|функция SQRT||  
  
-   Функции даты:  
  
    |||||  
    |-|-|-|-|  
    |Функция Curdate|DayOfWeek|функция MonthName|second|  
    |Curtime|День года|minute|week|  
    |Dayname|Час|Теперь|year|  
    |день месяца|Месяц|квартал||  
  
-   Строковые функции:  
  
    |||||  
    |-|-|-|-|  
    |ASCII|Слева|Правильно|UCase|  
    |CHAR|Длина|RTRIM||  
    |Concat|Ltrim|функция SOUNDEX||  
    |Lcase|Заменить|substring||  
  
-   Функция преобразования типа:  
  
    ||  
    |-|  
    |Преобразовать|  
  
-   Системные функции:  
  
    ||  
    |-|  
    |Ifnull|  
    |Пользователь|
