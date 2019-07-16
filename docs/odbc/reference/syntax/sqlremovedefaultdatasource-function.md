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
ms.openlocfilehash: cfefcd9f2f55e2d78c5c6e5b1bac7ce52e9033e5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68024605"
---
# <a name="sqlremovedefaultdatasource-function"></a>Функция SQLRemoveDefaultDataSource
**Соответствие стандартам**  
 Представленные версии: 1.0, рекомендуется использовать ODBC  
  
 **Сводка**  
 В ODBC 3.0 **SQLRemoveDefaultDataSource** функции был заменен вызовом [SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md) с *fRequest* аргумент ODBC_REMOVE_DEFAULT_DSN. Если ODBC 2 *.x* программа установки вызывает эту функцию, установщик ODBC будет выполняться сопоставление следующим **SQLConfigDataSource** вызова:  
  
```cpp  
SQLConfigDataSource (NULL, ODBC_REMOVE_DEFAULT_DSN, NULL, NULL)  
```
