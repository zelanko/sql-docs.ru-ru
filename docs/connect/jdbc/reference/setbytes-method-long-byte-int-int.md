---
title: "Метод (long, byte, int, int) setBytes | Документы Microsoft"
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
- SQLServerBlob.setBytes (long.byte[], int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7def226c-b211-459e-8c1a-08592d75d4a4
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5aa6587a6877143486aa5b053311694229f10a36
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setbytes-method-long-byte-int-int"></a>setBytes метод (long, byte, int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Целиком или частично записывает заданный массив байтов в большой двоичный объект, начиная с заданной позиции и используя заданное смещение и длину. Затем возвращает число записанных байтов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int setBytes(long pos,  
                    byte[] bytes,  
                    int offset,  
                    int len)  
```  
  
#### <a name="parameters"></a>Параметры  
 *POS*  
  
 Позиция (считая с 1) в большом двоичном объекте, с которой начинается запись данных.  
  
 *байт*  
  
 Массив байтов для записи в большой двоичный объект.  
  
 *Смещение*  
  
 Смещение в байтах массива, где начинается чтение данных из **байтов** массива.  
  
 *функция Len*  
  
 Число байтов, которые должны считываться из массива байтов в большой двоичный объект.  
  
## <a name="return-value"></a>Возвращаемое значение  
 **Int** содержит число записанных байтов.  
  
## <a name="exceptions"></a>Исключения  
 java.sql.SQLException  
  
## <a name="remarks"></a>Замечания  
 Этот метод setBytes указывается с помощью метода setBytes в интерфейсе java.sql.Blob.  
  
 Данные перезаписываются, начиная с указанной позиции, и могут превысить исходную длину большого двоичного объекта. Если указать значение позиции+1, будут добавлены байты. Если передается значение позиции+2 и более (либо нулевое или отрицательное значение), то создается ошибка позиции. Передача нулевой длины **байтов** массив будет возвращено нулевое значение, так как байты не были записаны.  
  
## <a name="see-also"></a>См. также:  
 [Метод setBytes &#40; SQLServerBlob &#41;](../../../connect/jdbc/reference/setbytes-method-sqlserverblob.md)   
 [Методы SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [Элементы SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [Класс SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  

