---
title: Функция SQLRemoveDefaultDataSource | Документы Microsoft
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
apiname:
- SQLRemoveDefaultDataSource
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLRemoveDefaultDataSource
helpviewer_keywords:
- SQLRemoveDefaultDataSource function [ODBC]
ms.assetid: db803266-57df-4864-a41b-901247549c1f
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ed9d4bbed89bc4ed9330e8e857dcf1a0b9a3c149
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlremovedefaultdatasource-function"></a>Функция SQLRemoveDefaultDataSource
**Соответствия**  
 Появился в версии: ODBC 1.0, устаревшие  
  
 **Сводка**  
 В ODBC 3.0 **SQLRemoveDefaultDataSource** функция была заменена вызов [SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md) с *fRequest* ODBC_REMOVE_DEFAULT_DSN аргумент. Если ODBC 2 *.x* вызывает данную функцию, программа установки, установщик ODBC будет выполняться сопоставление для следующих **SQLConfigDataSource** вызова:  
  
```  
SQLConfigDataSource (NULL, ODBC_REMOVE_DEFAULT_DSN, NULL, NULL)  
```
