---
description: Метод getMaxCatalogNameLength (SQLServerDatabaseMetaData)
title: Метод getMaxCatalogNameLength (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getMaxCatalogNameLength
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 89c11327-eae1-4178-9e26-4b484d521c65
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bf1819338cb3b456e667c65a3ea98023c7453abb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88435666"
---
# <a name="getmaxcatalognamelength-method-sqlserverdatabasemetadata"></a>Метод getMaxCatalogNameLength (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает максимальное число символов, допустимое в имени каталога для этой базы данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getMaxCatalogNameLength()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **int**, указывающее максимально допустимое количество символов.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getMaxCatalogNameLength задается с помощью метода getMaxCatalogNameLength в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
