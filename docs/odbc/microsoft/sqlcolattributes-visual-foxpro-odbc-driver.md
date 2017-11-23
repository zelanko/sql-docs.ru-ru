---
title: "SQLColAttributes (драйвер ODBC для Visual FoxPro) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SQLColAttribute function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: d403dfa0-c26d-47d4-91d9-2f29aa387399
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 750f95ef793d36daca117817d81f9136ef016a55
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="sqlcolattributes-visual-foxpro-odbc-driver"></a>SQLColAttributes (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Этот раздел содержит сведения по Visual FoxPro ODBC драйвера. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: полный  
  
 Соответствия ODBC API: Уровень Core  
  
 Возвращает сведения о дескрипторе для столбца в результирующем наборе. Сведения о дескрипторе возвращается как символьная строка, зависящие от дескриптора 32-разрядное значение или является целым числом.  
  
> [!NOTE]  
>  **SQLColAttributes** не может использоваться для возврата сведений о закладки столбца (0).  
  
 Драйвер ODBC для Visual FoxPro поддерживает все *fDescType* значения. В следующей таблице представлены комментарии на реализацию драйвера выбранных значений.  
  
|*fDescType*|Комментарий|  
|-----------------|-------------|  
|SQL_COLUMN_AUTO_INCREMENT|Возвращает значение FALSE: Visual FoxPro не имеет счетчик полей.|  
|SQL_COLUMN_CASE_SENSITIVE|Всегда возвращает значение TRUE, если столбец имеет тип символа.|  
|SQL_COLUMN_LABEL|Возвращает имя столбца, который возвращается методом SQL_COLUMN_NAME также.|  
|SQL_COLUMN_MONEY|Возвращает значение TRUE, если столбец имеет тип валюты (представленным «Y» на языке Visual FoxPro).|  
|SQL_COLUMN_OWNER_NAME|Всегда возвращает пустую строку.|  
|SQL_COLUMN_QUALIFIER_NAME|Всегда возвращает пустую строку.|  
|SQL_COLUMN_SEARCHABLE|Возвращает SQL_UNSEARCHABLE для столбцов типа Общие; Эти столбцы не может использоваться в предложении WHERE.<br /><br /> Возвращает SQL_SEARCHABLE для столбцов типа символа или Memo с NOCPTRANS не задано; Эти столбцы могут использоваться в предложении WHERE с любым оператором сравнения.<br /><br /> Возвращает SQL_ALL_EXCEPT_LIKE для всех других типов столбцов; Эти столбцы могут использоваться в предложении WHERE, со всеми операторами сравнения, за исключением LIKE.|  
|SQL_COLUMN_TABLE_NAME|Всегда возвращает пустую строку.|  
  
 Дополнительные сведения см. в разделе [SQLColAttributes](../../odbc/reference/syntax/sqlcolattributes-function.md) в *справочнике программиста ODBC*.
