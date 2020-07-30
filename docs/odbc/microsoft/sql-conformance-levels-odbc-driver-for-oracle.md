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
ms.openlocfilehash: 969296e377d398615ad95cf1337c3f9f97d5eb5c
ms.sourcegitcommit: 99f61724de5edf6640efd99916d464172eb23f92
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87363404"
---
# <a name="sql-conformance-levels-odbc-driver-for-oracle"></a>Уровень соответствия SQL (драйвер ODBC для Oracle)
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемый Oracle.  
  
 Драйвер ODBC для Oracle поддерживает минимальную грамматику SQL и основную грамматику SQL, а также поддерживает следующие расширения ODBC для SQL:  
  
-   Данные даты, времени и отметок времени  
  
-   Левые и правые внешние объединения  
  
-   Числовые функции:  

    :::row:::
        :::column:::
            Abs  
            Ceiling  
            Cos  
            Exp  
            Этаж  
        :::column-end:::
        :::column:::
            Журнал  
            Log10  
            Mod  
            Pi  
            Питание  
        :::column-end:::
        :::column:::
            round  
            second  
            подписывание  
            sin  
            sqrt  
        :::column-end:::
        :::column:::
            tan  
            truncate  
        :::column-end:::
    :::row-end:::
    
-   Функции для работы с датами:  

    :::row:::
        :::column:::
            CURDATE  
            куртиме  
            дайнаме  
            DayOfMonth  
        :::column-end:::
        :::column:::
            DayOfWeek  
            День года  
            Час  
            Месяц  
        :::column-end:::
        :::column:::
            MonthName  
            minute  
            now  
            квартал  
        :::column-end:::
        :::column:::
            second  
            week  
            year  
        :::column-end:::
    :::row-end:::

-   Строковые функции:  

    :::row:::
        :::column:::
            Ascii  
            Char  
            Concat  
            Lcase  
        :::column-end:::
        :::column:::
            Левый  
            Длина  
            Ltrim  
            Заменить  
        :::column-end:::
        :::column:::
            right  
            RTRIM  
            SOUNDEX  
            substring  
        :::column-end:::
        :::column:::
            укасе  
        :::column-end:::
    :::row-end:::

-   Функция преобразования типа:  

    Convert  

-   Системные функции:  
  
    ифнулл  
    Пользователь
