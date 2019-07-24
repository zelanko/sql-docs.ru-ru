---
title: Метод supportsPositionedDelete (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsPositionedDelete
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8011659a-d74b-489b-a88b-08bd9e8b48b2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1dbe35f0d0068cabd92f3f8ff538e15fc0b81668
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67969023"
---
# <a name="supportspositioneddelete-method-sqlserverdatabasemetadata"></a>Метод supportsPositionedDelete (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение, определяющее, поддерживает ли эта база данных позиционированные инструкции DELETE.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean supportsPositionedDelete()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true** , если поддерживается. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод supportsPositionedDelete задается методом supportsPositionedDelete в интерфейсе Java. SQL. DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
