---
title: SQLPrimaryKeys (драйвер ODBC для Visual FoxPro) | Документы Microsoft
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
- SQLPrimaryKeys function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 8dbe2903-efdc-45e0-a079-9e357c5fd81b
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4d16d0a556fdb6eaa353260117c950886ad0687c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlprimarykeys-visual-foxpro-odbc-driver"></a>SQLPrimaryKeys (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Этот раздел содержит сведения по Visual FoxPro ODBC драйвера. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: полный  
  
 Совместимости API ODBC: Уровень 2  
  
 Возвращает имена столбцов, которые составляют первичный ключ для таблицы. Реализация драйвера ODBC для Visual FoxPro **SQLPrimaryKeys** ведет себя следующим образом:  
  
-   Игнорирует *szTableOwner* и *cbTableOwner* аргументы.  
  
-   Работает только для источников данных, которые являются [баз данных](../../odbc/microsoft/visual-foxpro-terminology.md). Драйвер возвращает ошибку «Драйвер не поддерживает эту функцию» Если источником данных является каталог [свободных таблиц](../../odbc/microsoft/visual-foxpro-terminology.md).  
  
 Дополнительные сведения см. в разделе [SQLPrimaryKeys](../../odbc/reference/syntax/sqlprimarykeys-function.md) в *справочнике программиста ODBC*.
