---
description: Метод getMaxColumnNameLength (SQLServerDatabaseMetaData)
title: Метод getMaxColumnNameLength (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getMaxColumnNameLength
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 67fb5407-55b9-48b6-87f3-112700f304ba
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f014ef391062da5289353e44b56e25f598f19053
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88435646"
---
# <a name="getmaxcolumnnamelength-method-sqlserverdatabasemetadata"></a>Метод getMaxColumnNameLength (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает максимальное число символов, допустимое в имени столбца для этой базы данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getMaxColumnNameLength()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **int**, указывающее максимально допустимое количество символов.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getMaxColumnNameLength задается с помощью метода getMaxColumnNameLength в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
