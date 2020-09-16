---
description: Метод getLogWriter (SQLServerDataSource)
title: Метод getLogWriter (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getLogWriter
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: cde41743-1a5d-4930-91b3-4e5fccc1bc36
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bec90cfe08948535b11b7d2432778b1e0be13ddb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88435726"
---
# <a name="getlogwriter-method-sqlserverdatasource"></a>Метод getLogWriter (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Этот метод предназначен только для внутреннего использования. Дополнительные сведения о ведении журнала см. в статье о [трассировке операций драйвера](../../../connect/jdbc/tracing-driver-operation.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.io.PrintWriter getLogWriter()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект PrintWriter.  
  
## <a name="remarks"></a>Remarks  
 Этот метод getLogWriter задается с помощью метода getLogWriter в интерфейсе javax.sql.DataSource.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
