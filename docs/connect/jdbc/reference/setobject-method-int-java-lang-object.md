---
title: "Метод setObject (int, java.lang.Object) | Документы Microsoft"
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
- SQLServerPreparedStatement.setObject (int, java.lang.Object)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 61f19faa-3006-4a1c-974c-55951e3b3000
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2116f0662e21e4cb38d60560a680e90e6b2321d9
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setobject-method-int-javalangobject"></a>Метод setObject (int, java.lang.Object)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Устанавливает значение указанного параметра по заданному объекту.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setObject(int index,  
                            java.lang.Object obj)  
```  
  
#### <a name="parameters"></a>Параметры  
 *Индекс*  
  
 **Int** указывает номер параметра.  
  
 *OBJ*  
  
 Объект.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод setObject указывается с помощью метода setObject в интерфейсе java.sql.PreparedStatement.  
  
 Перед вызовом этого метода setObject, приложение должно задать указанный параметр с помощью одного из следующих методов:  
  
-   Набор\<типа > методы класса SQLServerPreparedStatement или SQLServerCallableStatement  
  
-   SetNull методы класса SQLServerPreparedStatement или SQLServerCallableStatement  
  
-   [RegisterOutParameter](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md) метод класса SQLServerCallableStatement  
  
 В этом случае тип параметра задается автоматически. Если приложение вызывает этот метод setObject с obj, равным NULL, драйвер предполагает, тип параметра, который задан ранее вызванным методом.  
  
 Если значение obj равно NULL, а не сведения о типе для этого параметра можно определить, этот метод setObject преобразует указанный параметр в тип CHAR перед отправкой в базу данных.  
  
 Начиная с версии [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] версии 3.0 драйвера JDBC поведение данного метода изменяется с **sendTimeAsDatetime** свойство соединения ([задание свойств соединения](../../../connect/jdbc/setting-the-connection-properties.md)) и [ SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md).  
  
 Дополнительные сведения см. в разделе [как настройка java.sql.Time отправляются на сервер](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="see-also"></a>См. также:  
 [Метод setObject &#40; SQLServerPreparedStatement &#41;](../../../connect/jdbc/reference/setobject-method-sqlserverpreparedstatement.md)   
 [Члены SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Класс SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  

