---
description: Метод getWarnings (SQLServerConnection)
title: Метод getWarnings (SQLServerConnection) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.getWarnings
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 15af39bf-6285-44cc-a021-7341e7a055c4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 19993e5425b886824dfa2a556aaef5fa9234d6f8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88433786"
---
# <a name="getwarnings-method-sqlserverconnection"></a>Метод getWarnings (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает первое предупреждение, указанное в отчетах вызовов данного объекта [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.SQLWarning getWarnings()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект SQLWarning.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getWarnings задается с помощью метода getWarnings в интерфейсе java.sql.Connection.  
  
 Последующие предупреждения добавляются к первому SQLWarning и вызываются методом getNextWarning. В случае вызова в закрытом соединении создается исключение.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
