---
title: Метод updateByte (java.lang.String, byte) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateByte (java.lang.String, byte)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5416aed2-a5b6-4e3b-9750-90db8cda8cec
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 1b34e0f653868c07566db7542f77d800ab8db1a0
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66784302"
---
# <a name="updatebyte-method-javalangstring-byte"></a>Метод updateByte (java.lang.String, byte)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет указанный столбец значением **byte** по заданному имени столбца.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void updateByte(java.lang.String columnName,  
                       byte x)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnName*  
  
 Значение типа **String**, содержащее имя столбца.  
  
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
  
  
