---
title: Метод setSendTimeAsDatetime (SQLServerDataSource) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 705a0494-b5e2-43db-940a-1b8cec550cdb
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4a5e9d17255ac790fbf2d1466555a2e2e877e13d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="setsendtimeasdatetime-method-sqlserverdatasource"></a>Метод setSendTimeAsDatetime (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Этот метод добавлен в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] версии 3.0 драйвера JDBC.  
  
 Изменяет значение **sendTimeAsDatetime** свойство соединения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setSendTimeAsDatetime(boolean sendTimeAsDateTime)  
```  
  
#### <a name="parameters"></a>Параметры  
 *sendTimeAsDateTime*  
  
 Значение типа Boolean. Если задано значение true, то значения java.sql.Time отправляемых на сервер в качестве [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] **datetime** типов. Если задано значение false, то значения java.sql.Time отправляемых на сервер в качестве [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] **время** типов.  
  
## <a name="remarks"></a>Замечания  
 [SQLServerDataSource.getSendTimeAsDatetime](../../../connect/jdbc/reference/getsendtimeasdatetime-method-sqlserverdatasource.md) возвращает значение **sendTimeAsDatetime** свойство соединения.  
  
 Дополнительные сведения о **sendTimeAsDatetime** свойства соединения в разделе [задание свойств соединения](../../../connect/jdbc/setting-the-connection-properties.md).  
  
 Дополнительные сведения см. в разделе [как настройка java.sql.Time отправляются на сервер](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
