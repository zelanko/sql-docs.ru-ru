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
ms.topic: article
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
ms.workload: Inactive
ms.openlocfilehash: c5b3a37cf0b0f42567d4a787b9c090f8298f74ca
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sqlremovedefaultdatasource-function"></a>Функция SQLRemoveDefaultDataSource
**Соответствия**  
 Появился в версии: ODBC 1.0, устаревшие  
  
 **Сводка**  
 В ODBC 3.0 **SQLRemoveDefaultDataSource** функция была заменена вызов [SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md) с *fRequest* ODBC_REMOVE_DEFAULT_DSN аргумент. Если ODBC 2*.x* вызывает данную функцию, программа установки, установщик ODBC будет выполняться сопоставление для следующих **SQLConfigDataSource** вызова:  
  
```  
SQLConfigDataSource (NULL, ODBC_REMOVE_DEFAULT_DSN, NULL, NULL)  
```
