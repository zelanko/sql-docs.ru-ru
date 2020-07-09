---
title: Библиотеки и платформы подключения
description: Список драйверов подключения, которые клиентские приложения на различных языках могут использовать для подключения к Microsoft SQL Server, работающему локально или в облаке, в Linux, Windows или Docker, а также в базе данных SQL Azure и хранилище данных SQL Azure.
author: VanMSFT
ms.author: vanto
ms.date: 03/17/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 80efe5ff-09ba-48a0-ac93-a91d62cff47c
ms.openlocfilehash: 063ef8f06b6a93e54f7189c1a68cbfa176f21208
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85896539"
---
# <a name="connectivity-libraries-and-frameworks-for-microsoft-sql-server"></a>Библиотеки и платформы подключения для Microsoft SQL Server

[!INCLUDE [SQL Server - Linux](../includes/applies-to-version/sql-linux.md)]

Ознакомьтесь с учебниками [Начало работы](https://aka.ms/sqldev), чтобы быстро приступить к работе с такими языками программирования, как C#, Java, Node.js, PHP и Python, и создайте приложение с помощью SQL Server на Linux или Windows или Docker в macOS.

В следующей таблице приведен список библиотек или *драйверов* подключения, которые клиентские приложения на различных языках могут использовать для подключения к Microsoft SQL Server, работающему локально или в облаке, в Linux, Windows или Docker, а также в базе данных SQL Azure и хранилище данных SQL Azure. 

| Язык | Платформа | Дополнительные ресурсы | Скачивание | Приступая к работе |
| :-- | :-- | :-- | :-- | :-- |
| C# | Windows, Linux, macOS | [Microsoft ADO.NET для SQL Server](/sql/connect/ado-net/microsoft-ado-net-sql-server) | [Загрузить](https://msdn.microsoft.com/vstudio/aa496123.aspx) | [Начало работы](https://www.microsoft.com/sql-server/developer-get-started/csharp/ubuntu)
| Java | Windows, Linux, macOS | [Драйвер Microsoft JDBC для SQL Server](https://msdn.microsoft.com/library/mt484311.aspx) | [Загрузить](https://go.microsoft.com/fwlink/?LinkId=245496) |  [Начало работы](https://www.microsoft.com/sql-server/developer-get-started/java/ubuntu)
| PHP | Windows, Linux, macOS| [PHP SQL Driver для SQL Server](../connect/php/microsoft-php-driver-for-sql-server.md) | Операционная система: <br/> \* [Windows](https://www.microsoft.com/download/details.aspx?id=20098) <br/> \* [Linux](https://github.com/Microsoft/msphpsql/tree/dev#install-unix) <br/> \* [macOS](https://github.com/Microsoft/msphpsql/tree/dev#install-unix) |  [Начало работы](https://www.microsoft.com/sql-server/developer-get-started/php/ubuntu)
| Node.js | Windows, Linux, macOS | [Драйвер Node.js для SQL Server](../connect/node-js/node-js-driver-for-sql-server.md) |  [Начало работы](https://www.microsoft.com/sql-server/developer-get-started/node/ubuntu)
| Python | Windows, Linux, macOS | [Python SQL Driver](../connect/python/python-driver-for-sql-server.md) <br/> \* [pyodbc](https://msdn.microsoft.com/library/mt763257.aspx) |  [Начало работы](https://www.microsoft.com/sql-server/developer-get-started/python/ubuntu)
| Ruby | Windows, Linux, macOS | [Драйвер Ruby для SQL Server](../connect/ruby/ruby-driver-for-sql-server.md) | [Начало работы](https://www.microsoft.com/sql-server/developer-get-started/ruby/ubuntu)
| C++ | Windows, Linux, macOS | [Драйвер Microsoft ODBC для SQL Server](https://msdn.microsoft.com/library/mt654048(v=sql.1).aspx) | [Загрузить](https://msdn.microsoft.com/library/mt654048(v=sql.1).aspx) |  

В следующей таблице приведен список примеров платформ объектно-реляционного сопоставления (ORM) и веб-платформ, которые клиентское приложение может использовать с Microsoft SQL Server, работающим локально или в облаке, в Linux, Windows или Docker, а также в базе данных SQL Azure и хранилище данных SQL Azure. 

| Язык | Платформа | ORM |
| :-- | :-- | :-- |
| C# | Windows, Linux, macOS | [Entity Framework](https://docs.microsoft.com/ef)<br>[Entity Framework Core](https://docs.microsoft.com/ef/core/index) |
| Java | Windows, Linux, macOS |[Hibernate ORM](https://hibernate.org/orm)|
| PHP | Windows, Linux | [Laravel (Eloquent)](https://laravel.com/docs/5.0/eloquent) |
| Node.js | Windows, Linux, macOS | [Sequelize ORM](https://docs.sequelizejs.com) |
| Python | Windows, Linux, macOS |[Django](https://www.djangoproject.com/) |
| Ruby | Windows, Linux, macOS | [Ruby on Rails](https://rubyonrails.org/) |

## <a name="related-links"></a>Связанные ссылки
- [Драйверы SQL Server](https://msdn.microsoft.com/library/mt654049.aspx) для подключения из клиентских приложений
