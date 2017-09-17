---
title: "Поместите метод (byte, long) | Документы Microsoft"
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
- SQLServerBlob.position (byte[], long)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 787412c2-4342-49c8-9ca2-7a9ddcd3277c
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6d6a9eaec4548bbeff5e6c0879240f783301d211
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="position-method-byte-long"></a>Поместите метод (byte, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает положение указанного шаблона в большом двоичном ОБЪЕКТЕ на основе заданного **байтов** массива шаблона и начального индекса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public long position(byte[] bPattern,  
                     long start)  
```  
  
#### <a name="parameters"></a>Параметры  
 *bPattern*  
  
 Шаблон для поиска.  
  
 *Запуск*  
  
 Индекс, с которого начинается поиск.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект **длинные** значение позиции, где был обнаружен шаблон, или -1, если он не найден.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод позиция указывается с помощью метода позиции в интерфейсе java.sql.Blob.  
  
## <a name="see-also"></a>См. также:  
 [Поместите метод &#40; SQLServerBlob &#41;](../../../connect/jdbc/reference/position-method-sqlserverblob.md)   
 [Методы SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [Элементы SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [Класс SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
