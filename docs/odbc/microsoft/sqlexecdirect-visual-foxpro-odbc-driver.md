---
title: "SQLExecDirect (драйвер ODBC для Visual FoxPro) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLExecDirect function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5004060f-8510-4018-87a4-d41789e69d3e
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3edf8a3bd785d3440af3347d457dd5078e289638
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlexecdirect-visual-foxpro-odbc-driver"></a>SQLExecDirect (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Этот раздел содержит сведения по Visual FoxPro ODBC драйвера. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: полный  
  
 Соответствия ODBC API: Уровень Core  
  
 Выполняется новая [доступный для подготовки инструкции SQL](../../odbc/microsoft/visual-foxpro-terminology.md). Драйвер ODBC для Visual FoxPro использует текущие значения переменных маркера параметра, если существует параметров в инструкции.  
  
 Чтобы создать команду пакета, чтобы отправить несколько инструкций SQL, одновременно, используйте точку с запятой (;) для разделения каждая инструкция SQL в пакете.  
  
 Если на таблицу, представление или имена полей содержат пробелы, заключите имена кавычка после метки. Например если база данных содержит таблицу с именем My таблицу и поле Мое поле, заключите каждый элемент идентификатора следующим образом:  
  
```  
SELECT `My Table`.`Field1`, `My Table`.`Field2` FROM `My Table`  
```  
  
 Дополнительные сведения см. в разделе [SQLExecDirect](../../odbc/reference/syntax/sqlexecdirect-function.md) в *справочнике программиста ODBC*.
