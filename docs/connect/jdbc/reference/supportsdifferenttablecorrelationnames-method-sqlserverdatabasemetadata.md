---
title: Метод supportsDifferentTableCorrelationNames | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsDifferentTableCorrelationNames
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b4f8db0c-2eaf-476b-b916-3e83355778f7
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: cb739baaacaf84c4853a7c62a261832bb8c5d2bf
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66794179"
---
# <a name="supportsdifferenttablecorrelationnames-method-sqlserverdatabasemetadata"></a>Метод supportsDifferentTableCorrelationNames (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение, определяющее, что, когда поддерживаются корреляционные имена таблиц, они должны отличаться от имен таблиц.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean supportsDifferentTableCorrelationNames()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** Если поддерживается. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод supportsDifferentTableCorrelationNames указывается с помощью метода supportsDifferentTableCorrelationNames в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
