---
title: Экспорт и импорт базы данных на платформе Linux | Документация Майкрософт
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.technology: linux
ms.assetid: 2210cfc3-c23a-4025-a551-625890d6845f
ms.custom: sql-linux
ms.openlocfilehash: 36e18344efe0e3e329d4cb2672b51f23f0900128
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2018
ms.locfileid: "46713186"
---
# <a name="export-and-import-a-database-on-linux-with-ssms-or-sqlpackageexe-on-windows"></a>Экспорт и импорт базы данных на платформе Linux с помощью SSMS или SqlPackage.exe на Windows

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье показано, как использовать [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md) и [SqlPackage.exe](https://msdn.microsoft.com/library/hh550080.aspx) для экспорта и импорта базы данных на сервере SQL Server в Linux. SSMS и SqlPackage.exe — приложения Windows, поэтому используйте этот метод, если используется компьютер Windows, который может подключиться к удаленному экземпляру SQL Server в Linux.

Всегда следует устанавливать и использовать самой последней версии из SQL Server Management Studio (SSMS), как описано в разделе [используйте SSMS в Windows для подключения к SQL Server в Linux](sql-server-linux-manage-ssms.md)

> [!NOTE]
> Если вы переносите базу данных из одного экземпляра SQL Server на другой, рекомендуется использовать [резервного копирования и восстановления](sql-server-linux-migrate-restore-database.md).

## <a name="export-a-database-with-ssms"></a>Экспорт базы данных с помощью SSMS

1. Запустите SSMS, введя **Microsoft SQL Server Management Studio** поле поиска Windows и выберите классическое приложение.

    ![SQL Server Management Studio](./media/sql-server-linux-manage-ssms/ssms.png) 

2. Подключиться к исходной базы данных в обозревателе объектов. База данных-источник может быть в Microsoft SQL Server локально или в облаке, в Linux, Windows или Docker и базы данных SQL Azure или хранилище данных SQL Azure.

3. Базы данных-источника в обозревателе объектов щелкните правой кнопкой мыши **задачи**и нажмите кнопку **Экспорт приложения уровня данных...**

4. В окне мастера экспорта щелкните **Далее**, а затем на **параметры** вкладке, настройте сохранение bacpac-файл на локальный диск или большой двоичный объект Azure.

5. По умолчанию экспортируются все объекты в базе данных. Нажмите кнопку **вкладка "Дополнительно"** и выбрать объекты базы данных, которые необходимо экспортировать.

6. Нажмите кнопку **Далее** , а затем кнопку **Готово**.

*. Bacpac-файл будет создан в расположении, который вы выбрали, и вы будете готовы импортировать его в целевую базу данных.

## <a name="import-a-database-with-ssms"></a>Импорт базы данных с помощью SSMS

1. Запустите SSMS, введя **Microsoft SQL Server Management Studio** поле поиска Windows и выберите классическое приложение.

    ![SQL Server Management Studio](./media/sql-server-linux-manage-ssms/ssms.png) 

2. Подключитесь к целевой сервер в обозревателе объектов. Целевой сервер может быть Microsoft SQL Server локально или в облаке, в Linux, Windows или Docker и базы данных SQL Azure или хранилище данных SQL Azure.

3. Щелкните правой кнопкой мыши **баз данных** папку в обозревателе решений и выберите **Импорт приложения уровня данных...**

4. Создание базы данных в целевой сервер, укажите bacpac-файла с локального диска или выберите учетную запись хранения Azure и контейнер, в который был передан bacpac-файл.

5. Укажите новое имя базы данных для базы данных. При импорте базы данных в базе данных SQL Azure, установите выпуск Microsoft Azure SQL базы данных (уровень служб), максимальный размер базы данных и обслуживания (уровень производительности).

6. Нажмите кнопку **Далее** и нажмите кнопку **Готово** для импорта файла BACPAC в новую базу данных на целевом сервере.

*. Bacpac-файл импортируется для создания новой базы данных в указанный целевой сервер.

## <a id="sqlpackage"></a> Параметр командной строки SqlPackage

Можно также использовать средство командной строки SQL Server Data Tools (SSDT) [SqlPackage.exe](https://msdn.microsoft.com/library/hh550080.aspx), для экспорта и импорта bacpac-файлов.

Например, следующая команда экспортирует bacpac-файла:

```bash
SqlPackage.exe /a:Export /ssn:tcp:<your_server> /sdn:<your_database> /su:<username> /sp:<password> /tf:<path_to_bacpac>
```

Используйте следующую команду для импорта базы данных схемы и данные пользователя с. Bacpac-файла:

```bash
SqlPackage.exe /a:Import /tsn:tcp:<your_server> /tdn:<your_database> /tu:<username> /tp:<password> /sf:<path_to_bacpac>

```

## <a name="see-also"></a>См. также
Дополнительные сведения о том, как использовать SSMS см. в разделе [использовать SQL Server Management Studio](https://msdn.microsoft.com/library/ms174173.aspx). Дополнительные сведения о SqlPackage.exe, см. в разделе [SqlPackage справочная документация по](https://msdn.microsoft.com/library/hh550080.aspx).
