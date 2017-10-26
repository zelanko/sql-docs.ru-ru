---
title: "Метод getSendTimeAsDatetime (SQLServerDataSource) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02287122-5dc1-455d-987f-95fd9a69d503
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 625d1e864cd0f913dbf8826372017ee99a80e41d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getsendtimeasdatetime-method-sqlserverdatasource"></a>Метод getSendTimeAsDatetime (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Этот метод добавлен в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] версии 3.0 драйвера JDBC.  
  
 Возвращает значение **sendTimeAsDatetime** свойство соединения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean getSendTimeAsDatetime();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** Если значения java.sql.Time будут отправляться на сервер в качестве [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] **datetime** типа. **false** Если значения java.sql.Time будут отправляться на сервер в качестве [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] **время** типа.  
  
## <a name="remarks"></a>Замечания  
 В разделе [задание свойств соединения](../../../connect/jdbc/setting-the-connection-properties.md) Дополнительные сведения о **sendTimeAsDatetime** свойство соединения.  
  
 [SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md) позволяет программно задать **sendTimeAsDatetime** свойство соединения.  
  
 Дополнительные сведения см. в разделе [как настройка java.sql.Time отправляются на сервер](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

