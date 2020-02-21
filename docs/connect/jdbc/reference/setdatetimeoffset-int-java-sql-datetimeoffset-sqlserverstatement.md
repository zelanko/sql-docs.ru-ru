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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 166c9ddbd4b5c11b3c032a5a4ecf43c95f183473
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67974539"
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
|DATETIME|Разрешена вставка значений только в формате: ГГГГ-ММ-ДД чч:мм:сс[.nnn]|  
|smalldatetime|Разрешена вставка значений только в формате: ГГГГ-ММ-ДД чч:мм:сс|  
|Time|Могут вставляться только значения в формате «чч:мм:сс[.ннннннн]»|  
|Дата|Разрешена вставка значений только в формате: ГГГГ-ММ-ДД|  
|datetime2|Разрешена вставка значений только в формате: ГГГГ-ММ-ДД чч:мм:сс[.nnnnnnn]|  
  
## <a name="see-also"></a>См. также:  
 [getDateTimeOffset (SQLServerResultSet)](../../../connect/jdbc/reference/getdatetimeoffset-sqlserverresultset.md)   
 [Элементы SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
