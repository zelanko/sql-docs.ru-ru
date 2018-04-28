---
title: Метод setLogWriter (SQLServerDataSource) | Документы Microsoft
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
ms.topic: article
apiname:
- SQLServerDataSource.setLogWriter
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7a77d8ef-2211-4bf8-af35-020fc896c073
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d8c2fe3e1d9dd02f8a3d4e1186233dcf5b2b8933
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="setlogwriter-method-sqlserverdatasource"></a>Метод setLogWriter (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Этот метод предназначен только для внутреннего использования. Дополнительные сведения о ведении журнала см. в разделе [Трассировка операций драйвера](../../../connect/jdbc/tracing-driver-operation.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setLogWriter(java.io.PrintWriter out)  
```  
  
#### <a name="parameters"></a>Параметры  
 *Out*  
  
 Объект PrintWriter.  
  
## <a name="remarks"></a>Замечания  
 Этот метод setLogWriter указывается с помощью метода setLogWriter в интерфейсе javax.sql.DataSource.  
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
