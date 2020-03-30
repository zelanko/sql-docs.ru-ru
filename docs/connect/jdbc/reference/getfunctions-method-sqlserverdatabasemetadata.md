---
title: Метод getFunctions (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 44335cbd-c84d-4ef3-a6a1-fca7eb7ec768
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b799fb56207294041c52fe455ad2acceff508d3a
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67982953"
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
 *catalog*  
  
 Имя каталога в базе данных. Если это пустая строка, то результат включает функции, доступные без каталога. Если это значение **NULL**, то имя каталога не используется для поиска.  
  
 *schemaPattern*  
  
 Имя схемы. Если это пустая строка, то результат включает функции, доступные без схемы. Если это значение **NULL**, то имя схемы не используется для поиска.  
  
 *functionNamePattern*  
  
 Имя функции.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getFunctions определен с помощью метода getFunctions в интерфейсе java.sql.DatabaseMetaData.  
  
 Этот метод возвращает только те системные и пользовательские функции, которые соответствуют указанному имени схемы и функции.  
  
> [!IMPORTANT]  
>  Возвращаемый результирующий набор может содержать функции, для выполнения которых у вызывающего пользователя отсутствуют разрешения.  
  
 Все описания функции содержат следующие столбцы:  
  
|Имя|Тип|Description|  
|----------|----------|-----------------|  
|FUNCTION_CAT|**String**|Имя базы данных, в которой находится указанная функция.|  
|FUNCTION_SCHEM|**String**|Имя схемы, в которой находится указанная функция.|  
|FUNCTION_NAME|**String**|Имя функции.|  
|NUM_INPUT_PARAMS|**int**|Зарезервировано для использования в будущем, в настоящий момент возвращает значение -1.|  
|NUM_OUTPUT_PARAMS|**int**|Зарезервировано для использования в будущем, в настоящий момент возвращает значение -1.|  
|NUM_RESULT_SETS|**int**|Зарезервировано для использования в будущем, в настоящий момент возвращает значение -1.|  
|ПРИМЕЧАНИЯ|**String**|Комментарии к функции.|  
|FUNCTION_TYPE|**short**|Тип функции. Может иметь одно из следующих значений.<br /><br /> SQL_PT_UNKNOWN (0)<br /><br /> SQL_PT_PROCEDURE (1)<br /><br /> SQL_PT_FUNCTION (2)|  
  
 Все описания в возвращенном результирующем наборе упорядочены с помощью FUNCTION_CAT, FUNCTION_SCHEM, FUNCTION_NAME и SPECIFIC_NAME.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
