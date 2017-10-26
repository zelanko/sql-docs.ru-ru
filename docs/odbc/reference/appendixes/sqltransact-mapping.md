---
title: "Сопоставление SQLTransact | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLTransact
- SQLTransact function [ODBC], mapping
ms.assetid: 8a01041f-3572-46f9-8213-b817f3cf929c
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 252339f7fcd2a3893f030c0ffbc4485ab5441152
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

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

