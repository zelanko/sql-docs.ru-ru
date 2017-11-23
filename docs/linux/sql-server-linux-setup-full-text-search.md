---
title: "Установка SQL Server Full-Text Search в Linux | Документы Microsoft"
description: "В этом разделе описывается установка SQL Server Full-Text Search в Linux."
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: bb42076f-e823-4cee-9281-cd3f83ae42f5
ms.workload: Inactive
ms.openlocfilehash: 9ab570753e7bc6cc2b2aded26b2629d00f1bf292
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="install-sql-server-full-text-search-on-linux"></a>Установка SQL Server Full-Text Search в Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Следующие шаги установки [SQL Server Full-Text Search](https://msdn.microsoft.com/library/ms142571.aspx) (**mssql-server-fts**) в Linux. Компонент Full-Text Search позволяет выполнять полнотекстовые запросы к символьным данным в таблицах SQL Server. Известные проблемы в этом выпуске см. в разделе [заметки о выпуске](sql-server-linux-release-notes.md).

> [!NOTE]
> Перед установкой SQL Server Full-Text Search, сначала [Установка SQL Server](sql-server-linux-setup.md#platforms). Это настраивает ключи и репозиториев, которые используются при установке **mssql-server-fts** пакета.

Установка SQL Server Full-Text Search для вашей платформы:

- [Red Hat Enterprise Linux](#RHEL)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#SLES)

## <a name="RHEL">Установите на RHEL</a>

Используйте следующие команды для установки **mssql-server-fts** в Red Hat Enterprise Linux. 

```bash
sudo yum install -y mssql-server-fts
```

Если у вас уже есть **mssql-server-fts** установлены, можно обновить до последней версии с помощью следующих команд:

```bash
sudo yum check-update
sudo yum update mssql-server-fts
```

Если вам требуется автономной установки, найдите загрузки пакета компонент Full-text Search в [заметки о выпуске](sql-server-linux-release-notes.md). Затем используйте те же действия автономной установки, описанную в разделе [Установка SQL Server](sql-server-linux-setup.md#offline).

## <a name="ubuntu">Установите на Ubuntu</a>

Используйте следующие команды для установки **mssql-server-fts** на Ubuntu. 

```bash
sudo apt-get update 
sudo apt-get install -y mssql-server-fts
```

Если у вас уже есть **mssql-server-fts** установлены, можно обновить до последней версии с помощью следующих команд:

```bash
sudo apt-get update 
sudo apt-get install -y mssql-server-fts 
```

Если вам требуется автономной установки, найдите загрузки пакета компонент Full-text Search в [заметки о выпуске](sql-server-linux-release-notes.md). Затем используйте те же действия автономной установки, описанную в разделе [Установка SQL Server](sql-server-linux-setup.md#offline).

## <a name="SLES">Установите на SLES</a>

Используйте следующие команды для установки **mssql-server-fts** на SUSE Linux Enterprise Server. 

```bash
sudo zypper install mssql-server-fts
```

Если у вас уже есть **mssql-server-fts** установлены, можно обновить до последней версии с помощью следующих команд:

```bash
sudo zypper refresh
sudo zypper update mssql-server-fts
```

Если вам требуется автономной установки, найдите загрузки пакета компонент Full-text Search в [заметки о выпуске](sql-server-linux-release-notes.md). Затем используйте те же действия автономной установки, описанную в разделе [Установка SQL Server](sql-server-linux-setup.md#offline).

## <a name="supported-languages"></a>Поддерживаемые языки

Компонент Full-Text Search использует [средства разбиения по словам](../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md) , определяющие, как определить отдельные слова на основе языка. Можно получить список средств разбиения по словам, зарегистрированных с помощью запроса к **sys.fulltext_languages** представления каталога. Средства разбиения по словам для следующих языков устанавливаются вместе с SQL Server 2017 г.:

| Язык | КОД языка |
|---|---|
| Нейтральный | 0 |
| Арабский | 1025 |
| Бенгальский (Индия) | 1093 |
| Букмол | 1044 |
| Бразильский | 1046 |
| British English | 2057 |
| Болгарский | 1026 |
| Каталонский | 1027 |
| Китайский (Гонконг, КНР) | 3076 |
| Китайский (Макао SAR) | 5124 |
| Китайский (Сингапур) | 4100 |
| Хорватский | 1050 |
| Чешский | 1029 |
| Danish | 1030 |
| Нидерландский | 1043 |
| Английский | 1033 |
| Французский | 1036 |
| Немецкий | 1031 |
| Греческий | 1032 |
| Гуджарати | 1095 |
| Hebrew | 1037 |
| Hindi | 1081 |
| Исландский | 1039 |
| Индонезийский | 1057 |
| Итальянский | 1040 |
| Японский | 1041 |
| Каннада | 1099 |
| Корейский | 1042 |
| Латышский | 1062 |
| Литовский | 1063 |
| Малайский (Малайзия) | 1086 |
| Малайялам | 1100 |
| Маратхи | 1102 |
| Польский | 1045 |
| Португальский | 2070 |
| Панджабский | 1094 |
| Румынский | 1048 |
| Русский | 1049 |
| Сербский (кириллица) | 3098 |
| Сербский (латиница) | 2074 |
| Китайский (упрощенный) | 2052 |
| Словацкий | 1051 |
| Словенский | 1060 |
| Испанский | 3082 |
| Шведский | 1053 |
| Тамильский | 1097 |
| Телугу | 1098 |
| Тайский | 1054 |
| Китайский (традиционный) | 1028 |
| Турецкий | 1055 |
| Украинский | 1058 |
| Урду | 1056 |
| Вьетнамский | 1066 |

## <a id="filters"></a>Фильтры

Компонент Full-Text Search также работает с текстом, хранящихся в двоичные файлы. Но в этом случае требуется установленный фильтр для обработки файла. Дополнительные сведения о фильтрах см. в разделе [Настройка и управление фильтрами для поиска](../relational-databases/search/configure-and-manage-filters-for-search.md).

Можно просмотреть список установленных фильтров, вызвав **sp_help_fulltext_system_components «фильтр»**. Для SQL Server 2017 г устанавливаются следующие фильтры:

| Название компонента | Идентификатор класса | Version |
|---|---|---|
|площадь | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.ANS | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.ASC | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.ascx | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.asm | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.ASP | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.aspx | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.ASX | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.BAS | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.bat | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.bcp | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.c | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.CC | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.CLS | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.cmd | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.cpp | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.cs | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.CSA | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|CSS-файлах | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|CSV-файл | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.cxx | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.DBS | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.DEF | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.dic | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.DOS | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.DSP | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.dsw | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.рсш | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.FAQ | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.FKY | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.h | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.HHC | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.hpp | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|расширением HTA | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.htm | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.HTML | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.htt | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|формата HTW | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.htx | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.hXX | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.i | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.ibq | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.ICS | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.IDL | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.Idq | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.Inc | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.inf | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|INI-файле | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.inl | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.inx | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.Jav | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.Java | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.js | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.kci | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.lgn | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.log | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.lst | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.m3u | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.MAK | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.MK | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|ODC | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.odh | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.ODL | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.pkgdef | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.pkgundef | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.PL | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.PRC | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.rc | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.RC2 | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.rct | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.reg | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.RGS | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.RTF | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.rul | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.s | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.SCC | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.shtm | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.shtml | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.snippet | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.SoL | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.sor | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.srf | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.stm | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.TAB | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.TDL | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|TLH-файлы | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.TLI | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.TRG | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.txt | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.UDF | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.UDT | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.URL | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.usr | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.vbs | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.VIW | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.vsct | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.vsixlangpack | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.vsixmanifest | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.vspscc | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.vsscc | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.vssscc | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.wri | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.WTX | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|XML | 41B9BE05-B3AF-460C-BF0B-2CDD44A093B1 | 12.0.9735.0 |

## <a name="semantic-search"></a>Семантический поиск
[Семантический поиск](../relational-databases/search/semantic-search-sql-server.md) лежит компонент Full-Text Search для извлечения и индексирования статистически соответствующих *ключевых фраз*. Это позволяет запрашивать значения в документах в базе данных. Это также позволяет найти документы, которые похожи.

Для использования семантического поиска, необходимо сначала восстановить базу данных семантической статистики языка на компьютере.

1. С помощью средства, такие как [sqlcmd](sql-server-linux-setup-tools.md), для выполнения следующей команды Transact-SQL на экземпляре SQL Server для Linux. Эта команда восстанавливает базу данных статистики языка.

   ```sql
   RESTORE DATABASE [semanticsdb] FROM
   DISK = N'/opt/mssql/misc/semanticsdb.bak' WITH FILE = 1,
   MOVE N'semanticsdb' TO N'/var/opt/mssql/data/semanticsDB.mdf',
   MOVE N'semanticsdb_log' TO N'/var/opt/mssql/data/semanticsdb_log.ldf', NOUNLOAD, STATS = 5
   GO
   ```

   > [!NOTE]
   > При необходимости измените пути в предыдущей команды RESTORE для настройки конфигурации.

1. Выполните следующую команду Transact-SQL, чтобы зарегистрировать базу данных статистики семантики языка.

    ```sql
    EXEC sp_fulltext_semantic_register_language_statistics_db @dbname = N'semanticsdb';  
    GO
    ```

## <a name="next-steps"></a>Следующие шаги

Сведения о функциях полнотекстового поиска см. в разделе [SQL Server Full-Text Search](../relational-databases/search/full-text-search.md). 
