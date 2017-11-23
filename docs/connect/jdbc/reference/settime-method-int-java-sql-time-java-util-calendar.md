---
title: "Метод setTime (int, java.sql.Time, java.util.Calendar) | Документы Microsoft"
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
apiname: SQLServerPreparedStatement.setTime (int, java.sql.Time, java.lang.Calendar)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 79ff6eef-6ad7-4e33-95be-c2d552c65546
caps.latest.revision: "18"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8fbe886670a2ffdb6065b57cfb8a27a9ff078e99
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="settime-method-int-javasqltime-javautilcalendar"></a>Метод setTime (int, java.sql.Time, java.util.Calendar)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Устанавливает указанный параметр в заданные значения времени и календаря.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setTime(int n,  
                          java.sql.Time x,  
                          java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>Параметры  
 *n*  
  
 **Int** указывает номер параметра.  
  
 *x*  
  
 Объект времени.  
  
 *Клиентская лицензия*  
  
 Объект календаря.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод setTime определяется setTime-метод в интерфейсе java.sql.PreparedStatement.  
  
 Начиная с версии [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] версии 3.0 драйвера JDBC поведение данного метода изменяется с **sendTimeAsDatetime** свойство соединения ([задание свойств соединения](../../../connect/jdbc/setting-the-connection-properties.md)) и [ SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md).  
  
 Дополнительные сведения см. в разделе [как настройка java.sql.Time отправляются на сервер](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="see-also"></a>См. также:  
 [Метод setTime &#40; SQLServerPreparedStatement &#41;](../../../connect/jdbc/reference/settime-method-sqlserverpreparedstatement.md)   
 [Члены SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Класс SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
