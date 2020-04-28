---
title: Сопоставление SQLTransact | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLTransact
- SQLTransact function [ODBC], mapping
ms.assetid: 8a01041f-3572-46f9-8213-b817f3cf929c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6aaa056fca860a70f81ad7c3a4cd8539512bc25d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304885"
---
# <a name="sqltransact-mapping"></a>Сопоставление SQLTransact
Теперь **SQLTransact** заменяется на **SQLEndTran**. Основное различие между двумя функциями заключается в том, что **SQLEndTran** содержит аргумент *параметром handletype*, указывающий область действия, которое необходимо выполнить. Аргумент *параметром handletype* может указывать среду или маркер соединения. Следующий вызов **SQLTransact**:  
  
```  
SQLTransact(henv, hdbc, fType)  
```  
  
 сопоставлен с  
  
```  
SQLEndTran(SQL_HANDLE_DBC, ConnectionHandle, CompletionType);  
```  
  
 Если *коннектионхандле* не равно SQL_NULL_HDBC. Аргументу *коннектионхандле* присваивается значение *хдбк*.  
  
 **SQL_Transact** сопоставлено с  
  
```  
SQLEndTran (SQL_HANDLE_ENV, EnvironmentHandle, CompletionType);  
```  
  
 Если *коннектионхандле* равно SQL_NULL_HDBC. Аргументу *енвиронменсандле* присваивается значение *хенв*.  
  
 В обоих приведенных выше случаях аргументу *комплетионтипе* присваивается то же значение, что и для *fType*.
