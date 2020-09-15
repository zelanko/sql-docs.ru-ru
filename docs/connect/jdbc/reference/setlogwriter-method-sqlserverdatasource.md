---
description: Метод setLogWriter (SQLServerDataSource)
title: Метод setLogWriter (SQLServerDataSource) | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3f38105acc725f392c91adf193e658ed3ad05ff6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88431726"
---
# <a name="setlogwriter-method-sqlserverdatasource"></a>Метод setLogWriter (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Этот метод предназначен только для внутреннего использования. Дополнительные сведения о ведении журнала см. в статье о [трассировке операций драйвера](../../../connect/jdbc/tracing-driver-operation.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setLogWriter(java.io.PrintWriter out)  
```  
  
#### <a name="parameters"></a>Параметры  
 *out*  
  
 Объект PrintWriter.  
  
## <a name="remarks"></a>Remarks  
 Этот метод setLogWriter задается с помощью метода setLogWriter в интерфейсе javax.sql.DataSource.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
