---
title: "Экспорт и импорт базы данных на платформе Linux | Документы Microsoft"
description: 
author: sanagama
ms.author: sanagama
manager: jhubbard
ms.date: 07/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 2210cfc3-c23a-4025-a551-625890d6845f
ms.custom: H1Hack27Feb2017
ms.translationtype: MT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: ef4a59f57f0bd99951297733e51bbc02b81e78ef
ms.contentlocale: ru-ru
ms.lasthandoff: 09/21/2017

---
# <a name="export-and-import-a-database-on-linux-with-ssms-or-sqlpackageexe-on-windows"></a>Экспорт и импорт базы данных в Linux с помощью SSMS или SqlPackage.exe в Windows

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

В этом разделе показано, как использовать [SQL Server Management Studio (SSMS)](/sql-docs/docs/ssms/download-sql-server-management-studio-ssms) и [SqlPackage.exe](https://msdn.microsoft.com/library/hh550080.aspx) для экспорта и импорта базы данных на RC2 2017 г. SQL Server в Linux. Среда SSMS и SqlPackage.exe приложений Windows, поэтому используйте этот метод, если компьютером Windows, можно подключиться к удаленному экземпляру SQL Server в Linux.

Следует всегда устанавливать и использовать последнюю версию служб SQL Server Management Studio (SSMS), как описано в [используйте SSMS в Windows для подключения к SQL Server в Linux](sql-server-linux-develop-use-ssms.md)

> [!NOTE]
> При переносе базы данных из одного экземпляра SQL Server на другой, рекомендуется использовать [резервного копирования и восстановления](sql-server-linux-migrate-restore-database.md).

## <a name="export-a-database-with-ssms"></a>Экспорт базы данных с помощью SSMS

1. Запустите SSMS, введя **Microsoft SQL Server Management Studio** поле поиска в Windows и нажмите кнопку классического приложения.

    ![Среда SQL Server Management Studio](./media/sql-server-linux-develop-use-ssms/ssms.png) 

2. Подключиться к исходной базы данных в обозревателе объектов. База данных-источник может быть в Microsoft SQL Server, работающий локально или в облаке, в Linux, Windows или Docker и базы данных SQL Azure или хранилище данных SQL Azure.

3. Базы данных-источника в обозревателе объектов щелкните правой кнопкой мыши **задачи**и нажмите кнопку **Экспорт приложения уровня данных...**

4. В окне мастера экспорта нажмите кнопку **Далее**, а затем на **параметры** настройте экспорта, чтобы сохранить BACPAC-файл, либо на локальном диске или в BLOB-объект Azure.

5. По умолчанию экспортируются все объекты в базе данных. Нажмите кнопку **вкладка "Дополнительно"** и выбрать объекты базы данных, которые требуется экспортировать.

6. Нажмите кнопку **Далее** , а затем кнопку **Готово**.

*. BACPAC-файл успешно создан в выбранное расположение, и вы будете готовы импортировать его в целевой базе данных.

## <a name="import-a-database-with-ssms"></a>Импорт базы данных с помощью SSMS

1. Запустите SSMS, введя **Microsoft SQL Server Management Studio** поле поиска в Windows и нажмите кнопку классического приложения.

    ![Среда SQL Server Management Studio](./media/sql-server-linux-develop-use-ssms/ssms.png) 

2. Подключения на целевой сервер в обозревателе объектов. Целевой сервер может быть Microsoft SQL Server, работающий локально или в облаке, в Linux, Windows или Docker и базы данных SQL Azure или хранилище данных SQL Azure.

3. Щелкните правой кнопкой мыши **баз данных** папки в обозревателе объектов и нажмите кнопку **Импорт приложения уровня данных...**

4. Чтобы создать базу данных в целевом сервере, укажите BACPAC-файл на локальном диске или выберите учетную запись хранилища Azure и контейнер, к которому вы отправили BACPAC-файл.

5. Укажите имя базы данных для базы данных. При импорте базы данных в базе данных SQL Azure, установите выпуск служб Microsoft Azure SQL Database (уровень службы), максимальный размер базы данных и цель службы (уровень производительности).

6. Нажмите кнопку **Далее** и нажмите кнопку **Готово** для импорта файла BACPAC в новую базу данных на целевом сервере.

*. Чтобы создать новую базу данных в указанный целевой сервер импортируется BACPAC-файл.

## <a id="sqlpackage"></a>SqlPackage параметр командной строки

Можно также использовать средство командной строки SQL Server Data Tools (SSDT) [SqlPackage.exe](https://msdn.microsoft.com/library/hh550080.aspx), для экспорта и импорта BACPAC-файлов.

Следующая команда экспортирует BACPAC-файла:

```bash
SqlPackage.exe /a:Export /ssn:tcp:<your_server> /sdn:<your_database> /su:<username> /sp:<password> /tf:<path_to_bacpac>
```

Используйте следующую команду для импорта базы данных схемы и данные пользователя с. BACPAC-файла:

```bash
SqlPackage.exe /a:Import /tsn:tcp:<your_server> /tdn:<your_database> /tu:<username> /tp:<password> /sf:<path_to_bacpac>

```

## <a name="see-also"></a>См. также:
Дополнительные сведения о том, как с помощью среды SSMS см. в разделе [использовать SQL Server Management Studio](https://msdn.microsoft.com/library/ms174173.aspx). Дополнительные сведения о SqlPackage.exe см. в разделе [SqlPackage справочной документации](https://msdn.microsoft.com/library/hh550080.aspx).

