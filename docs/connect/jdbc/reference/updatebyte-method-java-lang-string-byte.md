---
title: Метод updateByte (java.lang.String, byte) | Документы Microsoft
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
- SQLServerResultSet.updateByte (java.lang.String, byte)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5416aed2-a5b6-4e3b-9750-90db8cda8cec
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 552854768d7ea5e45afe67f2202d499f205e3c31
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="updatebyte-method-javalangstring-byte"></a>Метод updateByte (java.lang.String, byte)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет указанный столбец с **байтов** значение заданному имени столбца.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void updateByte(java.lang.String columnName,  
                       byte x)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnName*  
  
 Объект **строка** , содержащее имя столбца.  
  
 *x*  
  
 Объект **байтов** значение.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод updateByte указывается с помощью метода updateByte в интерфейсе java.sql.ResultSet.  
  
## <a name="see-also"></a>См. также  
 [Метод updateByte &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatebyte-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
