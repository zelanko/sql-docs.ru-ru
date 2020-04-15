---
title: СЗЛТрансакт Картирование (ru) Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304885"
---
# <a name="sqltransact-mapping"></a>Сопоставление SQLTransact
В настоящее время на смену **«СЗЛТрансакт»** заменена **на S'LEndTran**. Основное различие между этими двумя функциями заключается в том, что **S'LEndTran** содержит аргумент *HandleType*, который определяет объем работы, которая должна быть сделана. Аргумент *HandleType* может указывать среду или ручку соединения. Следующий звонок в **S'LTransact:**  
  
```  
SQLTransact(henv, hdbc, fType)  
```  
  
 отображается до  
  
```  
SQLEndTran(SQL_HANDLE_DBC, ConnectionHandle, CompletionType);  
```  
  
 если *ConnectionHandle* не соответствует SQL_NULL_HDBC. *Аргумент ConnectionHandle* устанавливается на значение *HDbc.*  
  
 **SQL_Transact** отображается до  
  
```  
SQLEndTran (SQL_HANDLE_ENV, EnvironmentHandle, CompletionType);  
```  
  
 если *ConnectionHandle* равен SQL_NULL_HDBC. *Аргумент EnvironmentHandle* устанавливается на значение *henv*.  
  
 В обоих предыдущих случаях аргумент *CompletionType* устанавливается на то же значение, что и *fType.*
