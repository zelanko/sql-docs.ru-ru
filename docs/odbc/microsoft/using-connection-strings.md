---
title: С помощью строки подключения | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 496fe10fbf49f4d712127e2e4122c50fa20ba2be
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68044583"
---
# <a name="using-connection-strings"></a>Изменение строк подключения
Строку подключения можно использовать для подключения к источнику данных Visual FoxPro.  
  
 Например для подключения к источнику данных TasTrade и переопределение, текущее значение параметра эксклюзивным, связанный с источником данных, можно использовать строку:  
  
```  
DSN=TasTrade;Exclusive=Yes  
```  
  
 Список ключевых слов для атрибута и значения, можно включить в строку подключения, см. в разделе [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md).  
  
 Полное описание синтаксис строки подключения, см. в разделе [SQLBrowseConnect](../../odbc/reference/syntax/sqlbrowseconnect-function.md) в *Справочник по программированию ODBC*.
