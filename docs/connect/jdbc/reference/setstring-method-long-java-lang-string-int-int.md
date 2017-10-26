---
title: "Метод setString (long, java.lang.String, int, int) | Документы Microsoft"
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
- SQLServerClob.setString (long, java.lang.String, int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9fb59b09-e825-46a6-ba5d-85d4a8dc143a
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 362cd4df54ee5ad826d2313341cd9ba4c7253546
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setstring-method-long-javalangstring-int-int"></a>Метод setString (long, java.lang.String, int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Записывает заданную строку в объект CLOB, начиная с заданной позиции, по заданному смещению и длине.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int setString(long pos,  
                     java.lang.String str,  
                     int offset,  
                     int len)  
```  
  
#### <a name="parameters"></a>Параметры  
 *POS*  
  
 Позиция, с которой начинается запись в объект CLOB.  
  
 *STR*  
  
 Строка для записи в объект CLOB.  
  
 *Смещение*  
  
 Смещение в строке, с которого начинается считывание символов.  
  
 *функция Len*  
  
 Количество записываемых символов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Количество записанных символов.  
  
## <a name="exceptions"></a>Исключения  
 java.sql.SQLException  
  
## <a name="remarks"></a>Замечания  
 Этот метод setString задается с помощью метода setString в интерфейсе java.sql.Clob.  
  
 Символьные данные перезаписываются, начиная с указанной позиции, и могут превысить исходную длину объекта CLOB. Если указать значение позиции+1, будет добавлена строка. Если указать значение позиции+2 и более (либо нулевое или отрицательное значение), то создается ошибка позиции.  
  
## <a name="see-also"></a>См. также:  
 [Метод setString &#40; SQLServerClob &#41;](../../../connect/jdbc/reference/setstring-method-sqlserverclob.md)   
 [Методы SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [Элементы SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [Класс SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  

