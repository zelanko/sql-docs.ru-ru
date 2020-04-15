---
title: S'LColAttributes (Визуальный водитель FoxPro ODBC) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLColAttribute function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: d403dfa0-c26d-47d4-91d9-2f29aa387399
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9508fa7b9ada8273e1250d7584e577892acf5c51
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307915"
---
# <a name="sqlcolattributes-visual-foxpro-odbc-driver"></a>SQLColAttributes (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Эта тема содержит Visual FoxPro ODBC Драйвер-специфической информации. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
 Поддержка: Полная  
  
 Соответствие ODBC API: базовый уровень  
  
 Возвращает информацию о дескрипторе для столбца в наборе результатов. Информация о дескрипторе возвращается в виде строки символов, 32-битного значения, зависящей от дескриптора, или в целых значениях.  
  
> [!NOTE]  
>  Для возврата информации о столбце закладки (колонка 0) **нельзя** использовать колонку закладок.  
  
 Визуальный драйвер FoxPro ODBC поддерживает все значения *fDescType.* В следующей таблице содержатся комментарии по реализации драйвером выбранных значений.  
  
|*fDescType*|Комментарий|  
|-----------------|-------------|  
|SQL_COLUMN_AUTO_INCREMENT|Возвращает FALSE: Visual FoxPro не имеет встречных полей.|  
|SQL_COLUMN_CASE_SENSITIVE|Всегда возвращает СЯП, если тип столбца является характером.|  
|SQL_COLUMN_LABEL|Возвращает имя столбца, которое также возвращается SQL_COLUMN_NAME.|  
|SQL_COLUMN_MONEY|Возвращает TRUE, если тип столбца является валютой (представлен "Y" на языке Visual FoxPro).|  
|SQL_COLUMN_OWNER_NAME|Всегда возвращает пустую строку.|  
|SQL_COLUMN_QUALIFIER_NAME|Всегда возвращает пустую строку.|  
|SQL_COLUMN_SEARCHABLE|Возвраты SQL_UNSEARCHABLE для столбцов типа General; эти столбцы не могут быть использованы в пункте WHERE.<br /><br /> Возвращает SQL_SEARCHABLE для столбцов типа Характер или памятка с NOCPTRANS не установлен; эти столбцы могут быть использованы в пункте WHERE с любым оператором сравнения.<br /><br /> Возвраты SQL_ALL_EXCEPT_LIKE для всех других типов столбцов; эти столбцы могут быть использованы в пункте WHERE со всеми операторами сравнения, за исключением LIKE.|  
|SQL_COLUMN_TABLE_NAME|Всегда возвращает пустую строку.|  
  
 Для получения более подробной информации, *ODBC Programmer's Reference* [см.](../../odbc/reference/syntax/sqlcolattributes-function.md)
