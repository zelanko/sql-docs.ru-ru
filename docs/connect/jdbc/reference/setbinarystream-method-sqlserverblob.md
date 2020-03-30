---
title: Метод setBinaryStream (SQLServerBlob) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerBlob.setBinaryStream
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: abcec31f-1a60-4765-9725-8cf7e9f1f8ab
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4555dfb9256f3ffe2ba61e82fe90307991a5a580
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67975092"
---
# <a name="setbinarystream-method-sqlserverblob"></a>Метод setBinaryStream (SQLServerBlob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает поток, который можно использовать для записи значения большого двоичного объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.io.OutputStream setBinaryStream(long pos)  
```  
  
#### <a name="parameters"></a>Параметры  
 *Pos*  
  
 Позиция, с которой начинается запись значения большого двоичного объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Выходной поток.  
  
## <a name="exceptions"></a>Исключения  
 java.sql.SQLException  
  
## <a name="remarks"></a>Remarks  
 Этот метод setBinaryStream задается с помощью метода setBinaryStream в интерфейсе java.sql.Blob.  
  
 Данные в большом двоичном объекте перезаписываются выходным потоком, начиная с указанной позиции, и могут превысить начальную длину большого двоичного объекта. Если указать значение позиции+1, будут добавлены байты. Если передается значение позиции+2 и более (либо нулевое или отрицательное значение), то создается ошибка позиции.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [Элементы SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [Класс SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
