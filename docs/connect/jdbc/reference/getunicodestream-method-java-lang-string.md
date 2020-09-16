---
description: Метод getUnicodeStream (java.lang.String)
title: Метод getUnicodeStream (java.lang.String) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getUnicodeStream (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e8ea50a3-804a-4752-96e5-eb3d521f93c1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 51524bd6b2282c58008a7c1997856a9962407dac
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88433926"
---
# <a name="getunicodestream-method-javalangstring"></a>Метод getUnicodeStream (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает значение имени заданного столбца в текущей строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде потока символов в Юникоде.  
  
> [!NOTE]  
>  Этот метод является устаревшим в спецификации JDBC, и в случае его вызова создается исключение «не реализовано». Вместо этого следует использовать метод [getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.io.InputStream getUnicodeStream(java.lang.String columnName)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnName*  
  
 Значение типа **String**, содержащее имя столбца.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект InputStream.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getUnicodeString определен с помощью метода getUnicodeString в интерфейсе java.sql.ResultSet.  
  
## <a name="see-also"></a>См. также:  
 [Метод getUnicodeStream (SQLServerResultSet)](../../../connect/jdbc/reference/getunicodestream-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
