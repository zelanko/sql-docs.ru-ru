---
title: Скачивание драйвера Microsoft JDBC Driver for SQL Server
description: Скачайте драйвер Microsoft JDBC для SQL Server, чтобы разрабатывать приложения Java, которые подключаются к SQL Server.
ms.date: 09/30/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 451181b8-11e6-4d01-b547-9ac5aada8238
author: MightyPen
ms.author: genemi
ms.openlocfilehash: dc273bccf054408f48e7bb2bd0409a31bb18bd18
ms.sourcegitcommit: 445842da7c7d216b94a9576e382164c67f54e19a
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 09/30/2019
ms.locfileid: "71682006"
---
# <a name="download-microsoft-jdbc-driver-for-sql-server"></a>Скачивание драйвера Microsoft JDBC Driver for SQL Server

В этой статье содержатся ссылки для загрузки драйвера Microsoft JDBC для SQL Server. Этот драйвер позволяет разрабатывать приложения Java, подключающиеся к SQL Server.  

## <a name="available-downloads-of-jdbc-driver-for-sql-server"></a>Доступные загрузки драйвера JDBC для SQL Server

Используйте ссылки в следующей таблице, чтобы скачать последний драйвер Microsoft JDBC для SQL Server, соответствующий среда выполнения Java (JRE):

| Версия | Дата выпуска | Версии Java |
|---|---|---|
| [Microsoft JDBC Driver 7.4](https://go.microsoft.com/fwlink/?linkid=2099962) | 01.08.2019 | JRE 8, 11, 12 |
| [Microsoft JDBC Driver 7.2](https://go.microsoft.com/fwlink/?linkid=2063159) | 17.04.2019 | JRE 8, 11 |
| [Microsoft JDBC Driver 7.0](https://go.microsoft.com/fwlink/?linkid=2005972) | 31.07.2018 | JRE 8, 10 |
| [Microsoft JDBC Driver 6.4](https://go.microsoft.com/fwlink/?linkid=868290)  | 26.03.2018 | JRE 7, 8, 9 |
| [Microsoft JDBC Driver 6.2](https://go.microsoft.com/fwlink/?linkid=852460) | 12.02.2018 | JRE 7, 8 |
| [Microsoft JDBC Driver 6.0](https://go.microsoft.com/fwlink/?LinkId=245496) | 27.02.2018 | JRE 7, 8 |
| [Драйвер Microsoft JDBC 4,2](https://go.microsoft.com/fwlink/?linkid=841534) | 26.02.2018 | JRE 7, 8 |
| [Драйвер Microsoft JDBC 4,1](https://go.microsoft.com/fwlink/?linkid=841533) | 27.02.2018 | JRE 7 |

При скачивании драйвера существует несколько JAR-файлов. Имя JAR-файла указывает версию Java, которую он поддерживает. Дополнительные сведения о каждом выпуске см. в [заметках о выпуске](release-notes-for-the-jdbc-driver.md) и [требованиях к системе](system-requirements-for-the-jdbc-driver.md).

## <a name="using-the-jdbc-driver-with-maven-central"></a>Использование JDBC Driver с Maven Central

JDBC Driver можно включить в проект Maven, добавив его в качестве зависимости в файл POM.xml с помощью следующего кода:

```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>7.4.1.jre11</version>
</dependency>
```  

## <a name="unsupported-drivers"></a>Неподдерживаемые драйверы

Скачивание неподдерживаемых версий драйверов здесь недоступно. Мы постоянно работаем над улучшением поддержки возможностей подключения Java. Настоятельно рекомендуем использовать последнюю версию драйвера Microsoft JDBC.  
  
## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о драйвере Microsoft JDBC для SQL Server см. в статье [Обзор драйвера JDBC](overview-of-the-jdbc-driver.md) и [репозитория GitHub драйвера JDBC](https://github.com/microsoft/mssql-jdbc/blob/dev/README.md).
