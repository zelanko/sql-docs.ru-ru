---
description: Метод setHoldability (SQLServerConnection)
title: Метод setHoldability (SQLServerConnection) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.setHoldability
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 552eebd0-4c38-43f0-961f-35244f99109b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7111094bf78e1fa1408ce163d764e52f30274c33
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88431796"
---
# <a name="setholdability-method-sqlserverconnection"></a>Метод setHoldability (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Изменяет возможность ожидания объектов [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md), созданных с помощью этого объекта [SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md) с заданной возможностью ожидания.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setHoldability(int nNewHold)  
```  
  
#### <a name="parameters"></a>Параметры  
 *nNewHold*  
  
 Значение **int**, содержащее один из следующих уровней возможности ожидания:  
  
 HOLD_CURSORS_OVER_COMMIT  
  
 CLOSE_CURSORS_AT_COMMIT  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод setHoldability определен с помощью метода setHoldability в интерфейсе java.sql.Connection.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
