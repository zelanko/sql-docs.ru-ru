---
title: Сопоставление SQLTransact | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLTransact
- SQLTransact function [ODBC], mapping
ms.assetid: 8a01041f-3572-46f9-8213-b817f3cf929c
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3e938a4eb7c605d1ed9cf71c038bcc7187e1a8cb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32907879"
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
