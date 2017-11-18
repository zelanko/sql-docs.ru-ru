---
title: "Метод getHoldability (SQLServerResultSet) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4508d90f-c3c4-4eac-8001-fb0b93b66734
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ae5a5d40381cd6b7939e7e67b5950e3d0e3644d3
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getholdability-method-sqlserverresultset"></a>Метод getHoldability (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает значение удержания это [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getHoldability()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **Int** значение, которое содержит один из следующих уровней удержания:  
  
 HOLD_CURSORS_OVER_COMMIT  
  
 CLOSE_CURSORS_AT_COMMIT  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getHoldability указывается с помощью метода getHoldability в интерфейсе java.sql.ResultSet.  
  
 Чтобы задать удержание результирующего набора, приложения могут использовать [setHoldability](../../../connect/jdbc/reference/setholdability-method-sqlserverconnection.md) метод [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) класса. После [setHoldability](../../../connect/jdbc/reference/setholdability-method-sqlserverconnection.md) вызывается метод и создается объект инструкции и его объект результирующего набора и выполняется инструкция, приложение может потребоваться изменение уровня удержания еще раз.  
  
 Для серверных курсоров при соединении с SQL Server 2005 или более поздней версии параметр возможности сохранения влияет только на новые результирующие наборы, которые будут созданы для этого соединения. Однако для SQL Server 2000 установка возможности сохранения относится и к существующим результирующим наборам, и к новым, которые пока не созданы для данного соединения.  
  
 При сбросе уровня удержания и getHoldability метод будет вызван на ранее созданном объекте результирующего набора, значение, возвращенное этим методом может отличаться от значения удержания, возвращенного следующие методы: Statement.getResultSetHoldability , Connection.getHoldability или DatabaseMetaData.getResultSetHoldability.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

