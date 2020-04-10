---
title: Получение версии драйвера | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 5e241d72-16da-4ada-ac67-e6308394108f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1a1c5c6d4dcc3a5bd5acaac37ffdcdadc184e497
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80924660"
---
# <a name="getting-the-driver-version"></a>Получение версии драйвера
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Версию установленного драйвера [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] можно получить следующими способами:  
  
-   Вызовите методы [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)[getDriverMajorVersion](../../connect/jdbc/reference/getdrivermajorversion-method-sqlserverdatabasemetadata.md), [getDriverMinorVersion](../../connect/jdbc/reference/getdriverminorversion-method-sqlserverdatabasemetadata.md) или [getDriverVersion](../../connect/jdbc/reference/getdriverversion-method-sqlserverdatabasemetadata.md).  
  
-   Версия указана в файле readme.txt, распространяемом вместе с продуктом.  
  
 Кроме того, имя драйвера JDBC возвращается методом [getDriverName](../../connect/jdbc/reference/getdrivername-method-sqlserverdatabasemetadata.md) в классе SQLServerDatabaseMetaData. Он, например, возвращает строку "Microsoft JDBC Driver 6.4 for SQL Server".  
  
 Ниже представлен пример данных, возвращаемых вызовами к методам класса SQLServerDatabaseMetaData:  
  
 `getDriverName = Microsoft JDBC Driver 6.4 for SQL Server`  
  
 `getDriverMajorVersion = 6`  
  
 `getDriverMinorVersion = 4`  
  
 `getDriverVersion = 6.4.` *xxx.x*  
  
 Здесь «xxx.x» представляет номер окончательной версии.  
  
## <a name="see-also"></a>См. также раздел  
 [Диагностика проблем с JDBC Driver](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)  
  
  
