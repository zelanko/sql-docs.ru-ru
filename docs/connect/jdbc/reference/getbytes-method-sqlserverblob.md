---
title: Метод getBytes (SQLServerBlob) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerBlob.getBytes
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: bea1b810-b5c1-466d-bdc4-561468214632
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c4c7891c6d7454e0397406f9391fdfb60d0f0fc7
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "68213718"
---
# <a name="getbytes-method-sqlserverblob"></a>Метод getBytes (SQLServerBlob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает данные большого двоичного объекта в виде массива байтов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public byte[] getBytes(long pos,  
                       int length)  
```  
  
#### <a name="parameters"></a>Параметры  
 *pos*  
  
 Начальная позиция (отсчет с 1, а не с 0).  
  
 *length*  
  
 Длина получаемых данных.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Массив **byte**, содержащий запрошенные данные.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Метод getBytes определен с помощью метода getBytes в интерфейсе java.sql.Blob.  
  
 Если длина большого двоичного объекта равна нулю или имеет значение NULL, то при попытке получить ровно 0 байт в позиции 1 возвращается пустой массив **byte** (массив длиной 0).  
  
 Если длина большого двоичного объекта равна нулю или имеет значение NULL, то при попытке получить данные любой длины в позиции, отличной от 1, будет вызвано исключение позиции.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [Элементы SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [Класс SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
