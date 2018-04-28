---
title: Получение версии драйвера | Документы Microsoft
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
ms.topic: article
ms.assetid: 5e241d72-16da-4ada-ac67-e6308394108f
caps.latest.revision: 21
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7eceb4cfafd27459f928b7f405e008d60871d17e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="getting-the-driver-version"></a>Получение версии драйвера
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Версию установленного драйвера [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] можно найти одним из следующих способов:  
  
-   Вызовите [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md) методы [getDriverMajorVersion](../../connect/jdbc/reference/getdrivermajorversion-method-sqlserverdatabasemetadata.md), [getDriverMinorVersion](../../connect/jdbc/reference/getdriverminorversion-method-sqlserverdatabasemetadata.md), или [getDriverVersion](../../connect/jdbc/reference/getdriverversion-method-sqlserverdatabasemetadata.md).  
  
-   Версия указана в файле readme.txt, распространяемом вместе с продуктом.  
  
 Кроме того, имя драйвера JDBC могут быть возвращены из [getDriverName](../../connect/jdbc/reference/getdrivername-method-sqlserverdatabasemetadata.md) вызова метода в классе SQLServerDatabaseMetaData. Возвращается, например, «Microsoft JDBC Driver 6.4 для SQL Server».  
  
 Ниже приведен пример выходных данных из вызовов методов класса SQLServerDatabaseMetaData:  
  
 `getDriverName = Microsoft JDBC Driver 6.4 for SQL Server`  
  
 `getDriverMajorVersion = 6`  
  
 `getDriverMinorVersion = 4`  
  
 `getDriverVersion = 6.4.` *xxx.x*  
  
 Здесь «xxx.x» представляет номер окончательной версии.  
  
## <a name="see-also"></a>См. также  
 [Диагностика проблем с драйвером JDBC](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)  
  
  
