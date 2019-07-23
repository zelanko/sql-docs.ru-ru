---
title: Получение версии драйвера | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 5e241d72-16da-4ada-ac67-e6308394108f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c75f14ca3f24a97240d7430210ab79c70e0bac85
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67956555"
---
# <a name="getting-the-driver-version"></a>Получение версии драйвера
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Версию установленного драйвера [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] можно получить следующими способами:  
  
-   Вызовите методы [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md) [getDriverMajorVersion](../../connect/jdbc/reference/getdrivermajorversion-method-sqlserverdatabasemetadata.md), [getDriverMinorVersion](../../connect/jdbc/reference/getdriverminorversion-method-sqlserverdatabasemetadata.md) или [getDriverVersion](../../connect/jdbc/reference/getdriverversion-method-sqlserverdatabasemetadata.md).  
  
-   Версия указана в файле readme.txt, распространяемом вместе с продуктом.  
  
 Кроме того, имя драйвера JDBC возвращается методом [getDriverName](../../connect/jdbc/reference/getdrivername-method-sqlserverdatabasemetadata.md) в классе SQLServerDatabaseMetaData. Он, например, возвращает строку "Microsoft JDBC Driver 6.4 for SQL Server".  
  
 Ниже приведен пример выходных данных вызовов методов класса SQLServerDatabaseMetaData:  
  
 `getDriverName = Microsoft JDBC Driver 6.4 for SQL Server`  
  
 `getDriverMajorVersion = 6`  
  
 `getDriverMinorVersion = 4`  
  
 `getDriverVersion = 6.4.` *xxx.x*  
  
 Здесь «xxx.x» представляет номер окончательной версии.  
  
## <a name="see-also"></a>См. также:  
 [Диагностика проблем с драйвером JDBC](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)  
  
  
