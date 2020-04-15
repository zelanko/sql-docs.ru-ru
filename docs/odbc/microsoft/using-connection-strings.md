---
title: Использование строк соединения Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connection strings [ODBC]
- connecting to data source [ODBC], Visual FoxPro
- Visual FoxPro data source [ODBC], connecting
ms.assetid: 57634960-47e9-49bf-95c1-6e3702ac8166
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9083414503606720a40d372ed883a140953dc415
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307595"
---
# <a name="using-connection-strings"></a>Изменение строк подключения
Для подключения к источнику данных Visual FoxPro можно использовать строку подключения к visual FoxPro.  
  
 Например, для подключения к источнику данных TasTrade и переопределения текущего параметра Exclusive, связанного с источником данных, можно использовать строку:  
  
```  
DSN=TasTrade;Exclusive=Yes  
```  
  
 Для списка ключевых слов атрибутов и значений, которые [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md)можно включить в строку соединения, см.  
  
 Полное объяснение синтаксиса строки соединения [можно](../../odbc/reference/syntax/sqlbrowseconnect-function.md) узнать в *справочнике программиста ODBC.*
