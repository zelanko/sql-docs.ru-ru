---
title: "Метод setObject (java.lang.String, java.lang.Object, int, int) | Документы Microsoft"
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
- SQLServerCallableStatement.setObject (java.lang.String, java.lang.Object, int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 16f5f09a-51b5-423a-b52d-8c2eaa04e9ff
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 059dd6c2a901b4846373a4ee06ed5d51b78e7eab
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

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
  
 Объект **строка** , содержащее имя параметра.  
  
 **  
  
 **Объекта** значение.  
  
 *n*  
  
 **Int** , указывающее тип объекта, определенный в java.sql.Types.  
  
 *m*  
  
 **Int** указывает количество цифр справа от десятичной запятой. Этот параметр не учитывается для всех типов, кроме NUMERIC и DECIMAL.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод setObject указывается с помощью метода setObject в интерфейсе java.sql.CallableStatement.  
  
 Начиная с версии [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] версии 3.0 драйвера JDBC поведение данного метода изменяется с **sendTimeAsDatetime** свойство соединения ([задание свойств соединения](../../../connect/jdbc/setting-the-connection-properties.md)) и [ SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md).  
  
 Дополнительные сведения см. в разделе [как настройка java.sql.Time отправляются на сервер](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="see-also"></a>См. также:  
 [Метод setObject &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/setobject-method-sqlservercallablestatement.md)   
 [Члены SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
