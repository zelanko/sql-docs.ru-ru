---
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
ms.openlocfilehash: 2d7849fb0f55dd44a3af5590af2bccf6a06648a0
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80921242"
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
  
  
