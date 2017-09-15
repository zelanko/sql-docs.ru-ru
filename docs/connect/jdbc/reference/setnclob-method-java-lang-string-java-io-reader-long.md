---
title: "Метод setNClob (java.lang.String, java.io.Reader, long) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1b95ee7-7e82-418f-8f30-948589086f63
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: bb9938a611bea0db4f824d4cf95bfbbe6cfc9def
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setnclob-method-javalangstring-javaioreader-long"></a>Метод setNClob (java.lang.String, java.io.Reader, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Присваивает указанному параметру указанный объект чтения, равен указанному числу символов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setNClob(java.lang.String parameterName,  
              java.io.Reader reader,  
              long length)  
```  
  
#### <a name="parameters"></a>Параметры  
 *Имя_параметра*  
  
 Объект **строка** , содержащее имя параметра.  
  
 *Модуль чтения*  
  
 Объект модуля чтения.  
  
 *length*  
  
 Объект **длинные** указывает число символов в поток.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод следует использовать для **NCHAR**, **NVARCHAR**, **NTEXT**, и **XML** типы данных параметров.  
  
 Этот метод setNClob указывается с помощью метода setNClob в интерфейсе java.sql.CallableStatement.  
  
## <a name="see-also"></a>См. также:  
 [Метод setNClob &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/setnclob-method-sqlservercallablestatement.md)   
 [Элементы SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
