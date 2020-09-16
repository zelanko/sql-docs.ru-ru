---
description: Метод getNCharacterStream (int) (SQLServerResultSet)
title: Метод getNCharacterStream (int) (SQLServerResultSet) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: f1cfa4e4-3e1f-4504-b0de-cc626d653661
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 78d94536a297d28c1a181c165b6ceda39456d9aa
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88435366"
---
# <a name="getncharacterstream-method-int-sqlserverresultset"></a>Метод getNCharacterStream (int) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает значение указанного столбца в текущей строке объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде объекта Reader.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.io.Reader getNCharacterStream(int columnIndex)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnIndex*  
  
 Значение типа **int**, указывающее индекс столбца.  
  
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
  
  
