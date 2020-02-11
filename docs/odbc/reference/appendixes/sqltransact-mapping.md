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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68070114"
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
