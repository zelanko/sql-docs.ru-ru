---
description: Метод getScale (SQLServerResultSetMetaData)
title: Метод getScale (SQLServerResultSetMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSetMetaData.getScale
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: fe29aa5f-4cc5-413f-8bbd-a58064993d87
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1c36a67dc80a078308344105f2c1091a0d25f90d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88434766"
---
# <a name="getscale-method-sqlserverresultsetmetadata"></a>Метод getScale (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает число цифр справа от десятичной запятой для указанного столбца.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getScale(int column)  
```  
  
#### <a name="parameters"></a>Параметры  
 *column*  
  
 Значение типа **int**, указывающее индекс столбца.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение типа **int**, указывающее масштаб столбца.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getScale указывается с помощью метода getScale в интерфейсе java.sql.ResultSetMetaData.  
  
 В версии 3.0 драйвера JDBC [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поведение столбца DECIMAL_DIGITS изменилось. Дополнительные сведения см. в статье [SQLServerDatabaseMetaData.getColumns](../../../connect/jdbc/reference/getcolumns-method-sqlserverdatabasemetadata.md).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [Класс SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
