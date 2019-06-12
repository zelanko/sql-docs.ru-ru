---
title: Метод setBytes (long, byte) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerBlob.setBytes (long.byte[])
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ffb8f107-0f9d-4410-957f-62b718e1e872
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: f0d47be46aac25807fd9f97bb3ee40cf96ffd4fd
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66797635"
---
# <a name="setbytes-method-long-byte"></a>Метод setBytes (long, byte)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Записывает указанный массив байтов в большой двоичный объект, начиная с указанной позиции, а затем возвращает число записанных байтов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int setBytes(long pos,  
                    byte[] bytes)  
```  
  
#### <a name="parameters"></a>Параметры  
 *Торговых терминалов*  
  
 Позиция (считая с 1) в большом двоичном объекте, с которой начинается запись данных.  
  
 *bytes*  
  
 Массив байтов для записи в большой двоичный объект.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **long**, указывающее число записанных байтов.  
  
## <a name="exceptions"></a>Исключения  
 java.sql.SQLException  
  
## <a name="remarks"></a>Remarks  
 Метод setBytes определен с помощью метода setBytes в интерфейсе java.sql.Blob.  
  
 Данные перезаписываются, начиная с указанной позиции, и могут превысить исходную длину большого двоичного объекта. Если указать значение позиции+1, будут добавлены байты. Если передается значение позиции+2 и более (либо нулевое или отрицательное значение), то создается ошибка позиции. Если передается массив **byte** нулевой длины, то будет возвращено нулевое значение, поскольку не записан ни один байт.  
  
## <a name="see-also"></a>См. также:  
 [Метод setBytes &#40;SQLServerBlob&#41;](../../../connect/jdbc/reference/setbytes-method-sqlserverblob.md)   
 [Методы SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [Элементы SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [Класс SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
