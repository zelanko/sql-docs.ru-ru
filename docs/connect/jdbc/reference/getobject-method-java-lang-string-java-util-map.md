---
title: "Метод getObject (java.lang.String, java.util.Map) | Документы Microsoft"
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
- SQLServerCallableStatement.getObject (java.lang.String, Java.util.Map)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e174eb81-d569-479e-a171-365cd6d44b6a
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ed49e85c4b4fcd08df293378aca147f05ab280d0
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getobject-method-javalangstring-javautilmap"></a>Метод getObject (java.lang.String, java.util.Map)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает значение указанного параметра в виде объекта в языке программирования Java по заданному имени параметра, используя заданный объект карты.  
  
> [!NOTE]  
>  Этот метод не поддерживается в настоящее время [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]. Этот метод всегда возвращает сопоставление по умолчанию.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.Object getObject(java.lang.String sCol,  
                                  java.util.Map m)  
```  
  
#### <a name="parameters"></a>Параметры  
 *sCol*  
  
 Объект **строка** , содержащее имя параметра.  
  
 *m*  
  
 Объект схемы.  
  
## <a name="return-value"></a>Возвращаемое значение  
 **Объекта** значение.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getObject указывается с помощью метода getObject в интерфейсе java.sql.CallableStatement.  
  
 Этот метод вернет значение данного столбца в виде объекта Java. Объект Java будет иметь заданный по умолчанию тип, соответствующий типу SQL Server столбца и сопоставленный встроенным типам, указанным в спецификации JDBC. Если значение SQL NULL, то драйвер вернет значение Java NULL.  
  
 Этот метод также может быть использован для чтения абстрактных типов данных, относящихся к базе данных. В JDBC 2.0 API возможности метода getObject расширены и поддерживают материализацию данных определяемых пользователем типов SQL. Если столбец содержит структурированное или уникальное значение, поведение данного метода является, как если бы он был вызов `getObject(columnIndex, this.getStatement().getConnection().getTypeMap())`.  
  
 Начиная с версии [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] драйвера JDBC 3.0:  
  
-   Значение типа **даты** будет возвращаться в виде объекта java.sql.Date.  
  
-   Значение типа **время** будет возвращаться в виде объекта java.sql.Time.  
  
-   Значение типа **datetime2** будет возвращаться в виде объекта java.sql.Timestamp.  
  
-   Значение типа **datetimeoffset** будет возвращаться в виде объекта microsoft.sql.DateTimeOffset.  
  
## <a name="see-also"></a>См. также:  
 [Метод getObject &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/getobject-method-sqlservercallablestatement.md)   
 [Члены SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  

