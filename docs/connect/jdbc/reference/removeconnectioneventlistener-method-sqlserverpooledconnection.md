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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b9d2980b86704efe7e611878d373e0dd9b5cb7fa
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67975756"
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
  
  
