---
title: Метод getMaxConnections (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getMaxConnections
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 745410f7-e59b-4423-9728-c903adedc399
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 02aa3fcb7feed842a2da7b13c5609ea516ef40b0
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67982173"
---
# <a name="getmaxconnections-method-sqlserverdatabasemetadata"></a>Метод getMaxConnections (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает максимально возможное число одновременных соединений с этой базой данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getMaxConnections()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение типа **int**, указывающее максимально допустимое количество параллельных соединений.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getMaxConnections задается с помощью метода getMaxConnections в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
