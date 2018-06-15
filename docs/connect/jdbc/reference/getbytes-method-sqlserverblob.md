---
title: Метод getBytes (SQLServerBlob) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerBlob.getBytes
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: bea1b810-b5c1-466d-bdc4-561468214632
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7a872d042c0a96123cccffac5c5a6f8e2b686c4d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32830879"
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
 *POS*  
  
 Начальная позиция (отсчет с 1, а не с 0).  
  
 *длина*  
  
 Длина получаемых данных.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект **байтов** массив, содержащий запрошенные данные.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getBytes указывается с помощью метода getBytes в интерфейсе java.sql.Blob.  
  
 Если имеет значение null или иметь нулевую длину большого двоичного ОБЪЕКТА и попытайтесь получить ровно 0 байт в позиции 1, пустой **байтов** (массив длиной 0) возвращается массив.  
  
 Если длина большого двоичного объекта равна нулю или имеет значение NULL, то при попытке получить данные любой длины в позиции, отличной от 1, будет вызвано исключение позиции.  
  
## <a name="see-also"></a>См. также  
 [Методы SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [Элементы SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [Класс SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
