---
title: Использование строк подключения | Документы Microsoft
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
- connection strings [ODBC]
- connecting to data source [ODBC], Visual FoxPro
- Visual FoxPro data source [ODBC], connecting
ms.assetid: 57634960-47e9-49bf-95c1-6e3702ac8166
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e1e492423fec8f214890dfa7aa2f75c8a6ce19da
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="using-connection-strings"></a>Использование строк подключения
Можно использовать строку подключения для подключения к источнику данных Visual FoxPro.  
  
 Например для подключения к источнику данных TasTrade и переопределение текущее значение параметра эксклюзивным, связанного с источником данных, используется строка:  
  
```  
DSN=TasTrade;Exclusive=Yes  
```  
  
 Список ключевых атрибутов и значений, можно включить в строку подключения, в разделе [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md).  
  
 Полное описание синтаксис строки соединения см. в разделе [SQLBrowseConnect](../../odbc/reference/syntax/sqlbrowseconnect-function.md) в *справочнике программиста ODBC*.
