---
title: "Метод getColumnType (SQLServerResultSetMetaData) | Документы Microsoft"
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
- SQLServerResultSetMetaData.getColumnType
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 81815a41-9265-4574-a4d8-f6341a68d9fd
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ad090a3ad5377be43f0c91febb79cfbfc56b5330
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getcolumntype-method-sqlserverresultsetmetadata"></a>Метод getColumnType (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает тип SQL указанного столбца.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getColumnType(int column)  
```  
  
#### <a name="parameters"></a>Параметры  
 *столбец*  
  
 **Int** , указывающее индекс столбца.  
  
## <a name="return-value"></a>Возвращаемое значение  
 **Int** , указывающее тип JDBC, определенный в java.sql.Types.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Это getcolumntype-метод определяется в getcolumntype-метод в интерфейсе java.sql.ResultSetMetaData.  
  
 [!INCLUDE[msCoName](../../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Версии 3.0 драйвера JDBC поведение изменилось в столбце DATA_TYPE. В разделе [SQLServerDatabaseMetaData.getColumns](../../../connect/jdbc/reference/getcolumns-method-sqlserverdatabasemetadata.md) для получения дополнительной информации.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [Класс SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  

