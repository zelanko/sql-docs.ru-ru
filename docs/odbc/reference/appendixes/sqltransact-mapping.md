---
description: Сопоставление SQLTransact
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
ms.openlocfilehash: cf1298c9881a207c21074e03e8b0597ab8f11448
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429505"
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
