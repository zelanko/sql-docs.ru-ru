---
title: "Использование строк подключения | Документы Microsoft"
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
helpviewer_keywords:
- connection strings [ODBC]
- connecting to data source [ODBC], Visual FoxPro
- Visual FoxPro data source [ODBC], connecting
ms.assetid: 57634960-47e9-49bf-95c1-6e3702ac8166
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dc75f4b4b90f2845ea18d6e3208806fce2c9179e
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="using-connection-strings"></a>Использование строк подключения
Можно использовать строку подключения для подключения к источнику данных Visual FoxPro.  
  
 Например для подключения к источнику данных TasTrade и переопределение текущее значение параметра эксклюзивным, связанного с источником данных, используется строка:  
  
```  
DSN=TasTrade;Exclusive=Yes  
```  
  
 Список ключевых атрибутов и значений, можно включить в строку подключения, в разделе [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md).  
  
 Полное описание синтаксис строки соединения см. в разделе [SQLBrowseConnect](../../odbc/reference/syntax/sqlbrowseconnect-function.md) в *справочнике программиста ODBC*.
