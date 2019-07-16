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
ms.openlocfilehash: b2082a97b24284afcc879048bb08e86a7b2bb3ba
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68070114"
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
