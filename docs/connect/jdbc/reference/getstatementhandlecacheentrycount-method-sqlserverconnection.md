---
title: Метод getStatementHandleCacheEntryCount (SQLServerConnection) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.getStatementHandleCacheEntryCount
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6a5d87ab4f78a5f006e87c34fa774fd9f430aaae
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67979535"
---
# <a name="getstatementhandlecacheentrycount-method-sqlserverconnection"></a>Метод getStatementHandleCacheEntryCount (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Возвращает текущее число обработчиков подготовленных инструкций в составе пула.

## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getStatementHandleCacheEntryCount()  
```  

## <a name="return-value"></a>Возвращаемое значение
 Значение **int**, которое содержит текущее число обработчиков подготовленных инструкций в составе пула.

## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 Этот метод доступен в драйвере JDBC 6.4 и более поздних версий.
 
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
