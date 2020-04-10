---
title: Обработка метаданных с помощью JDBC Driver | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 5cfb35d4-ddcd-40a2-8091-f29cddc32552
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 859932404e14a9ab1216665d211e1b6734ca9726
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80924691"
---
# <a name="handling-metadata-with-the-jdbc-driver"></a>Обработка метаданных с помощью JDBC Driver
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] можно использовать для работы с метаданными в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] различными способами. Драйвер JDBC можно использовать для получения метаданных о базе данных, результирующем наборе или параметрах.  
  
 JDBC Driver предоставляет три класса для получения метаданных из базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md), который используется для возврата сведений о базе данных, к которой установлено подключение.  
  
-   [SQLServerResultSetMetaData](../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md), который используется для возврата сведений о результирующем наборе.  
  
-   [SQLServerParameterMetaData](../../connect/jdbc/reference/sqlserverparametermetadata-class.md), который используется для возврата сведений о параметрах подготовленных и вызываемых инструкций.  
  
 Здесь представлены разделы, где описывается использование каждого из трех классов метаданных для работы с метаданными в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Методы метаданных, описываемые в этом разделе, обычно предъявляют серьезные требования к производительности приложения, поэтому их нужно применять с осторожностью.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Использование метаданных базы данных](../../connect/jdbc/using-database-metadata.md)|Описывает получение метаданных о базе данных, с которой установлено соединение.|  
|[Использование метаданных результирующего набора](../../connect/jdbc/using-result-set-metadata.md)|Описывает получение метаданных о текущем результирующем наборе.|  
|[Использование метаданных параметров](../../connect/jdbc/using-parameter-metadata.md)|Описывает получение метаданных о параметрах подготовленных и вызываемых процедур.|  
  
## <a name="see-also"></a>См. также раздел  
 [Общие сведения о JDBC Driver](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
