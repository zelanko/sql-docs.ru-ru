---
title: SQLTransact (драйвер ODBC для Visual FoxPro) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLTransact function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 92cf86c0-f7a8-44d7-b59f-a1342677440b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e554a8669b6e6e95e234a5b939477a8bb2f7b8cc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67948868"
---
# <a name="sqltransact-visual-foxpro-odbc-driver"></a>SQLTransact (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  В этом разделе содержатся сведения, относящиеся к драйверу ODBC для Visual FoxPro. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: полная  
  
 Соответствие API ODBC: уровень ядра  
  
 Запрашивает операцию фиксации или отката для всех активных операций на всех дескрипторах инструкций (*хстмт*), связанных с соединением, или для всех подключений, связанных с дескриптором среды *хенв*. **SQLTransact** работает только для источников данных, являющихся [базами](../../odbc/microsoft/visual-foxpro-terminology.md)данных.  
  
 Если фиксация завершается ошибкой в ручном режиме, транзакция остается активной; можно выбрать откат транзакции или повторить операцию фиксации. Если операция фиксации завершается неудачей в автоматическом режиме транзакций, происходит автоматический откат транзакции. транзакция не может быть неактивной.  
  
 Дополнительные сведения см. в разделе [SQLTransact](../../odbc/reference/syntax/sqltransact-function.md) в *справочнике программиста по ODBC*.
