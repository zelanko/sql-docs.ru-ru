---
title: Метод setSQLXML (SQLServerCallableStatement) | Документы Microsoft
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
ms.assetid: de095cb3-1111-4154-8996-3c2e529e3000
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 19741a95c1a335abd63d61d74a4faf2c6affed97
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="setsqlxml-method-sqlservercallablestatement"></a>Метод setSQLXML (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Присваивает указанному параметру указанный объект SQLXML.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setSQLXML(java.lang.String parameterName,  
                            java.sql.SQLXML xmlObject)  
```  
  
#### <a name="parameters"></a>Параметры  
 *Имя_параметра*  
  
 **Строка** , указывающее имя параметра.  
  
 *xmlObject*  
  
 Объект SQLXML, содержащее значение параметра.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод setSQLXML указывается с помощью метода setSQLXML в интерфейсе java.sql.CallableStatement.  
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
