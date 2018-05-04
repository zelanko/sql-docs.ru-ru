---
title: Метод для входного потока setBinaryStream) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 339c8277-2d08-4094-9fa9-26c8ad3e7348
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2b338cd3fe41db8a5608029f618f3690df271526
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="setbinarystream-method-javalangstring-javaioinputstream"></a>Метод setBinaryStream (java.lang.String, java.io.InputStream)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Устанавливает для указанного параметра указанное значение входного потока.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setBinaryStream(java.lang.String parameterName,  
                            java.io.InputStream x)  
```  
  
#### <a name="parameters"></a>Параметры  
 *Имя_параметра*  
  
 Объект **строка** , содержащее имя параметра.  
  
 *x*  
  
 Объект, InputStream.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод setBinaryStream указывается с помощью метода setBinaryStream в интерфейсе java.sql.CallableStatement.  
  
## <a name="see-also"></a>См. также  
 [setBinaryStream &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/setbinarystream-sqlservercallablestatement.md)   
 [Элементы SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
