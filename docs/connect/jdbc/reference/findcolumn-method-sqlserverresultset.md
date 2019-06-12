---
title: Метод findColumn (SQLServerResultSet) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.findColumn
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7c29994a-0b53-420b-8a9b-82a9eef08587
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 4e3499748bc8c5e1b4a0251ef089bb498ba6aece
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66799038"
---
# <a name="findcolumn-method-sqlserverresultset"></a>Метод findColumn (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает индекс первого столбца, имя которого совпадает с заданным именем в этом объекте [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int findColumn(java.lang.String columnName)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnName*  
  
 Значение **String**, содержащее имя столбца.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение типа **int**, указывающее индекс столбца.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод findColumn указывается с помощью метода findColumn в интерфейсе java.sql.ResultSet.  
  
 Если имеется несколько столбцов с одинаковым именем, то метод findColumn возвращает первое совпадение с учетом регистра. Если отсутствуют совпадения с учетом регистра, то этот метод возвращает первое совпадение без учета регистра.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
