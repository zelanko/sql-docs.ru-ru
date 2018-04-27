---
title: Подключение библиотек и платформ | Документы Microsoft
description: Список драйверов подключения, которые клиентские приложения могут использовать на различных языках для подключения к Microsoft SQL Server, работающий локально или в облаке, на Docker, Windows или Linux, а также для базы данных SQL Azure и хранилище данных SQL Azure.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: 80efe5ff-09ba-48a0-ac93-a91d62cff47c
ms.workload: Inactive
ms.openlocfilehash: e74d5804d5a6fef00696b62d7f4606dc8fa7599e
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="connectivity-libraries-and-frameworks-for-microsoft-sql-server"></a>Библиотек подключений и платформы для Microsoft SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Извлечение [учебными руководствами для начинающих](http://aka.ms/sqldev) быстро приступить к работе с языки программирования типа C#, Java, Node.js, PHP и Python и построение приложения с помощью SQL Server в Linux или Windows или Docker на macOS.

В следующей таблице перечислены библиотек подключений или *драйверы* , клиентские приложения можно использовать из множества языков для подключения и использования Microsoft SQL Server, работающий локально или в облаке, в Linux, Windows или Docker и также база данных SQL в Azure и хранилище данных Azure SQL. 

| Язык | Платформа | Дополнительные ресурсы | Загрузить | Приступая к работе |
| :-- | :-- | :-- | :-- | :-- |
| C# | Windows, Linux, macOS | [Microsoft ADO.NET для SQL Server](http://msdn.microsoft.com/library/mt657768.aspx) | [Загрузить](https://msdn.microsoft.com/vstudio/aa496123.aspx) | [Начало работы](https://www.microsoft.com/en-us/sql-server/developer-get-started/csharp/ubuntu)
| Java | Windows, Linux, macOS | [Драйвер Microsoft JDBC для SQL Server](http://msdn.microsoft.com/library/mt484311.aspx) | [Загрузить](http://go.microsoft.com/fwlink/?LinkId=245496) |  [Начало работы](https://www.microsoft.com/en-us/sql-server/developer-get-started/java/ubuntu)
| PHP | Windows, Linux, macOS| [Драйвера PHP SQL для SQL Server](http://msdn.microsoft.com/library/dn865013.aspx) | Операционная система: <br/> \* [Windows](https://www.microsoft.com/download/details.aspx?id=20098) <br/> \* [Linux](https://github.com/Microsoft/msphpsql/tree/dev#install-unix) <br/> \* [MacOS](https://github.com/Microsoft/msphpsql/tree/dev#install-unix) |  [Начало работы](https://www.microsoft.com/en-us/sql-server/developer-get-started/php/ubuntu)
| Node.js | Windows, Linux, macOS | [Драйвер Node.js для SQL Server](../connect/node-js/node-js-driver-for-sql-server.md) |  [Начало работы](https://www.microsoft.com/en-us/sql-server/developer-get-started/node/ubuntu)
| Python | Windows, Linux, macOS | [Драйвер Python SQL](../connect/python/python-driver-for-sql-server.md) <br/> \* [pyodbc](http://msdn.microsoft.com/library/mt763257.aspx) |  [Начало работы](https://www.microsoft.com/en-us/sql-server/developer-get-started/python/ubuntu)
| Ruby | Windows, Linux, macOS | [Драйвер Ruby для SQL Server](../connect/ruby/ruby-driver-for-sql-server.md) | [Начало работы](https://www.microsoft.com/en-us/sql-server/developer-get-started/ruby/ubuntu)
| C++ | Windows, Linux, macOS | [Драйвер Microsoft ODBC для SQL Server](https://msdn.microsoft.com/en-us/library/mt654048(v=sql.1).aspx) | [Загрузить](https://msdn.microsoft.com/en-us/library/mt654048(v=sql.1).aspx) |  

В следующей таблице перечислены некоторые примеры объекта реляционного сопоставления (ORM) платформы и веб-платформ, клиентские приложения могут использовать Microsoft SQL Server, работающий локально или в облаке, в Docker, Windows или Linux, а также к базе данных SQL Azure и Хранилище данных Azure SQL. 

| Язык | Платформа | ORM(s) |
| :-- | :-- | :-- |
| C# | Windows, Linux, macOS | [Платформа Entity Framework](https://docs.microsoft.com/en-us/ef)<br>[Entity Framework Core](https://docs.microsoft.com/en-us/ef/core/index) |
| Java | Windows, Linux, macOS |[Режим гибернации ORM](http://hibernate.org/orm)|
| PHP | Windows, Linux | [Laravel (Eloquent)](https://laravel.com/docs/5.0/eloquent) |
| Node.js | Windows, Linux, macOS | [Sequelize ORM](http://docs.sequelizejs.com) |
| Python | Windows, Linux, macOS |[Django](https://www.djangoproject.com/) |
| Ruby | Windows, Linux, macOS | [Ruby на направляющие](http://rubyonrails.org/) |

## <a name="related-links"></a>Связанные ссылки
- [Драйверы для SQL Server](http://msdn.microsoft.com/library/mt654049.aspx) для подключение из клиентских приложений
