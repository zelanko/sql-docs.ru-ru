---
title: "Метод setWorkstationID (SQLServerDataSource) | Документы Microsoft"
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
apiname: SQLServerDataSource.setWorkstationID
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: c1093615-90bf-4918-9f05-8abd765ffb03
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bd2d1ad16dd1ff622c7d8f4f8394df08bdfd3f6a
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="setworkstationid-method-sqlserverdatasource"></a>Метод setWorkstationID (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает имя клиентского компьютера, используемое для соединения с источником данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setWorkstationID(java.lang.String workstationID)  
```  
  
#### <a name="parameters"></a>Параметры  
 *Идентификатор workstationID*  
  
 Объект **строка** , содержащее имя клиентского компьютера.  
  
## <a name="remarks"></a>Замечания  
 Идентификатор workstationID — это имя клиентского компьютера или рабочей станции. Если свойство workstationID не задано, значение по умолчанию создается путем вызова метода InetAddress.getLocalHost().getHostName(). Если getHostName возвращает пустое значение, вызывается метод getHostAddress().toString().  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
