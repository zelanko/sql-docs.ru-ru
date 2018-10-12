---
title: Метод setLogWriter (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setLogWriter
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7a77d8ef-2211-4bf8-af35-020fc896c073
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5db83b67bf5abffd0ada384eedc0fd0ba8db24f8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47700802"
---
# <a name="setlogwriter-method-sqlserverdatasource"></a>Метод setLogWriter (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Этот метод предназначен только для внутреннего использования. Дополнительные сведения о ведении журнала см. в разделе [Tracing Driver Operation](../../../connect/jdbc/tracing-driver-operation.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setLogWriter(java.io.PrintWriter out)  
```  
  
#### <a name="parameters"></a>Параметры  
 *out*  
  
 Объект PrintWriter.  
  
## <a name="remarks"></a>Remarks  
 Этот метод setLogWriter указывается с помощью метода setLogWriter в интерфейсе javax.sql.DataSource.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
