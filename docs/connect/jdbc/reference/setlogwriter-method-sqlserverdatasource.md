---
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
ms.openlocfilehash: c4f6e80a84c24ac8666c9cd02ec1df42625c3add
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80925747"
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
  
  
