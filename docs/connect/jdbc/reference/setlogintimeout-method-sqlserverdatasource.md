---
title: Метод setLoginTimeout (SQLServerDataSource) | Документы Microsoft
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
- SQLServerDataSource.setLoginTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b63d1cf4-dc1b-4e35-9a56-50436642eaaf
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f3c539e8805ba7e13e407c8a862ab1bbc13c6d7e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="setlogintimeout-method-sqlserverdatasource"></a>Метод setLoginTimeout (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает количество секунд, которое это [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) будет ждать объект при попытке установить соединение.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setLoginTimeout(int loginTimeout)  
```  
  
#### <a name="parameters"></a>Параметры  
 *LoginTimeout*  
  
 **Int** значение, представляющее количество секунд ожидания. Нулевое значение означает, что время ожидания равно системному времени ожидания по умолчанию, т.е. 15 секундам.  
  
## <a name="remarks"></a>Замечания  
 Этот метод setLoginTimeout указывается с помощью метода setLoginTimeout в интерфейсе javax.sql.DataSource.  
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
