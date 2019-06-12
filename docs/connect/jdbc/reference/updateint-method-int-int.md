---
title: Метод updateInt (int, int) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateInt (int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f4f651b0-a822-4bd4-b391-cc2355154a2a
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 7f5e69e13762bdfb9b6adde9f635588bc35b742c
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66797192"
---
# <a name="updateint-method-int-int"></a>Метод updateInt (int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет указанный столбец значением **int** по заданному индексу столбца.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void updateInt(int index,  
                      int x)  
```  
  
#### <a name="parameters"></a>Параметры  
 *index*  
  
 Значение типа **int**, указывающее индекс столбца.  
  
 *x*  
  
 **Int** значение.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getInt определен с помощью метода getInt в интерфейсе java.sql.ResultSet.  
  
## <a name="see-also"></a>См. также:  
 [Метод updateInt &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updateint-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
