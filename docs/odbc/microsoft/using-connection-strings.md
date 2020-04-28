---
title: Использование строк подключения | Документация Майкрософт
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307595"
---
# <a name="using-connection-strings"></a>Изменение строк подключения
Строку подключения можно использовать для подключения к источнику данных Visual FoxPro.  
  
 Например, чтобы подключиться к источнику данных Тастраде и переопределить текущее значение Exclusive, связанное с источником данных, используйте строку:  
  
```  
DSN=TasTrade;Exclusive=Yes  
```  
  
 Список ключевых слов и значений атрибутов, которые можно включить в строку подключения, см. в разделе [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md).  
  
 Полное описание синтаксиса строки подключения см. в разделе [SQLBrowseConnect](../../odbc/reference/syntax/sqlbrowseconnect-function.md) в *справочнике программиста по ODBC*.
