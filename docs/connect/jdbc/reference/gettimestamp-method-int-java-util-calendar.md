---
title: Метод getTimestamp (int, java.util.Calendar) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getTimestamp (int, java.util.Calendar)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 161c559a-8651-44ba-a914-15eb6a612417
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 50aa202837bee9e091cbb2ad31f56da6ea15eef0
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67978869"
---
# <a name="gettimestamp-method-int-javautilcalendar"></a>Метод getTimestamp (int, java.util.Calendar)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает значение указанного параметра в виде объекта java.sql.Timestamp на языке программирования Java по индексу параметра, используя указанный объект Calendar.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.Timestamp getTimestamp(int index,  
                                       java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>Параметры  
 *index*  
  
 Значение типа **int**, указывающее индекс параметра.  
  
 *cal*  
  
 Объект Calendar.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект Timestamp.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getTimestamp определен с помощью метода getTimestamp в интерфейсе java.sql.CallableStatement.  
  
 Этот метод возвращает значения только из столбцов [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]datetime**и**smalldatetime**в**.  
  
## <a name="see-also"></a>См. также:  
 [Метод getTimestamp (SQLServerCallableStatement)](../../../connect/jdbc/reference/gettimestamp-method-sqlservercallablestatement.md)   
 [Элементы SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
