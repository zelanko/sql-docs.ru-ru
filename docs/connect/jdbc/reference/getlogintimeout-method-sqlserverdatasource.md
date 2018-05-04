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
ms.topic: conceptual
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
ms.openlocfilehash: dcaccc8a16561f43b4ada72d1e07bad291b6ec2c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
  
  
