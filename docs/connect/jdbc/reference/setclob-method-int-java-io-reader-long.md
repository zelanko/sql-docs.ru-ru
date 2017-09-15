---
title: "Метод setClob (int, java.io.Reader, long) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 157882dd-1a96-4501-a895-46e88a49266e
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ab3cc5c9342b1e115a73d6616d9fe99992c4a869
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setclob-method-int-javaioreader-long"></a>Метод setClob (int, java.io.Reader, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Присваивает указанному параметру указанный объект чтения, который находится на заданное число знаков.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setClob(int parameterIndex,  
                          java.io.Reader reader,  
                          long length)  
```  
  
#### <a name="parameters"></a>Параметры  
 *parameterIndex*  
  
 **Int** , указывающее индекс параметра.  
  
 *Модуль чтения*  
  
 Объект модуля чтения.  
  
 *length*  
  
 Объект **длинные** указывает число символов в значении параметра.  
  
## <a name="remarks"></a>Замечания  
 Этот метод setClob указывается с помощью метода setClob в интерфейсе java.sql.PreparedStatement.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="see-also"></a>См. также:  
 [Метод setClob &#40; SQLServerPreparedStatement &#41;](../../../connect/jdbc/reference/setclob-method-sqlserverpreparedstatement.md)   
 [Элементы SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
