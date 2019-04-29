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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d5cf669883ce81528adbe1fbd8faeff2ed716218
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62735142"
---
# <a name="sqltransact-mapping"></a>Сопоставление SQLTransact
**SQLTransact** заменяется **SQLEndTran**. Это основное отличие между двумя функциями **SQLEndTran** содержит аргумент *HandleType*, который указывает объем работы, которые необходимо выполнить. *HandleType* аргумента можно указать среду или дескриптора соединения. Следующий вызов **SQLTransact**:  
  
```  
SQLTransact(henv, hdbc, fType)  
```  
  
 сопоставляется с  
  
```  
SQLEndTran(SQL_HANDLE_DBC, ConnectionHandle, CompletionType);  
```  
  
 Если *ConnectionHandle* не равно SQL_NULL_HDBC. *ConnectionHandle* аргумент имеет значение значение *hdbc*.  
  
 **SQL_Transact** сопоставляется с  
  
```  
SQLEndTran (SQL_HANDLE_ENV, EnvironmentHandle, CompletionType);  
```  
  
 Если *ConnectionHandle* равен SQL_NULL_HDBC. *EnvironmentHandle* аргумент имеет значение значение *henv*.  
  
 В обоих указанных выше случаях *CompletionType* аргумент имеет значение совпадает со значением *fType*.
