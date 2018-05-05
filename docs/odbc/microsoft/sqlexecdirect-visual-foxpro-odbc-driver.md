---
title: SQLExecDirect (драйвер ODBC для Visual FoxPro) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLExecDirect function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5004060f-8510-4018-87a4-d41789e69d3e
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b2089fb2289110ba175e4446f372c8a968b82a2e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
