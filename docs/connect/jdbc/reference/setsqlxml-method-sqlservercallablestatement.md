---
description: Метод setSQLXML (SQLServerCallableStatement)
title: Метод setSQLXML (SQLServerCallableStatement) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: de095cb3-1111-4154-8996-3c2e529e3000
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e41da20bd3e3f046f5ece7e2c190a3a81c70e861
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88458306"
---
# <a name="setsqlxml-method-sqlservercallablestatement"></a>Метод setSQLXML (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает указанному параметру значение заданного объекта SQLXML.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setSQLXML(java.lang.String parameterName,  
                            java.sql.SQLXML xmlObject)  
```  
  
#### <a name="parameters"></a>Параметры  
 *parameterName*  
  
 Значение **String**, которое указывает на имя параметра.  
  
 *xmlObject*  
  
 Объект SQLXML, содержащий значение параметра.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод setSQLXML определен с помощью метода setSQLXML в интерфейсе java.sql.CallableStatement.  
  
## <a name="see-also"></a>См. также:  
 [Члены SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
