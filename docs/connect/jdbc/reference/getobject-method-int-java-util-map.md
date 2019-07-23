---
title: Метод GetObject (int, Java. util. Map) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getObject (int, java.util.Map)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 164532be-7ed6-40fa-a273-dece4c8d72c4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5106bddd6cf71401be0f4a71dfaaf0406901a6cd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67981245"
---
# <a name="getobject-method-int-javautilmap"></a>Метод getObject (int, java.util.Map)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение заданного параметра в виде объекта на языке программирования Java по индексу параметра, используя указанный объект Map.  
  
> [!NOTE]  
>  Сейчас этот метод не поддерживается [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]. Этот метод всегда возвращает сопоставление по умолчанию.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.Object getObject(int index,  
                                  java.util.Map map)  
```  
  
#### <a name="parameters"></a>Параметры  
 *index*  
  
 Значение типа **int**, указывающее индекс параметра.  
  
 *map*  
  
 Объект Map.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **Object**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getObject определен с помощью метода getObject в интерфейсе java.sql.CallableStatement.  
  
 Этот метод вернет значение данного столбца в виде объекта Java. Объект Java будет иметь заданный по умолчанию тип, соответствующий типу SQL Server столбца и сопоставленный встроенным типам, указанным в спецификации JDBC. Если значение SQL NULL, то драйвер вернет значение Java NULL.  
  
 Этот метод также может быть использован для чтения абстрактных типов данных, относящихся к базе данных. В API JDBC 2.0 возможности метода getObject расширены и поддерживают материализацию данных определяемых пользователем типов SQL. Если в столбце содержится структурированное или уникальное значение, то выполнение этого метода будет аналогично вызову `getObject(columnIndex, this.getStatement().getConnection().getTypeMap())`.  
  
 Начиная с версии 3.0 драйвера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC действуют следующие правила:  
  
-   Значение типа date будет возвращаться в виде объекта java.sql.Date.  
  
-   Значение типа time будет возвращаться в виде объекта java.sql.Time.  
  
-   Значение типа datetime2 будет возвращаться в виде объекта java.sql.Timestamp.  
  
-   Значение типа datetimeoffset будет возвращаться в виде объекта microsoft.sql.DateTimeOffset.  
  
## <a name="see-also"></a>См. также:  
 [Метод getObject (SQLServerCallableStatement)](../../../connect/jdbc/reference/getobject-method-sqlservercallablestatement.md)   
 [Элементы SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
