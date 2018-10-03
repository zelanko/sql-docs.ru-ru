---
title: Функция SQLRemoveDefaultDataSource | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 90270f119b351592348287823c2b9d879a15154b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47821122"
---
# <a name="sqlremovedefaultdatasource-function"></a>Функция SQLRemoveDefaultDataSource
**Соответствие стандартам**  
 Версии представлены: ODBC 1.0 устарело  
  
 **Сводка**  
 В ODBC 3.0 **SQLRemoveDefaultDataSource** функции был заменен вызовом [SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md) с *fRequest* аргумент ODBC_REMOVE_DEFAULT_DSN. Если ODBC 2 *.x* программа установки вызывает эту функцию, установщик ODBC будет выполняться сопоставление следующим **SQLConfigDataSource** вызова:  
  
```  
SQLConfigDataSource (NULL, ODBC_REMOVE_DEFAULT_DSN, NULL, NULL)  
```
