---
title: Метод getReference (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getReference
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b3fb1a97-86ee-4977-adca-c35ae199dbb3
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 50eace66b5f792ce9876d56dab8768555a43392f
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66775605"
---
# <a name="getreference-method-sqlserverdatasource"></a>Метод getReference (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает ссылку на этот объект [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public javax.naming.Reference getReference()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Ссылочный объект.  
  
## <a name="remarks"></a>Remarks  
 Этот метод getReference указывается с помощью метода getReference в интерфейсе javax.naming.Referenceable.  
  
 Если в версиях драйвера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC, предшествующих 3.0, метод SQLServerDataSource.setTrustStorePassword вызывался в объекте SQLServerDataSource, пароль присутствовал в объекте, возвращаемом SQLServerDataSource.getReference, что позволяло использовать объект для создания дополнительных соединений. В версии 3.0 драйвера JDBC необходимо установить пароль для объекта, возвращаемого SQLServerDataSource.getReference, перед установлением соединения с объектом.  
  
 Кроме того, если SQLServerDataSource.setTrustStorePassword задается перед привязкой свойств источника данных, необходимо вызвать метод SQLServerDataSource.setTrustStorePassword перед получением соединения. Например,  
  
```  
ctx = new InitialContext(System.getProperties());  
  
SQLServerDataSource ds1 = (SQLServerDataSource) ctx.lookup(jndiName);  
  
ds1.setTrustStorePassword("XXXXX");  
Connection con = ds1.getConnection("user", "XXXXXX");  
  
ctx.rebind(jndiName, ds1);  
SQLServerDataSource ds2 = (SQLServerDataSource) ctx.lookup(jndiName);  
ds2.setTrustStorePassword("XXXXX");   // reset the truststore password  
con = ds2.getConnection("user", "XXXXXX");   // provide userid and password again  
```  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
