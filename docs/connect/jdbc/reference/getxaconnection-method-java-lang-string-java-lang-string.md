---
title: "Метод (java.lang.String, java.lang.String) getXAConnection | Документы Microsoft"
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
apiname: SQLServerXADataSource.getXAConnection (java.lang.String, java.lang.String)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 276e0093-3d42-4f73-acc4-2b5b98245b40
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7b9cb48cab11159a3494f785921368010144bbe8
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="getxaconnection-method-javalangstring-javalangstring"></a>Метод getXAConnection (java.lang.String, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Пытается установить физическое соединение с базой данных по заданному имени пользователя и паролю.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public javax.sql.XAConnection getXAConnection(java.lang.String user,  
                                              java.lang.String password)  
```  
  
#### <a name="parameters"></a>Параметры  
 *пользователь*  
  
 Объект **строка** , содержащее имя пользователя.  
  
 *пароль*  
  
 Объект **строка** , содержащее пароль.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект XAConnection.  
  
## <a name="exceptions"></a>Исключения  
 java.sql.SQLException  
  
## <a name="remarks"></a>Замечания  
 Этот метод getXAConnection указывается с помощью метода getXAConnection в интерфейсе javax.sql.XADataSource.  
  
> [!NOTE]  
>  Этот метод обычно вызывается в реализациях пула соединений XA, а не в обычном коде приложений JDBC.  
  
## <a name="see-also"></a>См. также:  
 [Метод getXAConnection &#40; SQLServerXADataSource &#41;](../../../connect/jdbc/reference/getxaconnection-method-sqlserverxadatasource.md)   
 [Методы SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-methods.md)   
 [Элементы SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-members.md)   
 [Класс SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-class.md)  
  
  
