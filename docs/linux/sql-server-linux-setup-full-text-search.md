---
title: Установка полнотекстового поиска SQL Server в Linux
description: В этой статье описывается установка SQL Server Full-Text Search в Linux.
author: VanMSFT
ms.author: vanto
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: bb42076f-e823-4cee-9281-cd3f83ae42f5
ms.openlocfilehash: 2f99310a1eaa240db15b4db5f686a4d6cc49c186
ms.sourcegitcommit: f76b4e96c03ce78d94520e898faa9170463fdf4f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2019
ms.locfileid: "70874765"
---
# <a name="install-sql-server-full-text-search-on-linux"></a>Установка полнотекстового поиска SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Для установки [полнотекстового поиска SQL Server](../relational-databases/search/full-text-search.md) (**mssql-server-fts**) в Linux необходимо выполнить приведенные далее действия. Полнотекстовый поиск позволяет выполнять полнотекстовые запросы к символьным данным в таблицах SQL Server. Известные проблемы в этом выпуске рассматриваются в [заметках о выпуске](sql-server-linux-release-notes.md).

> [!NOTE]
> Перед установкой полнотекстового поиска SQL Server сначала [установите SQL Server](sql-server-linux-setup.md#platforms). Это позволит настроить ключи и репозитории, которые следует использовать при установке пакета **mssql-server-fts**.

Установите полнотекстовый поиск SQL Server для своей платформы:

- [Red Hat Enterprise Linux](#RHEL)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#SLES)

## <a name="RHEL">Установка в RHEL</a>

Используйте следующую команду для установки **mssql-server-fts** в Red Hat Enterprise Linux. 

```bash
sudo yum install -y mssql-server-fts
```

Если у вас уже есть **mssql-server-fts**, можно обновить пакет до последней версии, выполнив следующие команды:

```bash
sudo yum check-update
sudo yum update mssql-server-fts
```

Если вам нужна автономная установка, найдите скачиваемый пакет полнотекстового поиска в [заметках о выпуске](sql-server-linux-release-notes.md). Затем выполните действия по автономной установке, описанные в статье [Установка SQL Server](sql-server-linux-setup.md#offline).

## <a name="ubuntu">Установка в Ubuntu</a>

Используйте следующую команду для установки **mssql-server-fts** в Ubuntu. 

```bash
sudo apt-get update 
sudo apt-get install -y mssql-server-fts
```

Если у вас уже есть **mssql-server-fts**, можно обновить пакет до последней версии, выполнив следующие команды:

```bash
sudo apt-get update 
sudo apt-get install -y mssql-server-fts 
```

Если вам нужна автономная установка, найдите скачиваемый пакет полнотекстового поиска в [заметках о выпуске](sql-server-linux-release-notes.md). Затем выполните действия по автономной установке, описанные в статье [Установка SQL Server](sql-server-linux-setup.md#offline).

## <a name="SLES">Установка в SLES</a>

Используйте следующую команду для установки **mssql-server-fts** в SUSE Linux Enterprise Server. 

```bash
sudo zypper install mssql-server-fts
```

Если у вас уже есть **mssql-server-fts**, можно обновить пакет до последней версии, выполнив следующие команды:

```bash
sudo zypper refresh
sudo zypper update mssql-server-fts
```

Если вам нужна автономная установка, найдите скачиваемый пакет полнотекстового поиска в [заметках о выпуске](sql-server-linux-release-notes.md). Затем выполните действия по автономной установке, описанные в статье [Установка SQL Server](sql-server-linux-setup.md#offline).

## <a name="supported-languages"></a>Поддерживаемые языки

В полнотекстовом поиске используются [средства разбиения текста по словам](../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md), позволяющие определять отдельные слова на основе языка. Чтобы получить список зарегистрированных средств разбиения текста по словам, отправьте запрос к представлению каталога **sys.fulltext_languages**. С SQL Server устанавливаются средства разбиения текста по словам для указанных далее языков.

| Язык | Идентификатор языка |
|---|---|
| Нейтральный | 0 |
| Арабский | 1025 |
| Bengali (India) | 1093 |
| Букмол | 1044 |
| Португальский (Бразилия) | 1046 |
| British English | 2057 |
| Болгарский | 1026 |
| Каталонский | 1027 |
| Китайский (Гонконг, КНР) | 3076 |
| Chinese (Macao SAR) | 5124 |
| Chinese (Singapore) | 4100 |
| Хорватский | 1050 |
| Czech | 1029 |
| Danish | 1030 |
| Нидерландский | 1043 |
| Английский | 1033 |
| Французский | 1036 |
| Немецкий | 1031 |
| Greek | 1032 |
| Гуджарати | 1095 |
| Иврит | 1037 |
| Hindi | 1081 |
| Исландский | 1039 |
| Индонезийский | 1057 |
| Итальянский | 1040 |
| Японский | 1041 |
| Каннада | 1099 |
| Корейский | 1042 |
| Латышский | 1062 |
| Литовский | 1063 |
| Malay - Malaysia | 1086 |
| Малайялам | 1100 |
| Маратхи | 1102 |
| Польский | 1045 |
| Португальский | 2070 |
| Панджабский | 1094 |
| Румынский | 1048 |
| Русский | 1049 |
| Serbian (Cyrillic) | 3098 |
| Serbian (Latin) | 2074 |
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

## <a id="filters"></a> Фильтры

Полнотекстовый поиск также работает с текстом, хранящимся в двоичных файлах. Но в этом случае для обработки файла требуется установленный фильтр. Дополнительные сведения о фильтрах см. в статье [Настройка поисковых фильтров и управление ими](../relational-databases/search/configure-and-manage-filters-for-search.md).

Чтобы просмотреть список установленных фильтров, вызовите **sp_help_fulltext_system_components 'filter'**. Для SQL Server установлены указанные далее фильтры.

| Название компонента | Идентификатор класса | Версия |
|---|---|---|
|.a | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.ans | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.asc | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.ascx | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.asm | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.asp | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.aspx | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.asx | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.bas | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.bat | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.bcp | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.c | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.cc | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.cls | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.cmd | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.cpp | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.cs | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.csa | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.css | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.csv | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.cxx | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.dbs | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.def | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.dic | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.dos | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.dsp | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.dsw | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.ext | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.faq | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.fky | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.h | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.hhc | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.hpp | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.hta | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.htm | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.html | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.htt | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.htw | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.htx | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.hxx | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.i | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.ibq | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.ics | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.idl | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.idq | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.inc | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.inf | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.ini | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.inl | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.inx | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.jav | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.java | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.js | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.kci | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.lgn | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.log | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.lst | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.m3u | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.mak | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.mk | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|ODC | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.odh | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.odl | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.pkgdef | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.pkgundef | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.pl | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.prc | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.rc | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.rc2 | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.rct | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.reg | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.rgs | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.rtf | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.rul | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.s | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.scc | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.shtm | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.shtml | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.snippet | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.sol | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.sor | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.srf | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.stm | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.tab | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.tdl | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.tlh | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.tli | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.trg | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.txt | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.udf | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.udt | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.url | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.usr | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.vbs | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.viw | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.vsct | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.vsixlangpack | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.vsixmanifest | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.vspscc | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.vsscc | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.vssscc | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.wri | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.wtx | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|XML | 41B9BE05-B3AF-460C-BF0B-2CDD44A093B1 | 12.0.9735.0 |

## <a name="semantic-search"></a>Семантический поиск
[Семантический поиск](../relational-databases/search/semantic-search-sql-server.md) основан на функции полнотекстового поиска и предназначен для извлечения и индексирования статистически релевантных *ключевых фраз*. Он позволяет запрашивать значение в документах в базе данных. Кроме того, с его помощью можно находить похожие документы.

Чтобы использовать семантический поиск, сначала необходимо восстановить базу данных семантической статистики языка на компьютере.

1. Воспользуйтесь программой [sqlcmd](sql-server-linux-setup-tools.md) и выполните следующую команду Transact-SQL на экземпляре SQL Server Linux. Эта команда восстанавливает базу данных статистики языка.

   ```sql
   RESTORE DATABASE [semanticsdb] FROM
   DISK = N'/opt/mssql/misc/semanticsdb.bak' WITH FILE = 1,
   MOVE N'semanticsdb' TO N'/var/opt/mssql/data/semanticsDB.mdf',
   MOVE N'semanticsdb_log' TO N'/var/opt/mssql/data/semanticsdb_log.ldf', NOUNLOAD, STATS = 5
   GO
   ```

   > [!NOTE]
   > При необходимости обновите пути в предыдущей команде RESTORE, чтобы настроить конфигурацию.

1. Чтобы зарегистрировать базу данных семантической статистики языка, выполните следующую команду Transact-SQL.

    ```sql
    EXEC sp_fulltext_semantic_register_language_statistics_db @dbname = N'semanticsdb';  
    GO
    ```

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о полнотекстовом поиске см. в [этой статье](../relational-databases/search/full-text-search.md). 
