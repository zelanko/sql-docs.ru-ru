---
title: "Метод getUser (SQLServerDataSource) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDataSource.getUser
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3513dd7f-6ae5-4010-bde0-454ac4365bce
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9de58a65490961002fbdcfa37d0a2367ca078382
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

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
  
  

