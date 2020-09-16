---
description: Метод getNCharacterStream (java.lang.String) (SQLServerResultSet)
title: Метод getNCharacterStream (java.lang.String) (SQLServerResultSet) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: a117f3a3-9c25-41e1-9adb-a40e90620dd6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5db2c9a81865779fa00d3800aed64d1d7666b49f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88435346"
---
# <a name="getncharacterstream-method-javalangstring-sqlserverresultset"></a>Метод getNCharacterStream (java.lang.String) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает значение указанного столбца в текущей строке объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде объекта Reader.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.io.Reader getNCharacterStream(java.lang.String columnLabel)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnLabel*  
  
 Значение String, содержащее метку столбца.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект Reader.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getNCharacterStream задается с помощью метода getNCharacterStream в интерфейсе java.sql.ResultSet.  
  
 Этот метод может использоваться для получения значения из столбца **nvarchar**, **nchar**, **nvarchar(max)**, **ntext** или **xml** в текущей строке объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md). При попытке использования этого метода для получения значений других типов данных возникнет исключение.  
  
## <a name="see-also"></a>См. также:  
 [Метод getNCharacterStream (SQLServerResultSet)](../../../connect/jdbc/reference/getncharacterstream-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)  
  
  
