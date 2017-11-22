---
title: "SQLGetStmtOption (драйвер ODBC для Visual FoxPro) | Документы Microsoft"
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
helpviewer_keywords: SQLGetStmtOption function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 984a8b1d-f12c-420c-8be4-f555114c764b
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f74b2642ccb5c8b2cae920bcda28561c33e3ff27
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="sqlgetstmtoption-visual-foxpro-odbc-driver"></a>SQLGetStmtOption (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Этот раздел содержит сведения по Visual FoxPro ODBC драйвера. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: полный  
  
 Соответствия ODBC API: Один уровень  
  
 Возвращает текущее значение параметра инструкции.  
  
|*FOption*|Возвращает|  
|---------------|-------------|  
|SQL_GET_BOOKMARK|32-разрядное целое число, — это закладка для номер текущей записи|  
|SQL_ROW_NUMBER|установите 32-разрядное целое число, указывающее позицию текущей строки в результат|  
|SQL_TRANSLATE_DLL|Ошибка: «драйвер не поддерживает»|  
  
 Драйвер ODBC для Visual FoxPro имеет преобразование библиотеки DLL.  
  
 Дополнительные сведения см. в разделе [SQLGetStmtOption](../../odbc/reference/syntax/sqlgetstmtoption-function.md) в *справочнике программиста ODBC*.
