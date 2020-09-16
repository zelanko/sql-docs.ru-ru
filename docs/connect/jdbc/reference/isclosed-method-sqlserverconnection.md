---
description: Метод isClosed (SQLServerConnection)
title: Метод isClosed (SQLServerConnection) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.isClosed
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3560ab18-4350-4d02-9716-439f0c2f7142
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 09d4a5e3c1d3634e52fd9b2d8244262c40fada06
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88433596"
---
# <a name="isclosed-method-sqlserverconnection"></a>Метод isClosed (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Указывает, был ли закрыт этот объект [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean isClosed()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **true** если соединение закрыто. В противном случае значение **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод isClosed определен с помощью метода isClosed в интерфейсе java.sql.Connection.  
  
 Проверяет состояние вызванного объекта SQLServerConnection. Соединение считается закрытым, если для него вызван метод [close](../../../connect/jdbc/reference/close-method-sqlserverconnection.md) либо если произошли определенные неустранимые ошибки. Этот метод будет возвращать значение **true**, только если он вызывается после вызова метода close.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
