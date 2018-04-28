---
title: Метод (SQLServerResultSet) setFetchSize | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- SQLServerResultSet.setFetchSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 233bf4f8-4758-42d0-a80b-33e34fa78027
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2344b1701a66621665a4ea1179e74b602141918d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="setfetchsize-method-sqlserverresultset"></a>setFetchSize метод (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Дает указание относительно числа строк, которые должны быть извлечены из базы данных, при необходимости в дополнительных строках для данного драйвера JDBC [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setFetchSize(int rows)  
```  
  
#### <a name="parameters"></a>Параметры  
 *Строки*  
  
 **Int** , указывающее количество строк для выборки.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод setFetchSize указывается с помощью метода setFetchSize в интерфейсе java.sql.ResultSet.  
  
 Если указан нулевой размер выборки, то драйвер JDBC не учитывает это значение и оценивает предполагаемый размер выборки. Значение по умолчанию задается [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объекта, который создал результирующий набор. Размер выборки можно изменить в любой момент.  
  
 Этот метод изменяет размер выборки блока для серверных курсоров. Изменение вступает в силу при следующем вызове процедуры sp_cursorfetch драйвером JDBC. Если задать нулевой размер выборки, будет восстановлен тип выборки по умолчанию для используемого в данный момент типа курсора.  
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
