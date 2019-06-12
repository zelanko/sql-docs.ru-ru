---
title: Метод locatorsUpdateCopy (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.locatorsUpdateCopy
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f6ec8c1d-7ff8-4bc5-8bd3-0199a9294a6e
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 01cf5c8d9d4d4b40e4f76040725a81e6424bb254
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66779624"
---
# <a name="locatorsupdatecopy-method-sqlserverdatabasemetadata"></a>Метод locatorsUpdateCopy (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Указывает, будут ли обновления в LOB производиться над этим объектом LOB напрямую, либо над его копией.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean locatorsUpdateCopy()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** Если обновления выполняются в копии. **false** Если обновления выполняются непосредственно.  
  
## <a name="exceptions"></a>Исключения  
 java.sql.SQLException  
  
## <a name="remarks"></a>Remarks  
 Этот метод locatorsUpdateCopy указывается с помощью метода locatorsUpdateCopy в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
