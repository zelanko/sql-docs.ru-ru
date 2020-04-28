---
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
ms.openlocfilehash: 952ace7d17e8bb5b4c824761b02e5c8a0895f519
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303945"
---
# <a name="sqlremovedefaultdatasource-function"></a>Функция SQLRemoveDefaultDataSource
**Соответствия**  
 Введенная версия: ODBC 1,0, не рекомендуется  
  
 **Сводка**  
 В ODBC 3,0 функция **склремоведефаултдатасаурце** была заменена вызовом [SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md) с аргументом *фрекуест* ODBC_REMOVE_DEFAULT_DSN. Если программа установки ODBC 2 *. x* вызывает эту функцию, установщик ODBC будет сопоставлять его со следующим вызовом **SQLConfigDataSource** :  
  
```cpp  
SQLConfigDataSource (NULL, ODBC_REMOVE_DEFAULT_DSN, NULL, NULL)  
```
