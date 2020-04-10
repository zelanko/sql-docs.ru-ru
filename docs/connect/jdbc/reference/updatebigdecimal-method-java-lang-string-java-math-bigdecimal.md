---
title: Метод updateBigDecimal (java.lang.String, java.math.BigDecimal) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateBigDecimal (java.lang.String, java.math.BigDecimal)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b844cd9d-3d2d-4385-ab01-ecc89692054f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 88b5936ab055379954f0bd0215d0d5524f47fd4f
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80922883"
---
# <a name="updatebigdecimal-method-javalangstring-javamathbigdecimal"></a>Метод updateBigDecimal (java.lang.String, java.math.BigDecimal)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет указанный столбец объектом BigDecimal по заданному имени столбца.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void updateBigDecimal(java.lang.String columnName,  
                             java.math.BigDecimal x)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnName*  
  
 Значение типа **String**, содержащее имя столбца.  
  
 *x*  
  
 Объект BigDecimal.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод updateBigDecimal задается с помощью метода updateBigDecimal в интерфейсе java.sql.ResultSet.  
  
## <a name="see-also"></a>См. также:  
 [Метод updateBigDecimal (SQLServerResultSet)](../../../connect/jdbc/reference/updatebigdecimal-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
