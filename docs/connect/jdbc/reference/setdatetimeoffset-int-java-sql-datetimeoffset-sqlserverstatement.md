---
title: "setDateTimeOffset (int, java.sql.DateTimeOffset) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8b6e380-6b53-489b-be73-73fcb5258269
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b9b18af7823f8d02f80ba636fe57b5d6cd807770
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="setdatetimeoffsetint-javasqldatetimeoffset-sqlserverstatement"></a>Метод setDateTimeOffset(int, java.sql.DateTimeOffset) (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Устанавливает указанный параметр в заданное значение типа DateTimeOffset.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setDateTimeOffset(int parameterIndex, DateTimeOffset dateTime)  
```  
  
#### <a name="parameters"></a>Параметры  
 *parameterIndex*  
  
 Индекс задаваемого столбца.  
  
 *dateTimeOffset*  
  
 Объект DateTimeOffset.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 DateTimeOffset имеет формат «ГГГГ-ММ-ДД ЧЧ-ММ-СС[.ннннннн] [+][-] ЧЧ:ММ». Следующая таблица приводится в справочных целях.  
  
|Тип SQL|Insert|  
|--------------|------------|  
|datetime|Могут вставляться только значения в формате «ГГГГ-ММ-ДД чч:мм:сс[.ннн]»|  
|smalldatetime|Могут вставляться только значения в формате «ГГГГ-ММ-ДД чч:мм:сс»|  
|Time|Могут вставляться только значения в формате «чч:мм:сс[.ннннннн]»|  
|Дата|Могут вставляться только значения в формате «ГГГГ-ММ-ДД»|  
|datetime2|Могут вставляться только значения в формате «ГГГГ-ММ-ДД чч:мм:сс[.ннннннн]»|  
  
## <a name="see-also"></a>См. также:  
 [getDateTimeOffset &#40; SQLServerResultSet &#41;](../../../connect/jdbc/reference/getdatetimeoffset-sqlserverresultset.md)   
 [Члены SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
