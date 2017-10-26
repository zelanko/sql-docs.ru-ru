---
title: "Метод getFunctions (SQLServerDatabaseMetaData) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 44335cbd-c84d-4ef3-a6a1-fca7eb7ec768
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b0482197b706ac4e604fe6e4402bebbe1bc793fc
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getfunctions-method-sqlserverdatabasemetadata"></a>Метод getFunctions (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает описание системных и пользовательских функций.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public ResultSet getFunctions(java.lang.String catalog,  
                       java.lang.String schemaPattern,  
                       java.lang.String functionNamePattern)  
```  
  
#### <a name="parameters"></a>Параметры  
 *каталог*  
  
 Имя каталога в базе данных. Если это пустая строка, то результат включает функции, доступные без каталога. Если это **null**, имя каталога не используется для поиска.  
  
 *schemaPattern*  
  
 Имя схемы. Если это пустая строка, то результат включает функции, доступные без схемы. Если это **null**, имя схемы не используется для поиска.  
  
 *functionNamePattern*  
  
 Имя функции.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getFunctions указывается с помощью метода getFunctions в интерфейсе java.sql.DatabaseMetaData.  
  
 Этот метод возвращает только те системные и пользовательские функции, которые соответствуют указанному имени схемы и функции.  
  
> [!IMPORTANT]  
>  Возвращаемый результирующий набор может содержать функции, для выполнения которых у вызывающего пользователя отсутствуют разрешения.  
  
 Все описания функции содержат следующие столбцы:  
  
|Имя|Тип|Description|  
|----------|----------|-----------------|  
|FUNCTION_CAT|**Строковые значения**|Имя базы данных, в которой находится указанная функция.|  
|FUNCTION_SCHEM|**Строковые значения**|Имя схемы, в которой находится указанная функция.|  
|FUNCTION_NAME|**Строковые значения**|Имя функции.|  
|NUM_INPUT_PARAMS|**int**|Зарезервировано для использования в будущем, в настоящий момент возвращает значение -1.|  
|NUM_OUTPUT_PARAMS|**int**|Зарезервировано для использования в будущем, в настоящий момент возвращает значение -1.|  
|NUM_RESULT_SETS|**int**|Зарезервировано для использования в будущем, в настоящий момент возвращает значение -1.|  
|REMARKS|**Строковые значения**|Комментарии к функции.|  
|FUNCTION_TYPE|**короткий**|Тип функции. Может иметь одно из следующих значений.<br /><br /> SQL_PT_UNKNOWN (0)<br /><br /> SQL_PT_PROCEDURE (1)<br /><br /> SQL_PT_FUNCTION (2)|  
  
 Все описания в возвращенном результирующем наборе упорядочены с помощью FUNCTION_CAT, FUNCTION_SCHEM, FUNCTION_NAME и SPECIFIC_NAME.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

