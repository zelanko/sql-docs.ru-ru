---
title: "Метод getSubString (SQLServerClob) | Документы Microsoft"
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
- SQLServerClob.getSubString
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: bf915590-a883-4403-befa-5b5bb42f34d8
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0030ce1e83feaa1a619fa9ead2bac3dfec4ccf6d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getsubstring-method-sqlserverclob"></a>Метод getSubString (SQLServerClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает копию указанной подстроки в объекте CLOB по заданной начальной позиции и числу символов для копирования.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getSubString(long pos,  
                                     int length)  
```  
  
#### <a name="parameters"></a>Параметры  
 *POS*  
  
 Первый символ извлекаемой подстроки. Первый символ находится в позиции 1.  
  
 *length*  
  
 Количество копируемых последовательных символов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект **строка** , указанной подстроки в CLOB.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getSubString указывается с помощью метода getSubString в интерфейсе java.sql.Clob.  
  
 При попытке получить ноль символов из объекта CLOB со значением NULL или с нулевой длиной возвращается пустая строка. При попытке получить символы любой длины, начиная с позиции, отличной от 1, в объекте CLOB нулевой длины вызывается исключение позиции.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [Элементы SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [Класс SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  

