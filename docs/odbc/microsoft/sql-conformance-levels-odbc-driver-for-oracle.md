---
description: Уровень соответствия SQL (драйвер ODBC для Oracle)
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
ms.openlocfilehash: 78e98aed952ef8b15a4654be9f82e355d1b4177b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483427"
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
