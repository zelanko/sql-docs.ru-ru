---
description: Метод removeConnectionEventListener (SQLServerPooledConnection)
title: Метод removeConnectionEventListener (SQLServerPooledConnection) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPooledConnection.removeConnectionEventListener
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 46902e89-f512-40af-a2d9-a896f03d1200
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ba6472207d42379a3c1d5fe04f4313db986ab0d2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88432746"
---
# <a name="removeconnectioneventlistener-method-sqlserverpooledconnection"></a>Метод removeConnectionEventListener (SQLServerPooledConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Удаляет заданный прослушиватель событий.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void removeConnectionEventListener(javax.sql.ConnectionEventListener listener)  
```  
  
#### <a name="parameters"></a>Параметры  
 *listener*  
  
 Объект ConnectionEventListener.  
  
## <a name="remarks"></a>Remarks  
 Этот метод removeConnectionEventListener задается с помощью метода removeConnectionEventListener в интерфейсе javax.sql.PooledConnection.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-methods.md)   
 [Элементы SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-members.md)   
 [Класс SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)  
  
  
