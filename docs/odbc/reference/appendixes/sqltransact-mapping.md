---
title: Сопоставление SQLTransact | Документы Microsoft
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
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLTransact
- SQLTransact function [ODBC], mapping
ms.assetid: 8a01041f-3572-46f9-8213-b817f3cf929c
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e4742829b5df9d99007181109f68d020a2f4af98
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sqltransact-mapping"></a>Сопоставление SQLTransact
**SQLTransact** заменяется **SQLEndTran**. Основное различие между двумя функциями, звучит **SQLEndTran** содержит аргумент *HandleType*, которое указывает объем работы, которые необходимо выполнить. *HandleType* аргумент позволяет задать среду или дескриптора соединения. В следующем вызове **SQLTransact**:  
  
```  
SQLTransact(henv, hdbc, fType)  
```  
  
 сопоставляется  
  
```  
SQLEndTran(SQL_HANDLE_DBC, ConnectionHandle, CompletionType);  
```  
  
 Если *ConnectionHandle* не равно SQL_NULL_HDBC. *ConnectionHandle* аргументу присвоено значение *hdbc*.  
  
 **SQL_Transact** сопоставляется  
  
```  
SQLEndTran (SQL_HANDLE_ENV, EnvironmentHandle, CompletionType);  
```  
  
 Если *ConnectionHandle* равен SQL_NULL_HDBC. *EnvironmentHandle* аргументу присвоено значение *henv*.  
  
 В обоих случаях выше *CompletionType* аргумент имеет значение совпадает со значением *fType*.
