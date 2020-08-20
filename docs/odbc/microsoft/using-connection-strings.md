---
description: Изменение строк подключения
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
ms.openlocfilehash: 3ae8c3b1eda098a506d273f0d7baafec40985813
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471356"
---
# <a name="using-connection-strings"></a>Изменение строк подключения
Строку подключения можно использовать для подключения к источнику данных Visual FoxPro.  
  
 Например, чтобы подключиться к источнику данных Тастраде и переопределить текущее значение Exclusive, связанное с источником данных, используйте строку:  
  
```  
DSN=TasTrade;Exclusive=Yes  
```  
  
 Список ключевых слов и значений атрибутов, которые можно включить в строку подключения, см. в разделе [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md).  
  
 Полное описание синтаксиса строки подключения см. в разделе [SQLBrowseConnect](../../odbc/reference/syntax/sqlbrowseconnect-function.md) в *справочнике программиста по ODBC*.
