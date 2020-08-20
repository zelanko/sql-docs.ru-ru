---
description: SQLTransact (драйвер ODBC для Visual FoxPro)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1deed379c456ba2f15d30b6783c95d657e688457
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500117"
---
# <a name="sqltransact-visual-foxpro-odbc-driver"></a>SQLTransact (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  В этом разделе содержатся сведения, относящиеся к драйверу ODBC для Visual FoxPro. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: полная  
  
 Соответствие API ODBC: уровень ядра  
  
 Запрашивает операцию фиксации или отката для всех активных операций на всех дескрипторах инструкций (*хстмт*), связанных с соединением, или для всех подключений, связанных с дескриптором среды *хенв*. **SQLTransact** работает только для источников данных, являющихся [базами](../../odbc/microsoft/visual-foxpro-terminology.md)данных.  
  
 Если фиксация завершается ошибкой в ручном режиме, транзакция остается активной; можно выбрать откат транзакции или повторить операцию фиксации. Если операция фиксации завершается неудачей в автоматическом режиме транзакций, происходит автоматический откат транзакции. транзакция не может быть неактивной.  
  
 Дополнительные сведения см. в разделе [SQLTransact](../../odbc/reference/syntax/sqltransact-function.md) в *справочнике программиста по ODBC*.
