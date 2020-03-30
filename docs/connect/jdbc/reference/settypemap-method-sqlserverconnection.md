---
title: Метод setTypeMap (SQLServerConnection) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.setTypeMap
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: bffd20a6-1310-44b0-9602-974500481fa6
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a188d5d98aca0418a2452f29912f62604f3ffa90
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67972172"
---
# <a name="settypemap-method-sqlserverconnection"></a>Метод setTypeMap (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Устанавливает указанный объект TypeMap в качестве сопоставления типов для данного объекта [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).  
  
> [!NOTE]  
>  Сейчас этот метод не поддерживается [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setTypeMap(java.util.Map map)  
```  
  
#### <a name="parameters"></a>Параметры  
 *map*  
  
 Объект TypeMap.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод TypeMap задается с помощью метода TypeMap в интерфейсе java.sql.Connection.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
