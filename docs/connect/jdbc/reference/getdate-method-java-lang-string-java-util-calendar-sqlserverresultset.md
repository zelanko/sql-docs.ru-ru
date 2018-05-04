---
title: столбец getDate метод (java.util.Calendar) | Документы Microsoft
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
ms.topic: conceptual
apiname:
- SQLServerResultSet.getDate (java.lang.String, java.util.Calendar)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3fa2a72a-7499-44ec-8f76-a8e646e0190c
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 422061d9a42aaa6373016a61fa6f9b24c6d49d67
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="getdate-method-javalangstring-javautilcalendar-sqlserverresultset"></a>Метод getDate (java.lang.String, java.util.Calendar) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает значение имени заданного столбца в текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта в виде объекта java.sql.Date на языке Java, языке программирования, используя указанный объект календаря.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.Date getDate(java.lang.String colName,  
                             java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>Параметры  
 *ColName*  
  
 Объект **строка** , содержащее имя столбца.  
  
 *Клиентская лицензия*  
  
 Объект календаря.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект Date.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getDate указывается с помощью метода getDate в интерфейсе java.sql.ResultSet.  
  
 Этот метод возвращает допустимую часть даты [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] тип данных datetime или smalldatetime, а часть времени, значение времени Java — 00:00 (полночь) в часовом поясе указанного календаря.  
  
## <a name="see-also"></a>См. также  
 [Метод getDate &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getdate-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
