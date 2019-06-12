---
title: Метод updateFloat (java.lang.String, float) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateFloat (java.lang.String, float)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 19a6164f-f560-4304-8466-e55f0667a3d4
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: e348f9c51b68063867a13b9d9bfe6db3e7053645
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66804168"
---
# <a name="updatefloat-method-javalangstring-float"></a>Метод updateFloat (java.lang.String, float)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет указанный столбец значением типа **float** по заданному имени столбца.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void updateFloat(java.lang.String columnName,  
                        float x)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnName*  
  
 Значение типа **String**, содержащее имя столбца.  
  
 *x*  
  
 Объект **float** значение.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод updateFloat указывается с помощью метода updateFloat в интерфейсе java.sql.ResultSet.  
  
## <a name="see-also"></a>См. также:  
 [Метод updateFloat (SQLServerResultSet)](../../../connect/jdbc/reference/updatefloat-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
