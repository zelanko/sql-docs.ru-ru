---
title: "Метод getCharacterStream (long, long) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d70f502f-f60f-436a-83e6-797a0ed71bf3
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ba910c36ff82209a668ef6d96987330705703080
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getcharacterstream-method-long-long"></a>Метод getCharacterStream (long, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает **Clob** данных как объект чтения или в виде потока символов с указанной позицией и длиной.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.io.Reader getCharacterStream(long pos,  
                                         long length)  
```  
  
#### <a name="parameters"></a>Параметры  
 *POS*  
  
 Объект **длинные** , определяющее смещение до первого символа извлекаемого фрагмента значения.  
  
 *length*  
  
 Объект **длинные** , определяющее длину в символах для извлекаемого фрагмента значения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект чтения, который содержит **Clob** данных.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getCharacterStream указывается с помощью метода getCharacterStream в интерфейсе java.sql.Clob.  
  
## <a name="see-also"></a>См. также:  
 [Метод getCharacterStream &#40; SQLServerClob &#41;](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverclob.md)   
 [Методы SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [Элементы SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-members.md)  
  
  
