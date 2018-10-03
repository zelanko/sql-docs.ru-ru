---
title: Массовое копирование данных в SQL Server на Linux | Документация Майкрософт
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 01/30/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 7b93d0d7-7946-4b78-b33a-57d6307cdfa9
ms.openlocfilehash: 506d98acd28b38d0ce8867f96229632a306ae680
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47812156"
---
# <a name="bulk-copy-data-with-bcp-to-sql-server-on-linux"></a>Массовое копирование данных с помощью программы bcp для SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье показано, как использовать [bcp](../tools/bcp-utility.md) программа командной строки для массового копирования данных между экземпляром SQL Server в Linux и файлом данных в указанном пользователем формате.

Можно использовать `bcp` выполнять импорт большого количества строк в таблицы SQL Server или экспорт данных из таблиц SQL Server в файлы данных. За исключением случаев использования с параметром queryout `bcp` не требует знания языка Transact-SQL. `bcp` Программа работает с Microsoft SQL Server локально или в облаке, в Linux, Windows или Docker и базы данных SQL Azure и хранилище данных SQL Azure.

В этой статье показано, как выполнить следующие действия:
- Импорт данных в таблицу с помощью `bcp in` команды
- Экспорт данных из таблицы с помощью `bcp out` команды

## <a name="install-the-sql-server-command-line-tools"></a>Установка программ командной строки SQL Server

`bcp` является частью средства командной строки SQL Server, которые не устанавливаются автоматически вместе с SQL Server в Linux. Если вы еще не установили средства командной строки SQL Server на компьютере Linux, необходимо установить их. Дополнительные сведения о том, как установить средства выберите дистрибутива Linux из следующего списка:

- [Red Hat Enterprise Linux (RHEL)](sql-server-linux-setup-tools.md#RHEL)
- [Ubuntu](sql-server-linux-setup-tools.md#ubuntu)
- [SUSE Linux Enterprise Server (SLES)](sql-server-linux-setup-tools.md#SLES)

## <a name="import-data-with-bcp"></a>Импорт данных с помощью программы bcp

В этом руководстве Создание образца базы данных и таблицы в локальном экземпляре SQL Server (**localhost**), а затем использовать `bcp` загружался в образце таблицы из текстового файла на диске.

### <a name="create-a-sample-database-and-table"></a>Создание образца базы данных и таблицы

Начнем с создания образца базы данных с простой таблицей, которая используется в остальной части этого руководства.

1. В среде Linux откройте окно терминала команд.

2. Скопируйте и вставьте следующие команды в окне терминала. Эти команды используют **sqlcmd** программы командной строки для создания образца базы данных (**BcpSampleDB**) и таблица (**TestEmployees**) на локальном экземпляре SQL Server (**localhost**). Не забудьте заменить `username` и `<your_password>` при необходимости перед выполнением следующих команд.

Создать базу данных **BcpSampleDB**:
```bash 
sqlcmd -S localhost -U sa -P <your_password> -Q "CREATE DATABASE BcpSampleDB;"
```
Создать таблицу **TestEmployees** в базе данных **BcpSampleDB**:
```bash 
sqlcmd -S localhost -U sa -P <your_password> -d BcpSampleDB -Q "CREATE TABLE TestEmployees (Id INT IDENTITY(1,1) NOT NULL PRIMARY KEY, Name NVARCHAR(50), Location NVARCHAR(50));"
```
### <a name="create-the-source-data-file"></a>Создание файла источника данных
Скопируйте и вставьте следующую команду в окне терминала. Мы используем встроенную `cat` команду, чтобы создать текстовый файл данных с помощью трех записей сохраните файл в домашнем каталоге как **~/test_data.txt**. Полям в записях разделяются запятыми.

```bash
cat > ~/test_data.txt << EOF
1,Jared,Australia
2,Nikita,India
3,Tom,Germany
EOF
```

Чтобы узнать, что файл данных был создан правильно, выполнив следующую команду в окне терминала:
```bash 
cat ~/test_data.txt
```

Там отобразится следующее в окне терминала:
```bash
1,Jared,Australia
2,Nikita,India
3,Tom,Germany
```

### <a name="import-data-from-the-source-data-file"></a>Импорт данных из файла источника данных
Скопируйте и вставьте следующие команды в окне терминала. Эта команда использует `bcp` для подключения к локальному экземпляру SQL Server (**localhost**) и импортировать данные из файла данных (**~/test_data.txt**) в таблицу (**TestEmployees** ) в базе данных (**BcpSampleDB**). Не забудьте заменить имя пользователя и `<your_password>` при необходимости перед выполнением следующих команд.

```bash 
bcp TestEmployees in ~/test_data.txt -S localhost -U sa -P <your_password> -d BcpSampleDB -c -t  ','
```

Ниже приведен краткий обзор параметров командной строки, мы использовали с `bcp` в этом примере:
- `-S`: Указывает экземпляр SQL Server, к которому осуществляется подключение
- `-U`: Указывает идентификатор входа, используемый для подключения к SQL Server
- `-P`: Указывает пароль для идентификатора входа
- `-d`: указывает базу данных для подключения к
- `-c`: выполняет операции, используя символьный тип данных
- `-t`: Указывает признак конца поля. Мы используем `comma` признаком конца поля для записи в наш файл данных

> [!NOTE]
> В этом примере мы не указываете пользовательского признака конца строки. Строки в текстовом файле данных были правильно завершаться `newline` когда мы использовали `cat` команду, чтобы создать файл данных ранее.

Вы можете проверить, что данные были успешно импортированы, выполнив следующую команду в окне терминала. Не забудьте заменить `username` и `<your_password>` при необходимости перед выполнением команды.
```bash 
sqlcmd -S localhost -d BcpSampleDB -U sa -P <your_password> -I -Q "SELECT * FROM TestEmployees;"
```

Этого должен отобразиться следующие результаты:
```bash
Id          Name                Location
----------- ------------------- -------------------
          1 Jared               Australia
          2 Nikita              India
          3 Tom                 Germany

(3 rows affected)
```

## <a name="export-data-with-bcp"></a>Экспорт данных с помощью bcp

В этом руководстве вы используете `bcp` для экспорта данных из образец таблицы, созданную ранее в новый файл данных.

Скопируйте и вставьте следующие команды в окне терминала. Эти команды используют `bcp` программы командной строки для экспорта данных из таблицы **TestEmployees** в базе данных **BcpSampleDB** в новый файл данных с именем **~/test_export.txt** .  Не забудьте заменить имя пользователя и `<your_password>` при необходимости перед выполнением команды.

```bash 
bcp TestEmployees out ~/test_export.txt -S localhost -U sa -P <your_password> -d BcpSampleDB -c -t ','
```

Вы можете убедиться, что данные экспортированы, выполнив следующую команду в окне терминала:
```bash 
cat ~/test_export.txt
```

Там отобразится следующее в окне терминала:
```
1,Jared,Australia
2,Nikita,India
3,Tom,Germany
```

## <a name="see-also"></a>См. также
- [bcp, программа](../tools/bcp-utility.md)
- [Форматы данных для совместимости с помощью программы bcp](../relational-databases/import-export/specify-data-formats-for-compatibility-when-using-bcp-sql-server.md)
- [Массовый импорт данных с помощью инструкции BULK INSERT](../relational-databases/import-export/import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)
- [Инструкции BULK INSERT (Transact-SQL)](../t-sql/statements/bulk-insert-transact-sql.md)
