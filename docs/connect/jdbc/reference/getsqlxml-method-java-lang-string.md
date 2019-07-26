---
title: Метод getSQLXML (java.lang.String) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: f56b192a-3255-4215-b552-8e494fbca083
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 125584fd3ad858a4242f6d85e755b3ec04e50ab1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67979642"
---
# <a name="getsqlxml-method-javalangstring"></a>Метод getSQLXML (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение указанного параметра в виде объекта SQLXML по имени параметра.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final java.sql.SQLXML getSQLXML(java.lang.String parameterName)  
```  
  
#### <a name="parameters"></a>Параметры  
 *parameterName*  
  
 Значение **String**, которое указывает имя параметра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Асклксмлобжект.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Метод getSQLXML определен с помощью метода getSQLXML в интерфейсе java.sql.CallableStatement.  
  
## <a name="see-also"></a>См. также:  
 [Метод getSQLXML (SQLServerCallableStatement)](../../../connect/jdbc/reference/getsqlxml-method-sqlservercallablestatement.md)   
 [Элементы SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
