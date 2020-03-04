---
title: Скачивание драйвера Microsoft JDBC Driver for SQL Server
description: Скачайте драйвер Microsoft JDBC для SQL Server, чтобы разрабатывать приложения Java с подключением к SQL Server.
ms.date: 02/26/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 451181b8-11e6-4d01-b547-9ac5aada8238
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6576ed155e57fbd69757065c440382efa4adba5e
ms.sourcegitcommit: 6ee40a2411a635daeec83fa473d8a19e5ae64662
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/28/2020
ms.locfileid: "77903501"
---
# <a name="download-microsoft-jdbc-driver-for-sql-server"></a>Скачивание драйвера Microsoft JDBC Driver for SQL Server

Эта статья содержит ссылки для скачивания драйвера Microsoft JDBC для SQL Server. Этот драйвер позволяет разрабатывать приложения Java с подключением к SQL Server.  

## <a name="available-downloads-of-jdbc-driver-for-sql-server"></a>Доступные загрузки драйвера JDBC для SQL Server

Используйте ссылки из следующей таблицы, чтобы скачать свежую версию драйвера Microsoft JDBC для SQL Server, соответствующую используемой среде выполнения Java (JRE).

| Версия | Дата выпуска | Версии Java |
|---|---|---|
| [Microsoft JDBC Driver 8.2](https://go.microsoft.com/fwlink/?linkid=2116870) | 26.02.2020 | JRE 8, 11, 13 |
| [Microsoft JDBC Driver 7.4](https://go.microsoft.com/fwlink/?linkid=2099962) | 01.08.2019 | JRE 8, 11, 12 |
| [Microsoft JDBC Driver 7.2](https://go.microsoft.com/fwlink/?linkid=2063159) | 17.04.2019 | JRE 8, 11 |
| [Microsoft JDBC Driver 7.0](https://go.microsoft.com/fwlink/?linkid=2005972) | 31.07.2018 | JRE 8, 10 |
| [Microsoft JDBC Driver 6.4](https://go.microsoft.com/fwlink/?linkid=868290)  | 26.03.2018 | JRE 7, 8, 9 |
| [Microsoft JDBC Driver 6.2](https://go.microsoft.com/fwlink/?linkid=852460) | 12.02.2018 | JRE 7, 8 |
| [Microsoft JDBC Driver 6.0](https://go.microsoft.com/fwlink/?LinkId=245496) | 27.02.2018 | JRE 7, 8 |
| [Microsoft JDBC Driver 4.2](https://go.microsoft.com/fwlink/?linkid=841534) | 26.02.2018 | JRE 7, 8 |

При скачивании драйвера вы увидите несколько JAR-файлов. Имя каждого JAR-файла обозначает поддерживаемую версию Java. Дополнительные сведения о каждом выпуске см. в статьях с [заметками о выпуске](release-notes-for-the-jdbc-driver.md) и [требованиями к системе](system-requirements-for-the-jdbc-driver.md).

## <a name="using-the-jdbc-driver-with-maven-central"></a>Использование JDBC Driver с Maven Central

JDBC Driver можно включить в проект Maven, добавив его в качестве зависимости в файл POM.xml с помощью следующего кода:

```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>8.2.1.jre11</version>
</dependency>
```  

## <a name="unsupported-drivers"></a>Неподдерживаемые драйверы

Скачивание неподдерживаемых версий драйверов здесь недоступно. Мы постоянно работаем над улучшением поддержки возможностей подключения Java. Настоятельно рекомендуем использовать последнюю версию драйвера Microsoft JDBC.  
  
## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о драйвере Microsoft JDBC для SQL Server см. в статье [Общие сведения о JDBC Driver](overview-of-the-jdbc-driver.md) и в [репозитории JDBC Driver](https://github.com/microsoft/mssql-jdbc/blob/dev/README.md) на сайте GitHub.
