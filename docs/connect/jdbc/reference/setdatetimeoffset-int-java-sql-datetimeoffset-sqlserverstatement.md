---
title: setDateTimeOffset (int, java.sql.DateTimeOffset) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e8b6e380-6b53-489b-be73-73fcb5258269
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a45711b4f3007f0f3c91f271542784386db99379
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80927537"
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
  
## <a name="remarks"></a>Remarks  
 DateTimeOffset имеет формат «ГГГГ-ММ-ДД ЧЧ-ММ-СС[.ннннннн] [+][-] ЧЧ:ММ». Следующая таблица приводится в справочных целях.  
  
|Тип SQL|Вставить|  
|--------------|------------|  
|DATETIME|Могут вставляться только значения в формате «ГГГГ-ММ-ДД чч:мм:сс[.ннн]»|  
|smalldatetime|Могут вставляться только значения в формате «ГГГГ-ММ-ДД чч:мм:сс»|  
|Time|Могут вставляться только значения в формате «чч:мм:сс[.ннннннн]»|  
|Дата|Могут вставляться только значения в формате «ГГГГ-ММ-ДД»|  
|datetime2|Могут вставляться только значения в формате «ГГГГ-ММ-ДД чч:мм:сс[.ннннннн]»|  
  
## <a name="see-also"></a>См. также:  
 [getDateTimeOffset (SQLServerResultSet)](../../../connect/jdbc/reference/getdatetimeoffset-sqlserverresultset.md)   
 [Элементы SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
