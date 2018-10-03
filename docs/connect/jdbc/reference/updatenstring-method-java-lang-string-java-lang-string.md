---
title: Метод updateNString (java.lang.String, java.lang.String) | Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6daca03f-c60f-4842-b9e3-11d136e78312
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3b59df324948ff1d8745fc104fd9c4f7ffebd5b7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47834382"
---
# <a name="updatenstring-method-javalangstring-javalangstring"></a>Метод updateNString (java.lang.String, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет значение **String** с помощью указанной метки столбцов в заданном столбце.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void updateNString(java.lang.String columnLabel,  
                          java.lang.String nString)  
```  
  
#### <a name="parameters"></a>Параметры  
 *ColumnLabel состоит из*  
  
 Значение типа **String**, содержащее метку столбца.  
  
 *nString*  
  
 Объект **строка** объекта.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод updateNString указывается с помощью метода updateNString в интерфейсе java.sql.ResultSet.  
  
 Этот метод передает Java **строка** к выбранному **nchar**, **nvarchar(max)**, **ntext**, и **xml** столбцы. Использование этого метода при работе со столбцами других типов данных приведет к возникновению исключения.  
  
## <a name="see-also"></a>См. также:  
 [Метод updateNString &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatenstring-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
