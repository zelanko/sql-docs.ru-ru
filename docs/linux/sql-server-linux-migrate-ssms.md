---
title: Экспорт и импорт базы данных в Linux
description: ''
author: VanMSFT
ms.author: vanto
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 2210cfc3-c23a-4025-a551-625890d6845f
ms.openlocfilehash: f99ff799ec91ea455cc37bd994c8555330a8ff0f
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68105555"
---
# <a name="export-and-import-a-database-on-linux-with-ssms-or-sqlpackageexe-on-windows"></a>Экспорт и импорт базы данных в Linux с помощью SSMS или SqlPackage.exe в Windows

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье показано, как использовать [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md) и [SqlPackage.exe](https://msdn.microsoft.com/library/hh550080.aspx) для экспорта и импорта базы данных в SQL Server на базе Linux. SSMA и SqlPackage.exe — это приложения Windows, поэтому используйте эту методику при наличии компьютера Windows, который может подключаться к удаленному экземпляру SQL Server в Linux.

Всегда следует устанавливать и использовать самую последнюю версию SQL Server Management Studio (SSMS), как описано в статье [Использование SSMS в Windows для подключения к SQL Server на Linux](sql-server-linux-manage-ssms.md).

> [!NOTE]
> При переносе базы данных из одного экземпляра SQL Server в другой рекомендуется использовать [резервное копирование и восстановление](sql-server-linux-migrate-restore-database.md).

## <a name="export-a-database-with-ssms"></a>Экспорт базы данных с помощью SSMS

1. Запустите SSMS, введя **Microsoft SQL Server Management Studio** в поле поиска Windows, а затем щелкните классическое приложение.

    ![SQL Server Management Studio](./media/sql-server-linux-manage-ssms/ssms.png) 

2. Подключитесь к базе данных-источнику в обозревателе объектов. База данных-источник может находиться в Microsoft SQL Server, запущенном локально или в облаке, в Linux, Windows или Docker, а также в базе данных SQL Azure или хранилище данных SQL Azure.

3. Щелкните правой кнопкой мыши базу данных-источник в обозревателе объектов, наведите указатель на пункт **Задачи** и выберите пункт **Экспорт приложения уровня данных...**

4. В мастере экспорта нажмите кнопку **Далее**, а затем на вкладке **Параметры** настройте экспорт, чтобы сохранить BACPAC-файл в расположении локального диска или в BLOB-объекте Azure.

5. По умолчанию экспортируются все объекты в базе данных. Перейдите на вкладку **Дополнительно** и выберите объекты базы данных, которые необходимо экспортировать.

6. Нажмите кнопку **Далее** , а затем кнопку **Готово**.

BACPAC-файл успешно создается в выбранном расположении, и вы готовы импортировать его в целевую базу данных.

## <a name="import-a-database-with-ssms"></a>Импорт базы данных с помощью SSMS

1. Запустите SSMS, введя **Microsoft SQL Server Management Studio** в поле поиска Windows, а затем щелкните классическое приложение.

    ![SQL Server Management Studio](./media/sql-server-linux-manage-ssms/ssms.png) 

2. Подключитесь к целевому серверу в обозревателе объектов. Целевой сервер может находиться в Microsoft SQL Server, запущенном локально или в облаке, в Linux, Windows или Docker, а также в базе данных SQL Azure или хранилище данных SQL Azure.

3. Щелкните правой кнопкой мыши папку **Базы данных** в обозревателе объектов и выберите пункт **Импорт приложения уровня данных...**

4. Чтобы создать базу данных на целевом сервере, укажите BACPAC-файл на локальном диске или выберите учетную запись хранения Azure и контейнер, куда вы отправили BACPAC-файл.

5. Укажите имя для новой базы данных. При импорте базы данных в базе данных SQL Azure задайте выпуск базы данных SQL Microsoft Azure (уровень служб), максимальный размер базы данных и цель обслуживания (уровень производительности).

6. Нажмите кнопку **Далее**, а затем кнопку **Готово**, чтобы импортировать BACPAC-файл в новую базу данных на целевом сервере.

BACPAC-файл импортируется для создания базы данных на указанном целевом сервере.

## <a id="sqlpackage"></a> Параметр командной строки SqlPackage

Для экспорта и импорта BACPAC-файлов также можно использовать программу командной строки SQL Server Data Tools (SSDT) — [SqlPackage.exe](https://msdn.microsoft.com/library/hh550080.aspx).

В следующем примере команда экспортирует BACPAC-файл.

```bash
SqlPackage.exe /a:Export /ssn:tcp:<your_server> /sdn:<your_database> /su:<username> /sp:<password> /tf:<path_to_bacpac>
```

Используйте следующую команду для импорта схемы базы данных и пользовательских данных из BACPAC-файла.

```bash
SqlPackage.exe /a:Import /tsn:tcp:<your_server> /tdn:<your_database> /tu:<username> /tp:<password> /sf:<path_to_bacpac>

```

## <a name="see-also"></a>См. также раздел
Дополнительные сведения об использовании SSMS см. в разделе [Использование SQL Server Management Studio](https://msdn.microsoft.com/library/ms174173.aspx). Дополнительные сведения о SqlPackage.exe см. в [справочной документации по SqlPackage](https://msdn.microsoft.com/library/hh550080.aspx).
