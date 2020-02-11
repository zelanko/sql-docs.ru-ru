---
title: SQLSetScrollOptions (драйвер ODBC для Visual FoxPro) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 693e6e28-a845-41b1-9622-5058b0d87229
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b3746d9cea2ce5ffb7d03424d7cda4fa1889aabc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67905385"
---
# <a name="sqlsetscrolloptions-visual-foxpro-odbc-driver"></a>SQLSetScrollOptions (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  В этом разделе содержатся сведения, относящиеся к драйверу ODBC для Visual FoxPro. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: частичная  
  
 Соответствие API-интерфейса ODBC: уровень 2  
  
 Задает параметры, управляющие поведением курсоров, связанных с маркером инструкции, *хстмт*.  
  
 Драйвер ODBC для Visual FoxPro поддерживает только SQL_CONCUR_READ_ONLY; Он не поддерживает значение *фконкурренци* SQL_CONCUR_ROWVER. Драйвер преобразует SQL_KEYSET_SIZE, SQL_CURSOR_DYNAMIC и SQL_CURSOR_KEYSET_DRIVEN в SQL_SCROLL_STATIC с предупреждением ODBC_01S02.  
  
 Дополнительные сведения см. в разделе [SQLSetScrollOptions](../../odbc/reference/syntax/sqlsetscrolloptions-function.md) в *справочнике программиста по ODBC*.
