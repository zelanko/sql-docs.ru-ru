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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cc915680afeb93a2eb20b94e83b87281baf5cfd6
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80901840"
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
  
  
