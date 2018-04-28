---
title: Метод setUser (SQLServerDataSource) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- SQLServerDataSource.setUser
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: d2ea7906-2d10-438d-aa51-f576eea923c7
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3b8b93bf8205bcf1cf828ab53c7a2842e13a9f4c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="setuser-method-sqlserverdatasource"></a>Метод setUser (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает имя пользователя, используемое для соединения с источником данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setUser(java.lang.String user)  
```  
  
#### <a name="parameters"></a>Параметры  
 *user*  
  
 Объект **строка** , содержащее имя пользователя.  
  
## <a name="remarks"></a>Замечания  
 Метод setUser задает имя пользователя, который будет использоваться для подключения к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]. Если не указано значение имени пользователя, [getUser](../../../connect/jdbc/reference/getuser-method-sqlserverdatasource.md) метод возвращает значение по умолчанию null.  
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
