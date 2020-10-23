---
title: Библиотеки и платформы подключения
description: Список драйверов подключения, которые клиентские приложения на разных языках могут использовать для подключения к экземпляру Microsoft SQL Server, работающему локально или в облаке, в Linux, Windows или Docker, а также в базе данных SQL Azure и Azure Synapse Analytics.
author: VanMSFT
ms.author: vanto
ms.date: 03/17/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 80efe5ff-09ba-48a0-ac93-a91d62cff47c
ms.openlocfilehash: c626df1042ed3b3d9ecb5e25bbd219ceb468bfee
ms.sourcegitcommit: 22102f25db5ccca39aebf96bc861c92f2367c77a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2020
ms.locfileid: "92115497"
---
# <a name="connectivity-libraries-and-frameworks-for-microsoft-sql-server"></a>Библиотеки и платформы подключения для Microsoft SQL Server

[!INCLUDE [SQL Server - Linux](../includes/applies-to-version/sql-linux.md)]

Ознакомьтесь с учебниками [Начало работы](https://aka.ms/sqldev), чтобы быстро приступить к работе с такими языками программирования, как C#, Java, Node.js, PHP и Python, и создайте приложение с помощью SQL Server на Linux или Windows или Docker в macOS.

В следующей таблице перечислены библиотеки или *драйверы* подключения, которые клиентские приложения на разных языках могут использовать для подключения к экземпляру Microsoft SQL Server, работающему локально или в облаке, в Linux, Windows или Docker, а также в базе данных SQL Azure и Azure Synapse Analytics. 

| Язык | Платформа | Дополнительные ресурсы | Скачивание | Приступая к работе |
| :-- | :-- | :-- | :-- | :-- |
| C# | Windows, Linux, macOS | [Microsoft ADO.NET для SQL Server](../connect/ado-net/microsoft-ado-net-sql-server.md) | [Загрузить](https://msdn.microsoft.com/vstudio/aa496123.aspx) | [Начало работы](https://www.microsoft.com/sql-server/developer-get-started/csharp/ubuntu)
| Java | Windows, Linux, macOS | [Драйвер Microsoft JDBC для SQL Server](../connect/jdbc/microsoft-jdbc-driver-for-sql-server.md) | [Загрузить](https://go.microsoft.com/fwlink/?LinkId=245496) |  [Начало работы](https://www.microsoft.com/sql-server/developer-get-started/java/ubuntu)
| PHP | Windows, Linux, macOS| [PHP SQL Driver для SQL Server](../connect/php/microsoft-php-driver-for-sql-server.md) | Операционная система: <br/> \* [Windows](https://www.microsoft.com/download/details.aspx?id=20098) <br/> \* [Linux](https://github.com/Microsoft/msphpsql/tree/dev#install-unix) <br/> \* [macOS](https://github.com/Microsoft/msphpsql/tree/dev#install-unix) |  [Начало работы](https://www.microsoft.com/sql-server/developer-get-started/php/ubuntu)
| Node.js | Windows, Linux, macOS | [Драйвер Node.js для SQL Server](../connect/node-js/node-js-driver-for-sql-server.md) |  [Начало работы](https://www.microsoft.com/sql-server/developer-get-started/node/ubuntu)
| Python | Windows, Linux, macOS | [Python SQL Driver](../connect/python/python-driver-for-sql-server.md) <br/> \* [pyodbc](../connect/python/pyodbc/step-1-configure-development-environment-for-pyodbc-python-development.md) |  [Начало работы](https://www.microsoft.com/sql-server/developer-get-started/python/ubuntu)
| Ruby | Windows, Linux, macOS | [Драйвер Ruby для SQL Server](../connect/ruby/ruby-driver-for-sql-server.md) | [Начало работы](https://www.microsoft.com/sql-server/developer-get-started/ruby/ubuntu)
| C++ | Windows, Linux, macOS | [Драйвер Microsoft ODBC для SQL Server](../connect/odbc/microsoft-odbc-driver-for-sql-server.md) | [Загрузить](../connect/odbc/microsoft-odbc-driver-for-sql-server.md) |  

В следующей таблице перечислены примеры платформ объектно-реляционного сопоставления (ORM) и веб-платформ, которые клиентское приложение может использовать с экземпляром Microsoft SQL Server, работающим локально или в облаке, в Linux, Windows или Docker, а также в базе данных SQL Azure и Azure Synapse Analytics. 

| Язык | Платформа | ORM |
| :-- | :-- | :-- |
| C# | Windows, Linux, macOS | [Entity Framework](/ef)<br>[Entity Framework Core](/ef/core/index) |
| Java | Windows, Linux, macOS |[Hibernate ORM](https://hibernate.org/orm)|
| PHP | Windows, Linux | [Laravel (Eloquent)](https://laravel.com/docs/5.0/eloquent) |
| Node.js | Windows, Linux, macOS | [Sequelize ORM](http://sequelize.org/) |
| Python | Windows, Linux, macOS |[Django](https://www.djangoproject.com/) |
| Ruby | Windows, Linux, macOS | [Ruby on Rails](https://rubyonrails.org/) |

## <a name="related-links"></a>Связанные ссылки
- [Драйверы SQL Server](../connect/sql-connection-libraries.md) для подключения из клиентских приложений