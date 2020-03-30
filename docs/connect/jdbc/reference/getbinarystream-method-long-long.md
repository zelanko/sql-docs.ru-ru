---
title: Метод getBinaryStream (long, long) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 30bc8882-04b4-4efd-95e4-7d3a2a8c1d47
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5cc12f9e7ed7a83363766355fa5d340a459a332b
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67953650"
---
# <a name="getbinarystream-method-long-long"></a>Метод getBinaryStream (long, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает объект входного потока, который содержит часть значения BLOB, определяемую указанной начальной позицией и длиной.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.io.InputStream getBinaryStream(long pos, long length)  
```  
  
#### <a name="parameters"></a>Параметры  
 *pos*  
  
 Смещение до первого байта извлекаемого фрагмента значения.  
  
 *length*  
  
 Длина извлекаемого фрагмента значения в байтах.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Входной поток, содержащий данные большого двоичного объекта.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getBinaryStream задается с помощью метода getBinaryStream в интерфейсе java.sql.Blob.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [Элементы SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [Класс SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
