---
title: "JDBC 4.3 соответствия для драйвера JDBC | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2018
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 36025ec0-3c72-4e68-8083-58b38e42d03b
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b3f678f33ec8f2c844bce14daa150f6c135744ff
ms.sourcegitcommit: 9d0467265e052b925547aafaca51e5a5e93b7e38
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/02/2018
---
# <a name="jdbc-43-compliance-for-the-jdbc-driver"></a>JDBC 4.3 соответствия для драйвера JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

    
> [!NOTE]  
>  Для спецификаций Java Database Connectivity API 4.2 соответствуют версий, предшествующих 6.4 драйвера Microsoft JDBC для SQL Server. Этот раздел неприменим для версий, предшествующих версии 6.4.  
  
 В настоящее время 6.4 драйвера Microsoft JDBC для SQL Server является Java совместимые 9, но не полностью соответствует спецификации 4.3 API подключения к базе данных Java. Для вновь появился API в JDBC 4.3, если не поддерживается драйвером, драйвер вызывает исключение SQLFeatureNotSupportedException.