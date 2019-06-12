---
title: Метод updateByte (int, byte) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateByte (int, byte)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e635d789-9218-488e-a213-2e3e09635acc
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: cdfa8cab28d526cc14400f982cf62289d94d888e
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66786991"
---
# <a name="updatebyte-method-int-byte"></a>Метод updateByte (int, byte)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет указанный столбец значением **byte** по заданному индексу столбца.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void updateByte(int index,  
                       byte x)  
```  
  
#### <a name="parameters"></a>Параметры  
 *index*  
  
 Значение типа **int**, указывающее индекс столбца.  
  
 *x*  
  
 Значение типа **byte**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод updateByte указывается с помощью метода updateByte в интерфейсе java.sql.ResultSet.  
  
## <a name="see-also"></a>См. также:  
 [Метод updateByte (SQLServerResultSet)](../../../connect/jdbc/reference/updatebyte-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
