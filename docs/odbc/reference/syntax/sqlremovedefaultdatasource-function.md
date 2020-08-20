---
description: Функция SQLRemoveDefaultDataSource
title: Функция Склремоведефаултдатасаурце | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0010e59cc4dfad2d54b8b1c4e59e83ea72fcd3ad
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487092"
---
# <a name="sqlremovedefaultdatasource-function"></a>Функция SQLRemoveDefaultDataSource
**Соответствия**  
 Введенная версия: ODBC 1,0, не рекомендуется  
  
 **Сводка**  
 В ODBC 3,0 функция **склремоведефаултдатасаурце** была заменена вызовом [SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md) с аргументом *фрекуест* ODBC_REMOVE_DEFAULT_DSN. Если программа установки ODBC 2 *. x* вызывает эту функцию, установщик ODBC будет сопоставлять его со следующим вызовом **SQLConfigDataSource** :  
  
```cpp  
SQLConfigDataSource (NULL, ODBC_REMOVE_DEFAULT_DSN, NULL, NULL)  
```
