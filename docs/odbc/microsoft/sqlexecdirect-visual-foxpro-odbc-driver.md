---
title: SQLExecDirect (драйвер ODBC для Visual FoxPro) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLExecDirect function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5004060f-8510-4018-87a4-d41789e69d3e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 808d7890c18839c0e9059cdc3181a4579eb2ec4f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47716042"
---
# <a name="sqlexecdirect-visual-foxpro-odbc-driver"></a>SQLExecDirect (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Этот раздел содержит сведения Visual FoxPro ODBC-драйвером. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: полный  
  
 Соответствия API ODBC: Уровень Core  
  
 Выполняет новый, [подготавливаемых инструкции SQL](../../odbc/microsoft/visual-foxpro-terminology.md). Драйвер ODBC для Visual FoxPro использует текущие значения переменных маркера параметра, если существует любые параметры в инструкции.  
  
 Чтобы создать команду пакетной службы, чтобы отправить более одной инструкции SQL, одновременно, используйте точку с запятой (;) для разделения каждой инструкции SQL в пакете.  
  
 Если на таблицу, представление или имена полей содержат пробелы, заключите имя назад кавычка метки. Например если база данных содержит таблицу с именем My таблицу и поле Мое поле, заключите каждый элемент идентификатора следующим образом:  
  
```  
SELECT `My Table`.`Field1`, `My Table`.`Field2` FROM `My Table`  
```  
  
 Дополнительные сведения см. в разделе [SQLExecDirect](../../odbc/reference/syntax/sqlexecdirect-function.md) в *Справочник по программированию ODBC*.
