---
title: "Метод getUser (SQLServerDataSource) | Документы Microsoft"
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
apiname: SQLServerDataSource.getUser
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 3513dd7f-6ae5-4010-bde0-454ac4365bce
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d0be6cc3ac11282b6188129a6b04f3f47043862b
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="getuser-method-sqlserverdatasource"></a>Метод getUser (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает имя пользователя, используемое для соединения с источником данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getUser()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект **строка** , содержащее имя пользователя.  
  
## <a name="remarks"></a>Замечания  
 [SetUser](../../../connect/jdbc/reference/setuser-method-sqlserverdatasource.md) метод задает имя пользователя, который будет использоваться при подключении к экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]. Если значение имени пользователя не задано, метод getUser возвращает значение NULL по умолчанию.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
