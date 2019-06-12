---
title: Метод setObject (java.lang.String, java.lang.Object, int, int) | Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.setObject (java.lang.String, java.lang.Object, int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 16f5f09a-51b5-423a-b52d-8c2eaa04e9ff
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: aa535d31edb1d6f94bd06f41eaffda5f1970841a
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66788242"
---
# <a name="setobject-method-javalangstring-javalangobject-int-int"></a>Метод setObject (java.lang.String, java.lang.Object, int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Устанавливает значение указанного параметра по заданному объекту, целевому типу и масштабу.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setObject(java.lang.String sCol,  
                      java.lang.Object o,  
                      int n,  
                      int m)  
```  
  
#### <a name="parameters"></a>Параметры  
 *sCol*  
  
 Значение типа **String**, содержащее имя параметра.  
  
 *o*  
  
 Значение **Object**.  
  
 *n*  
  
 Значение типа **int**, указывающее целевой тип, определенный в java.sql.Types.  
  
 *m*  
  
 Значение типа **int**, указывающее количество разрядов справа от десятичного разделителя. Этот параметр не учитывается для всех типов, кроме NUMERIC и DECIMAL.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод setObject указывается методом setObject в интерфейсе java.sql.CallableStatement.  
  
 Начиная с версии [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] версии 3.0 драйвера JDBC поведение этого метода изменяется параметром **sendTimeAsDatetime** свойство соединения ([заданию свойств соединения](../../../connect/jdbc/setting-the-connection-properties.md)) и [ SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md).  
  
 Дополнительные сведения см. в разделе [java.sql.Time настройке как значения отправляются на сервер](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="see-also"></a>См. также:  
 [Метод setObject (SQLServerCallableStatement)](../../../connect/jdbc/reference/setobject-method-sqlservercallablestatement.md)   
 [Элементы SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
