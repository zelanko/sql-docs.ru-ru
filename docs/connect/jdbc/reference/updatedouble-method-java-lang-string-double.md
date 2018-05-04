---
title: Метод updateDouble (java.lang.String, double) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateDouble (java.lang.String, double)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f70971d5-34cc-4f70-8a91-5d46356b24ae
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 710b042933f163bfe235aab998fbeb591bd3f4ca
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="updatedouble-method-javalangstring-double"></a>Метод updateDouble (java.lang.String, double)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет указанный столбец с **двойные** значение заданному имени столбца.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void updateDouble(java.lang.String columnName,  
                         double x)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnName*  
  
 Объект **строка** , содержащее имя столбца.  
  
 *x*  
  
 Объект **двойные** значение.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод updateDouble указывается с помощью метода updateDouble в интерфейсе java.sql.ResultSet.  
  
## <a name="see-also"></a>См. также  
 [Метод updateDouble &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatedouble-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
