---
title: "Метод deletesAreDetected (SQLServerDatabaseMetaData) | Документы Microsoft"
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
- SQLServerDatabaseMetaData.deletesAreDetected
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 73f3d994-bbd7-43d2-8b64-50057e278983
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9078379a3e1f338c194849a7f3066bdab12a47ee
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="deletesaredetected-method-sqlserverdatabasemetadata"></a>Метод deletesAreDetected (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает ли удаление видимой строки могут быть обнаружены путем вызова [rowDeleted](../../../connect/jdbc/reference/rowdeleted-method-sqlserverresultset.md) метод [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) класса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean deletesAreDetected(int type)  
```  
  
#### <a name="parameters"></a>Параметры  
 *type*  
  
 **Int** , указывающее тип результирующего набора, которое может быть одним из следующих значений, определенных в java.sql.ResultSet или SQLServerResultSet:  
  
## <a name="javasqlresultset-types"></a>Типы java.sql.ResultSet  
 TYPE_FORWARD_ONLY  
  
 TYPE_SCROLL_SENSITIVE  
  
 TYPE_SCROLL_INSENSITIVE  
  
## <a name="sqlserverresultset-types"></a>Типы SQLServerResultSet  
 TYPE_SS_SCROLL_STATIC  
  
 TYPE_SS_SCROLL_KEYSET  
  
 TYPE_SS_DIRECT_FORWARD_ONLY  
  
 TYPE_SS_SERVER_CURSOR_FORWARD_ONLY  
  
 TYPE_SS_SCROLL_DYNAMIC  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** , если заменяется удаленную строку. **false** при удалении строка полностью удаляется.  
  
 При использовании [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] базы данных, этот метод возвращает **true** для курсоров TYPE_SS_SCROLL_KEYSET и **false** для всех других типов результирующего набора.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод deletesAreDetected указывается с помощью метода deletesAreDetected в интерфейсе java.sql.DatabaseMetaData.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]выявляет удаленные строки для всех обновляемых типов курсора, хотя выявление является временным для однопроходных и динамических курсоров.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
