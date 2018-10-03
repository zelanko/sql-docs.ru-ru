---
title: Метод getDate (int, java.util.Calendar) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getDate (int, java.util.Calendar)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 38ce7b75-2623-4eff-bc18-8cf7193adec8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c9d436c323415465f95760a92795e4bace50765c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47849772"
---
# <a name="getdate-method-int-javautilcalendar"></a>Метод getDate (int, java.util.Calendar)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение указанного параметра в виде объекта java.sql.Date на языке программирования Java по указанному индексу параметра и объекту Calendar.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.Date getDate(int index,  
                             java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>Параметры  
 *index*  
  
 Значение типа **int**, указывающее индекс параметра.  
  
 *Клиентская лицензия*  
  
 Объект календаря.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект Date.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getDate указывается методом getDate в интерфейсе java.sql.CallableStatement.  
  
 Этот метод возвращает допустимую часть даты для типа данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **datetime** или **smalldatetime**, а часть времени имеет начальное значение времени Java — 00:00 (полночь).  
  
## <a name="see-also"></a>См. также:  
 [Метод getDate (SQLServerCallableStatement)](../../../connect/jdbc/reference/getdate-method-sqlservercallablestatement.md)   
 [Элементы SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
