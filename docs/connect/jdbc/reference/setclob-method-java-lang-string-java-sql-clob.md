---
title: Метод setClob (java.lang.String, java.sql.Clob) | Документы Microsoft
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
ms.assetid: 256b5f55-7a6d-44fb-9a09-19fa39f19c35
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 05c8165a2b4a9181d9e1273651e4a92db235852f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="setclob-method-javalangstring-javasqlclob"></a>Метод setClob (java.lang.String, java.sql.Clob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Присваивает указанному параметру указанный объект Clob.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setClob(java.lang.String parameterName,  
            java.sql.Clob x)  
```  
  
#### <a name="parameters"></a>Параметры  
 *Имя_параметра*  
  
 Объект **строка** , содержащее имя параметра.  
  
 *x*  
  
 Объект Clob.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод setClob указывается с помощью метода setClob в интерфейсе java.sql.CallableStatement.  
  
## <a name="see-also"></a>См. также  
 [Метод setClob &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/setclob-method-sqlservercallablestatement.md)   
 [Элементы SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
