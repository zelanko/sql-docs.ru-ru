---
title: Массовое копирование данных в SQL Server на Linux
description: В этой статье описывается служебная программа bcp. С помощью bcp можно импортировать большое количество строк в таблицы SQL Server или экспортировать данные из таблиц SQL Server в файлы данных.
author: VanMSFT
ms.author: vanto
ms.date: 01/30/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 7b93d0d7-7946-4b78-b33a-57d6307cdfa9
ms.openlocfilehash: 1d4c924652ec21ab4ed8e7c79d01d7f36835715b
ms.sourcegitcommit: a5398f107599102af7c8cda815d8e5e9a367ce7e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/13/2020
ms.locfileid: "92006555"
---
# <a name="bulk-copy-data-with-bcp-to-sql-server-on-linux"></a>Массовое копирование данных в SQL Server на Linux с помощью программы bcp

[!INCLUDE [SQL Server - Linux](../includes/applies-to-version/sql-linux.md)]

В этой статье приводятся сведения об использовании программы командной строки [bcp](../tools/bcp-utility.md) для массового копирования данных между экземпляром SQL Server на Linux и файлом данных в формате, заданном пользователем.

С помощью программы `bcp` можно импортировать большое количество строк в таблицы SQL Server или экспортировать данные из таблиц SQL Server в файлы данных. За исключением случаев использования параметра queryout, применение программы `bcp` не требует знания языка Transact-SQL. Служебная программа командной строки `bcp` работает в экземпляре Microsoft SQL Server, запущенном локально или в облаке, в Linux, Windows или Docker, а также в Базе данных SQL Azure и Azure Synapse Analytics.

В этой статье показано, как выполнить следующие действия:
- Импорт данных в таблицу с помощью команды `bcp in`
- Экспорт данных из таблицы с помощью команды `bcp out`

## <a name="install-the-sql-server-command-line-tools"></a>Установка программ командной строки SQL Server

`bcp` входит в число программ командной строки SQL Server, которые не устанавливаются автоматически с SQL Server на Linux. Если вы еще не установили программы командной строки SQL Server на компьютере Linux, сделайте это. Чтобы получить дополнительные сведения об установке программ, выберите нужный дистрибутив Linux из следующего списка:

- [Red Hat Enterprise Linux (RHEL)](sql-server-linux-setup-tools.md#RHEL)
- [Ubuntu](sql-server-linux-setup-tools.md#ubuntu)
- [SUSE Linux Enterprise Server (SLES)](sql-server-linux-setup-tools.md#SLES)

## <a name="import-data-with-bcp"></a>Импорт данных с помощью bcp

В этом руководстве приводятся инструкции по созданию образца базы данных и таблицы на локальном экземпляре SQL Server (**localhost**) и использованию `bcp` для загрузки в образец таблицы из текстового файла на диске.

### <a name="create-a-sample-database-and-table"></a>Создание образца базы данных и таблицы

Начнем с создания образца базы данных с простой таблицей, которая будет использоваться в оставшейся части этого руководства.

1. На компьютере Linux откройте терминал ввода команд.

2. Скопируйте и вставьте в окно терминала следующие команды. Для создания образца базы данных (**BcpSampleDB**) и таблицы (**TestEmployees**) на локальном экземпляре SQL Server (**localhost**) эти команды используют служебную программу **sqlcmd**. При необходимости перед выполнением команд замените `username` и `<your_password>`.

Создайте базу данных **BcpSampleDB**:
```bash 
sqlcmd -S localhost -U sa -P <your_password> -Q "CREATE DATABASE BcpSampleDB;"
```
Создайте таблицу **TestEmployees** в базе данных **BcpSampleDB**:
```bash 
sqlcmd -S localhost -U sa -P <your_password> -d BcpSampleDB -Q "CREATE TABLE TestEmployees (Id INT IDENTITY(1,1) NOT NULL PRIMARY KEY, Name NVARCHAR(50), Location NVARCHAR(50));"
```
### <a name="create-the-source-data-file"></a>Создание файла исходных данных
Скопируйте и вставьте в окно терминала следующую команду. Для создания образца файла текстовых данных с тремя записями и сохранения файла в домашнем каталоге как **~/test_data.txt** используется встроенная команда `cat`. Поля в записях разделяются запятыми.

```bash
cat > ~/test_data.txt << EOF
1,Jared,Australia
2,Nikita,India
3,Tom,Germany
EOF
```

Проверьте правильность создания файла данных, выполнив в окне терминала следующую команду:
```bash 
cat ~/test_data.txt
```

В окне терминала должны отобразиться следующие строки:
```bash
1,Jared,Australia
2,Nikita,India
3,Tom,Germany
```

### <a name="import-data-from-the-source-data-file"></a>Импорт данных из исходного файла данных
Скопируйте и вставьте в окно терминала следующие команды. Для подключения к локальному экземпляру SQL Server (**localhost**) и импорта данных из файла данных ( **~/test_data.txt**) в таблицу (**TestEmployees**) в базе данных (**BcpSampleDB**) эта команда использует `bcp`. При необходимости перед выполнением команд замените имя пользователя и `<your_password>`.

```bash 
bcp TestEmployees in ~/test_data.txt -S localhost -U sa -P <your_password> -d BcpSampleDB -c -t  ','
```

Ниже приведен краткий обзор параметров командной строки, которые использовались в программе `bcp` в этом примере.
- `-S`: указывает экземпляр SQL Server, к которому выполняется подключение.
- `-U`: указывает идентификатор входа, используемый для подключения к SQL Server.
- `-P`: указывает пароль для идентификатора имени входа.
- `-d`: указывает базу данных, к которой нужно подключиться.
- `-c`: выполняет операцию, используя символьный тип данных.
- `-t`: указывает признак конца поля. В качестве признака конца поля для записей в файле данных в этом руководстве используется `comma`.

> [!NOTE]
> В этом примере пользовательский признак конца строки не указывается. Когда мы использовали команду `cat` для создания файла данных, строки в текстовом файле данных были корректно завершены символом `newline`.

Проверьте успешное завершение импорта данных, выполнив в окне терминала следующую команду: При необходимости перед выполнением команд замените `username` и `<your_password>`.
```bash 
sqlcmd -S localhost -d BcpSampleDB -U sa -P <your_password> -I -Q "SELECT * FROM TestEmployees;"
```

Должны отобразиться следующие результаты:
```bash
Id          Name                Location
----------- ------------------- -------------------
          1 Jared               Australia
          2 Nikita              India
          3 Tom                 Germany

(3 rows affected)
```

## <a name="export-data-with-bcp"></a>Экспорт данных с помощью bcp

В этом руководстве экспорт данных из образца таблицы, созданного ранее, в новый файл данных выполняется с помощью программы `bcp`.

Скопируйте и вставьте в окно терминала следующие команды. Для экспорта данных из таблицы **TestEmployees** в базе данных **BcpSampleDB** в новый файл данных **~/test_export.txt** эти команды используют служебную программу `bcp`.  При необходимости перед выполнением команд замените имя пользователя и `<your_password>`.

```bash 
bcp TestEmployees out ~/test_export.txt -S localhost -U sa -P <your_password> -d BcpSampleDB -c -t ','
```

Проверьте правильность экспорта данных, выполнив в окне терминала следующую команду:
```bash 
cat ~/test_export.txt
```

В окне терминала должны отобразиться следующие строки:
```
1,Jared,Australia
2,Nikita,India
3,Tom,Germany
```

## <a name="see-also"></a>См. также раздел
- [bcp, программа](../tools/bcp-utility.md)
- [Указание форматов данных для совместимости с помощью программы bcp](../relational-databases/import-export/specify-data-formats-for-compatibility-when-using-bcp-sql-server.md)
- [Массовый импорт данных с помощью инструкции BULK INSERT или OPENROWSET(BULK...) (SQL Server)](../relational-databases/import-export/import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)
- [BULK INSERT (Transact-SQL)](../t-sql/statements/bulk-insert-transact-sql.md)
