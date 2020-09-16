---
description: Обработка метаданных с помощью JDBC Driver
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
ms.openlocfilehash: 633629005eef8e9a47f616637e646886666f2200
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88438426"
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
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Использование метаданных базы данных](../../connect/jdbc/using-database-metadata.md)|Описывает получение метаданных о базе данных, с которой установлено соединение.|  
|[Использование метаданных результирующего набора](../../connect/jdbc/using-result-set-metadata.md)|Описывает получение метаданных о текущем результирующем наборе.|  
|[Использование метаданных параметров](../../connect/jdbc/using-parameter-metadata.md)|Описывает получение метаданных о параметрах подготовленных и вызываемых процедур.|  
  
## <a name="see-also"></a>См. также раздел  
 [Общие сведения о JDBC Driver](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
