---
title: Уровни соответствия S'L (драйвер ODBC для Oracle) Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300684"
---
# <a name="sql-conformance-levels-odbc-driver-for-oracle"></a>Уровень соответствия SQL (драйвер ODBC для Oracle)
> [!IMPORTANT]  
>  Эта функция будет удалена в будущей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставленный Oracle.  
  
 Драйвер ODBC для Oracle поддерживает грамматику «Минимальный СЗЛ» и грамматику Core S'L, а также поддерживает следующие расширения ODBC в S'L:  
  
-   Данные о дате, времени и метке времени  
  
-   Левые и правые внешние соединения  
  
-   Числовые функции:  
  
    |||||  
    |-|-|-|-|  
    |Abs|Журнал|round|tan|  
    |Ceiling|Log10|second|truncate|  
    |Cos|Mod|подписывание||  
    |Exp|Pi|sin||  
    |Этаж|Power|sqrt||  
  
-   Функции для работы с датами:  
  
    |||||  
    |-|-|-|-|  
    |Курдат|Dayofweek|месячный имя|second|  
    |Куртайм|День года|minute|week|  
    |Дневное имя|Час|now|year|  
    |Деньомесячный|Месяц|квартал||  
  
-   Строковые функции:  
  
    |||||  
    |-|-|-|-|  
    |Ascii|Слева|right|ucase|  
    |CHAR|Длина|Rtrim||  
    |Concat|Ltrim|Soundex||  
    |Lcase|Replace|substring||  
  
-   Функция преобразования типа:  
  
    ||  
    |-|  
    |Convert|  
  
-   Системные функции:  
  
    ||  
    |-|  
    |Ифнулл|  
    |Пользователь|
