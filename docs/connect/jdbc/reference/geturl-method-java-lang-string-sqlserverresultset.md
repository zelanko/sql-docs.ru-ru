---
description: Метод getURL (java.lang.String) (SQLServerResultSet)
title: Метод getURL (java.lang.String) (SQLServerResultSet) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getURL (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 105a5319-0f4c-4d08-964b-cc52f8e28ec1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0eef68b239a4d8578cf7b9d2575cebef31100e6b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88433866"
---
# <a name="geturl-method-javalangstring-sqlserverresultset"></a>Метод getURL (java.lang.String) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает значение имени заданного столбца в текущей строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде объекта URL.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.net.URL getURL(java.lang.String sColumn)  
```  
  
#### <a name="parameters"></a>Параметры  
 *sColumn*  
  
 Значение типа **String**, содержащее имя столбца.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект URL.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getURL определен с помощью метода getURL в интерфейсе java.sql.ResultSet.  
  
## <a name="see-also"></a>См. также:  
 [Метод getURL (SQLServerResultSet)](../../../connect/jdbc/reference/geturl-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
