---
title: Обработка метаданных с помощью драйвера JDBC | Документы Microsoft
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
ms.assetid: 5cfb35d4-ddcd-40a2-8091-f29cddc32552
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f566739dabdda602fcde3bf9726808536a8fb00d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="handling-metadata-with-the-jdbc-driver"></a>Обработка метаданных с использованием драйвера JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] Можно использовать для работы с метаданными в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базе данных различными способами. Драйвер JDBC можно использовать для получения метаданных о базе данных, результирующем наборе или параметрах.  
  
 Драйвер JDBC предоставляет три класса для получения метаданных из [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных:  
  
-   [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md), который используется для возврата сведений о базе данных, с которой установлено соединение.  
  
-   [SQLServerResultSetMetaData](../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md), который используется для возврата сведений о результирующем наборе.  
  
-   [SQLServerParameterMetaData](../../connect/jdbc/reference/sqlserverparametermetadata-class.md), который используется для получения сведений о параметрах подготовленных и вызываемых инструкций.  
  
 Подразделы данного раздела описывают, как использовать каждый из трех классов метаданных для работы с метаданными в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных.  
  
> [!NOTE]  
>  Методы метаданных, описываемые в этом разделе, обычно предъявляют серьезные требования к производительности приложения, поэтому их нужно применять с осторожностью.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Использование метаданных базы данных](../../connect/jdbc/using-database-metadata.md)|Описывает получение метаданных о базе данных, с которой установлено соединение.|  
|[Использование метаданных результирующего набора](../../connect/jdbc/using-result-set-metadata.md)|Описывает получение метаданных о текущем результирующем наборе.|  
|[Использование метаданных о параметрах](../../connect/jdbc/using-parameter-metadata.md)|Описывает получение метаданных о параметрах подготовленных и вызываемых процедур.|  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о драйвере JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
