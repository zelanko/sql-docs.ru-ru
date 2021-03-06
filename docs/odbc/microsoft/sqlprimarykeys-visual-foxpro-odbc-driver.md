---
description: SQLPrimaryKeys (драйвер ODBC для Visual FoxPro)
title: SQLPrimaryKeys (драйвер ODBC для Visual FoxPro) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLPrimaryKeys function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 8dbe2903-efdc-45e0-a079-9e357c5fd81b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 96b333e10c7000a8a44e957e33d0c84a3b004f43
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483347"
---
# <a name="sqlprimarykeys-visual-foxpro-odbc-driver"></a>SQLPrimaryKeys (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  В этом разделе содержатся сведения, относящиеся к драйверу ODBC для Visual FoxPro. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: полная  
  
 Соответствие API-интерфейса ODBC: уровень 2  
  
 Возвращает имена столбцов, которые составляют первичный ключ для таблицы. Реализация **SQLPrimaryKeys** драйвера ODBC для Visual FoxPro ведет себя следующим образом:  
  
-   Игнорирует аргументы *сзтаблеовнер* и *кбтаблеовнер* .  
  
-   Работает только с источниками данных, которые являются [базами](../../odbc/microsoft/visual-foxpro-terminology.md)данных. Драйвер возвращает ошибку "драйвер не поддерживает эту функцию", если источник данных является каталогом [свободных таблиц](../../odbc/microsoft/visual-foxpro-terminology.md).  
  
 Дополнительные сведения см. в разделе [SQLPrimaryKeys](../../odbc/reference/syntax/sqlprimarykeys-function.md) в *справочнике программиста по ODBC*.
