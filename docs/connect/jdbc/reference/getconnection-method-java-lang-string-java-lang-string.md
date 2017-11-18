---
title: "Метод (java.lang.String, java.lang.String) getConnection | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDataSource.getConnection (java.lang.String, java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 78db89d6-a8a0-4116-8885-548e627220ed
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 39b7a3bb2896ff308fc58510443bd54c487c77f8
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getconnection-method-javalangstring-javalangstring"></a>Метод getConnection (java.lang.String, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Пытается установить соединение с данными источника, который [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) представляет объект, используя заданное имя пользователя и пароль.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.Connection getConnection(java.lang.String username,  
                                         java.lang.String password)  
```  
  
#### <a name="parameters"></a>Параметры  
 *имя пользователя*  
  
 Объект **строка** , содержащее имя пользователя.  
  
 *пароль*  
  
 Объект **строка** , содержащее пароль.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объекта.  
  
## <a name="exceptions"></a>Исключения  
 java.sql.SQLException  
  
## <a name="remarks"></a>Замечания  
 Этот метод getConnection указывается с помощью метода getConnection в интерфейсе javax.sql.DataSource.  
  
 Вызов getConnection метод с именем ненулевой пользователя или пароля приведет к замене свойств имя и пароль пользователя, заданные в классе SQLServerDataSource при инициализации объекта SQLServerConnection. Например, если вызывающий объект вызвал [setUser](../../../connect/jdbc/reference/setuser-method-sqlserverdatasource.md) и [setPassword](../../../connect/jdbc/reference/setpassword-method-sqlserverdatasource.md) на источнике данных и затем getConnection вызовов и предоставляет ненулевой имя пользователя или стойкий пароль, имя пользователя и пароль задается Инструкция setUser и setPassword будет заменен имя пользователя и пароль, переданные в getConnection.  
  
> [!NOTE]  
>  Имя пользователя и пароль, которые заданы в URL-адресе с помощью вызова [setURL](../../../connect/jdbc/reference/seturl-method-sqlserverdatasource.md) метод в этом случае не будут изменены.  
  
## <a name="see-also"></a>См. также:  
 [Метод getConnection &#40; SQLServerDataSource &#41;](../../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md)   
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

