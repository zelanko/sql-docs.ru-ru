---
title: Метод getLoginTimeout (SQLServerDataSource) | Документы Microsoft
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
- SQLServerDataSource.getLoginTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 316f067c-9e08-456a-af19-b80b0bbd4a5c
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0ca310bbfa7b367f595ecf35ef92e9189ef323a0
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="getlogintimeout-method-sqlserverdatasource"></a>Метод getLoginTimeout (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает количество секунд, [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) будет ждать объект при попытке установить соединение.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getLoginTimeout()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **Int** значение, представляющее количество секунд ожидания.  
  
## <a name="remarks"></a>Замечания  
 Если приложение не указывает явно значение периода ожидания, этот метод возвращает значение по умолчанию 15 секунд.  
  
 Этот метод getLoginTimeout указывается с помощью метода getLoginTimeout в интерфейсе javax.sql.DataSource.  
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
