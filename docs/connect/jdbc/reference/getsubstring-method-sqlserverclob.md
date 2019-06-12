---
title: Метод getSubString (SQLServerClob) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerClob.getSubString
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: bf915590-a883-4403-befa-5b5bb42f34d8
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 3404d7e31cdc5ed82a4a2c57af1a05354104d4bc
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66787459"
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
 *Торговых терминалов*  
  
 Первый символ извлекаемой подстроки. Первый символ находится в позиции 1.  
  
 *length*  
  
 Количество копируемых последовательных символов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **String**, указывающее подстроку в объекте CLOB.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getSubString указывается с помощью метода getSubString в интерфейсе java.sql.Clob.  
  
 При попытке получить ноль символов из объекта CLOB со значением NULL или с нулевой длиной возвращается пустая строка. При попытке получить символы любой длины, начиная с позиции, отличной от 1, в объекте CLOB нулевой длины вызывается исключение позиции.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [Элементы SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [Класс SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
