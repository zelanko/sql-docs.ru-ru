---
title: "Массовое копирование данных SQL Server для Linux | Документы Microsoft"
description: 
author: sanagama
ms.author: sanagama
manager: jhubbard
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 7b93d0d7-7946-4b78-b33a-57d6307cdfa9
ms.workload: On Demand
ms.openlocfilehash: a6c760a78894dbda62320da0f8e59ed1aa3f2bcf
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2017
---
# <a name="bulk-copy-data-with-bcp-to-sql-server-on-linux"></a>Массовое копирование данных с помощью программы bcp для SQL Server в Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

В этом разделе показано, как использовать [bcp](../tools/bcp-utility.md) служебной программы командной строки для массового копирования данных между экземпляром 2017 г. SQL Server в Linux и файлом данных в указанном пользователем формате.

Можно использовать `bcp` для импорта большого количества строк в таблицы SQL Server или экспорта данных из таблицы SQL Server в файлы данных. За исключением случаев использования с параметром queryout `bcp` не требует знания языка Transact-SQL. `bcp` Служебной программы командной строки работает с Microsoft SQL Server, работающий локально или в облаке, Linux, Windows или Docker и базы данных SQL Azure и хранилище данных SQL Azure.

В этом разделе будет показано, как для:
- Импорт данных в таблицы с помощью `bcp in` команды
- Экспорт данных из таблицы подписку `bcp out` команды

## <a name="install-the-sql-server-command-line-tools"></a>Установите средства командной строки SQL Server

`bcp`является частью средства командной строки SQL Server, которые не устанавливается автоматически вместе с SQL Server в Linux. Если вы уже установили средства командной строки SQL Server на компьютере Linux, необходимо установить их. Дополнительные сведения о том, как установить инструменты отладки выберите Ваш дистрибутив Linux из следующего списка:

- [Red Hat Enterprise Linux (RHEL)](sql-server-linux-setup-tools.md#RHEL)
- [Ubuntu](sql-server-linux-setup-tools.md#ubuntu)
- [SUSE Linux Enterprise Server (SLES)](sql-server-linux-setup-tools.md#SLES)

## <a name="import-data-with-bcp"></a>Импорт данных с помощью программы bcp

В этом учебнике вы создадите образец базы данных и таблицы на локальном экземпляре SQL Server (**localhost**), а затем используйте `bcp` для загрузки в образец таблицы из текстового файла на диске.

### <a name="create-a-sample-database-and-table"></a>Создание образца базы данных и таблицы

Давайте начнем с создания образца базы данных с простой таблицы, которая будет использоваться в оставшейся части этого учебника.

1. На компьютере Linux откройте терминал команды.

2. Скопируйте и вставьте приведенные ниже команды в окне терминала. Эти команды используют **sqlcmd** служебной программы командной строки для создания образца базы данных (**BcpSampleDB**) и таблицу (**TestEmployees**) на локальном экземпляре SQL Server (**localhost**). Не забудьте заменить `username` и `<your_password>` при необходимости перед выполнением команды.

Создайте базу данных **BcpSampleDB**:
```bash 
sqlcmd -S localhost -U sa -P <your_password> -Q "CREATE DATABASE BcpSampleDB;"
```
Создать таблицу **TestEmployees** в базе данных **BcpSampleDB**:
```bash 
sqlcmd -S localhost -U sa -P <your_password> -d BcpSampleDB -Q "CREATE TABLE TestEmployees (Id INT IDENTITY(1,1) NOT NULL PRIMARY KEY, Name NVARCHAR(50), Location NVARCHAR(50));"
```
### <a name="create-the-source-data-file"></a>Создать файл источника данных
Скопируйте и вставьте ниже команду в окне терминала. Мы будем использовать встроенные `cat` команду, чтобы создать пример текстового файла данных с 3 записи сохраните файл в домашнем каталоге как **~/test_data.txt**. Полям в записях разделяются запятыми.

```bash
cat > ~/test_data.txt << EOF
1,Jared,Australia
2,Nikita,India
3,Tom,Germany
EOF
```

Можно проверить, что файл данных был создан правильно, выполнив команду ниже, в окне терминала.
```bash 
cat ~/test_data.txt
```

После этого должен отобразиться следующие в окне терминала:
```bash
1,Jared,Australia
2,Nikita,India
3,Tom,Germany
```

### <a name="import-data-from-the-source-data-file"></a>Импорт данных из файла источника данных
Скопируйте и вставьте приведенные ниже команды в окне терминала. Эта команда использует `bcp` для подключения к локальному экземпляру SQL Server (**localhost**) и импортировать данные из файла данных (**~/test_data.txt**) в таблицу (**TestEmployees**) в базе данных (**BcpSampleDB**). Не забудьте заменить имя пользователя и `<your_password>` при необходимости перед выполнением команды.

```bash 
bcp TestEmployees in ~/test_data.txt -S localhost -U sa -P <your_password> -d BcpSampleDB -c -t  ','
```

Ниже приведен краткий обзор параметров командной строки, мы использовали с `bcp` в этом примере:
- `-S`: Указывает экземпляр SQL Server, к которому выполняется подключение
- `-U`: Указывает идентификатор входа, используемый для подключения к SQL Server
- `-P`: Указывает пароль для идентификатора входа
- `-d`: задает для подключения к базе данных
- `-c`: выполняет операции, используя символьный тип данных
- `-t`: Указывает признак конца поля. Мы используем `comma` признаком конца поля для записи в наш файл данных

> [!NOTE]
> В этом примере мы не задается пользовательского признака конца строки. Строки в текстовом файле данных были правильно завершаться `newline` при использовании `cat` команду, чтобы создать файл данных более ранних версий.

Вы можете проверить, данные успешно импортирован, выполнив команду ниже, в окне терминала. Не забудьте заменить `username` и `<your_password>` при необходимости перед выполнением команды.
```bash 
sqlcmd -S localhost -d BcpSampleDB -U sa -P <your_password> -I -Q "SELECT * FROM TestEmployees;"
```

После этого должен отобразиться следующие результаты:
```bash
Id          Name                Location
----------- ------------------- -------------------
          1 Jared               Australia
          2 Nikita              India
          3 Tom                 Germany

(3 rows affected)
```

## <a name="export-data-with-bcp"></a>Экспорт данных с помощью программы bcp

В этом учебнике используется `bcp` для экспорта данных из таблицы-образца, созданную ранее в новый файл данных.

Скопируйте и вставьте приведенные ниже команды в окне терминала. Эти команды используют `bcp` служебной программы командной строки для экспорта данных из таблицы **TestEmployees** в в базе данных **BcpSampleDB** в новый файл данных с именем **~/test_export.txt**.  Не забудьте заменить имя пользователя и `<your_password>` при необходимости перед выполнением команды.

```bash 
bcp TestEmployees out ~/test_export.txt -S localhost -U sa -P <your_password> -d BcpSampleDB -c -t ','
```

Это можно проверить, что данные экспортированы правильно, выполнив команду ниже, в окне терминала.
```bash 
cat ~/test_export.txt
```

После этого должен отобразиться следующие в окне терминала:
```
1,Jared,Australia
2,Nikita,India
3,Tom,Germany
```

## <a name="see-also"></a>См. также
- [bcp, программа](../tools/bcp-utility.md)
- [Форматы данных для совместимости с помощью программы bcp](../relational-databases/import-export/specify-data-formats-for-compatibility-when-using-bcp-sql-server.md)
- [Массовый импорт данных с помощью инструкции BULK INSERT](../relational-databases/import-export/import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)
- [BULK INSERT (Transact-SQL)](../t-sql/statements/bulk-insert-transact-sql.md)
