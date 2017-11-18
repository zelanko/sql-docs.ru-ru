---
title: "Метод setObject (int, java.lang.Object, int, int) | Документы Microsoft"
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
- SQLServerPreparedStatement.setObject (int, java.lang.Object, int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: d190ee20-d669-4c6f-a081-d5cfec2f72ca
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: dda180cf7e5969704458e0d324ecc3322c6eaf18
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setobject-method-int-javalangobject-int-int"></a>Метод setObject (int, java.lang.Object, int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Устанавливает значение указанного параметра по заданному объекту, целевому типу и масштабу.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setObject(int n,  
                            java.lang.Object obj,  
                            int targetSqlType,  
                            int scale)  
```  
  
#### <a name="parameters"></a>Параметры  
 *n*  
  
 **Int** указывает номер параметра.  
  
 *OBJ*  
  
 Объект.  
  
 *targetSqlType*  
  
 **Int** , указывающее тип объекта, определенный в java.sql.Types.  
  
 *масштаб*  
  
 **Int** указывает количество цифр справа от десятичной запятой. Этот параметр не учитывается для всех типов, кроме NUMERIC и DECIMAL.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод setObject указывается с помощью метода setObject в интерфейсе java.sql.PreparedStatement.  
  
 Начиная с версии [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] версии 3.0 драйвера JDBC поведение данного метода изменяется с **sendTimeAsDatetime** свойство соединения ([задание свойств соединения](../../../connect/jdbc/setting-the-connection-properties.md)) и [ SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md).  
  
 Дополнительные сведения см. в разделе [как настройка java.sql.Time отправляются на сервер](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="see-also"></a>См. также:  
 [Метод setObject &#40; SQLServerPreparedStatement &#41;](../../../connect/jdbc/reference/setobject-method-sqlserverpreparedstatement.md)   
 [Члены SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Класс SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  

