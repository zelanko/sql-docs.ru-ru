---
title: JDBC 4.3 соответствия для драйвера JDBC | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2018
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
ms.assetid: 36025ec0-3c72-4e68-8083-58b38e42d03b
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 33b218598871e570fa99d212d565c834718de1d9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="jdbc-43-compliance-for-the-jdbc-driver"></a>JDBC 4.3 соответствия для драйвера JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

    
> [!NOTE]  
>  Для спецификаций Java Database Connectivity API 4.2 соответствуют версий, предшествующих 6.4 драйвера Microsoft JDBC для SQL Server. Этот раздел неприменим для версий, предшествующих версии 6.4.  
  
 В настоящее время 6.4 драйвера Microsoft JDBC для SQL Server является Java совместимые 9, но не полностью соответствует спецификации 4.3 API подключения к базе данных Java. Для вновь появился API в JDBC 4.3, если не поддерживается драйвером, драйвер вызывает исключение SQLFeatureNotSupportedException.