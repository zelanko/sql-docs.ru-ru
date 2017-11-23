---
title: "Метод insertsAreDetected (SQLServerDatabaseMetaData) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerDatabaseMetaData.insertsAreDetected
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: f296cc42-9d26-48c3-a360-bcf51c31f7fb
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 46ee8da85734c79f7d7e01806387a68e8010abdf
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="insertsaredetected-method-sqlserverdatabasemetadata"></a>Метод insertsAreDetected (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает ли вставка видимой строки могут быть обнаружены путем вызова метода [rowInserted](../../../connect/jdbc/reference/rowinserted-method-sqlserverresultset.md) метод [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) класса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean insertsAreDetected(int type)  
```  
  
#### <a name="parameters"></a>Параметры  
 *type*  
  
 Целочисленное значение, указывающее тип результирующего набора. Возможно одно из следующих значений, определенных в java.sql.ResultSet или SQLServerResultSet.  
  
## <a name="javasqlresultset-types"></a>Типы java.sql.ResultSet  
 TYPE_FORWARD_ONLY  
  
 TYPE_SCROLL_SENSITIVE  
  
 TYPE_SCROLL_INSENSITIVE  
  
## <a name="sqlserverresultset-types"></a>Типы SQLServerResultSet  
 TYPE_SS_SCROLL_STATIC  
  
 TYPE_SS_SCROLL_KEYSET  
  
 TYPE_SS_DIRECT_FORWARD_ONLY  
  
 TYPE_SS_SERVER_CURSOR_FORWARD_ONLY  
  
 TYPE_SS_SCROLL_DYNAMIC  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** , если можно обнаружить вставку строки. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод insertsAreDetected указывается с помощью метода insertsAreDetected в интерфейсе java.sql.DatabaseMetaData.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]не обнаруживает вставленные строки для любого типа курсора.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
