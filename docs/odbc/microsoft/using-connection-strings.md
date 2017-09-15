---
title: "Использование строк подключения | Документы Microsoft"
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
- connection strings [ODBC]
- connecting to data source [ODBC], Visual FoxPro
- Visual FoxPro data source [ODBC], connecting
ms.assetid: 57634960-47e9-49bf-95c1-6e3702ac8166
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f95e0a2ed1b93e89254e5e357cc3889dc5817554
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="using-connection-strings"></a>Использование строк подключения
Можно использовать строку подключения для подключения к источнику данных Visual FoxPro.  
  
 Например для подключения к источнику данных TasTrade и переопределение текущее значение параметра эксклюзивным, связанного с источником данных, используется строка:  
  
```  
DSN=TasTrade;Exclusive=Yes  
```  
  
 Список ключевых атрибутов и значений, можно включить в строку подключения, в разделе [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md).  
  
 Полное описание синтаксис строки соединения см. в разделе [SQLBrowseConnect](../../odbc/reference/syntax/sqlbrowseconnect-function.md) в *справочнике программиста ODBC*.
