---
title: "setPoolable метод (SQLServerStatement) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0f798c8-cafb-4acc-b85d-2e0059c91d92
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3cb4fd96733a36f6f9f0743fede135327c7d8b5e
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="setpoolable-method-sqlserverstatement"></a>setPoolable метод (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Запрашивает поддержку пулов или запрет пулов в инструкции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setPoolable(boolean poolable) throws SQLException  
```  
  
#### <a name="parameters"></a>Параметры  
 *может быть в пуле*  
  
 Если **true**, запросы, что инструкция в пул. Если **false**, запросы не включалось инструкцию.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Значение, указанное в *пулы* параметр является указание для реализации пула инструкций, указывающее, было ли приложению инструкции, помещаемых в пул. Диспетчер пула инструкций определяет, будет ли использоваться эта подсказка.  
  
 Значение пула инструкций применяется к внутренним кэшам инструкций, реализованным в драйвере, и внешним кэшам инструкций, реализованным на серверах приложений и в других приложениях.  
  
 По умолчанию объект SQLServerStatement не поддерживают. Объекты, SQLServerPreparedStatement и SQLServerCallableStatement, поддерживают.  
  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) создается, если этот метод вызывается для закрытой инструкции.  
  
 [isPoolable](../../../connect/jdbc/reference/ispoolable-method-sqlserverstatement.md) возвращает значение, указывающее, является ли объект пулы.  
  
## <a name="see-also"></a>См. также:  
 [Члены SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
