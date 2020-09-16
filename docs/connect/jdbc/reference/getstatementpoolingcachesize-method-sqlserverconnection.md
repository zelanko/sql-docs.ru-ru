---
description: Метод getStatementPoolingCacheSize (SQLServerConnection)
title: Метод getStatementPoolingCacheSize (SQLServerConnection) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.getStatementPoolingCacheSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 645dcaddce41a8764306f897453d082e72220836
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88434376"
---
# <a name="getstatementpoolingcachesize-method-sqlserverconnection"></a>Метод getStatementPoolingCacheSize (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Возвращает размер кэша подготовленных инструкций для этого подключения. Значение "0" означает, что кэширование не включено.

## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getStatementPoolingCacheSize()  
```  

## <a name="return-value"></a>Возвращаемое значение
 Значение типа **int**, которое содержит свойство подключения **statementPoolingCacheSize**.

## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 Этот метод доступен в драйвере JDBC 6.4 и более поздних версий.
 
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
