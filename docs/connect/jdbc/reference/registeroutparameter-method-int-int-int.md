---
title: Метод registerOutParameter (int, int, int) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.registerOutParameter (int, int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: d902d4e0-881f-4182-814c-0ede9a8da7fd
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 043d53b22987c1b459c7668db4ea962a80e303be
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47784142"
---
# <a name="registeroutparameter-method-int-int-int"></a>Метод registerOutParameter (int, int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Регистрирует параметр OUT с указанным порядковым номером для заданного типа и масштаба JDBC.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void registerOutParameter(int index,  
                                 int sqlType,  
                                 int scale)  
```  
  
#### <a name="parameters"></a>Параметры  
 *index*  
  
 Значение типа **int**, указывающее порядковый номер параметра.  
  
 *sqlType*  
  
 Код типа JDBC, определенный в java.sql.Types.  
  
 *масштаб*  
  
 Значение типа **int**, указывающее количество разрядов, размещаемых справа от десятичного разделителя.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод registerOutParameter указывается с помощью метода registerOutParameter в интерфейсе java.sql.CallableStatement.  
  
 Начиная с версии [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] версии 3.0 драйвера JDBC, когда *sqlType* имеет тип Java.SQL.types.Time, поведение этого метода изменяется параметром **sendTimeAsDatetime** свойство соединения ([Заданию свойств соединения](../../../connect/jdbc/setting-the-connection-properties.md)) и [SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md).  
  
 Дополнительные сведения см. в разделе [java.sql.Time настройке как значения отправляются на сервер](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="see-also"></a>См. также:  
 [Метод registerOutParameter (SQLServerCallableStatement)](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md)   
 [Элементы SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
