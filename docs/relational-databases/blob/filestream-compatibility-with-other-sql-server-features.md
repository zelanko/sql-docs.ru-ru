---
title: Совместимость FILESTREAM с другими компонентами SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], other SQL Server features and
- FILESTREAM [SQL Server], limitations
ms.assetid: d2c145dc-d49a-4f5b-91e6-89a2b0adb4f3
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 6e2b2f9e434e1e88d893478c558078c8139e1bb0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65094252"
---
# <a name="filestream-compatibility-with-other-sql-server-features"></a>Совместимость FILESTREAM с другими компонентами SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Поскольку данные FILESTREAM находятся в файловой системе, в данном разделе приводятся основные сведения, рекомендации и ограничения по использованию FILESTREAM со следующими компонентами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   [Службы SQL Server Integration Services](#ssis)  
  
-   [Распределенные запросы и связанные серверы](#distqueries)  
  
-   [Шифрование](#encryption)  
  
-   [Моментальные снимки базы данных](#DatabaseSnapshot)  
  
-   [Репликация](#Replication)  
  
-   [Доставка журналов](#LogShipping)  
  
-   [Зеркальное отображение базы данных](#DatabaseMirroring)  
  
-   [Полнотекстовое индексирование](#FullText)  
  
-   [Отказоустойчивая кластеризация](#FailoverClustering)  
  
-   [SQL Server Express](#SQLServerExpress)  
  
-   [Автономные базы данных](#contained)  
  
##  <a name="ssis"></a> Службы SQL Server Integration Services  
 Службы SQL Server Integration Services (SSIS) обрабатывают данные FILESTREAM в потоке данных как любые другие данные большого двоичного объекта с использованием типа данных DT_IMAGE SSIS.  
  
 Загрузку файлов из файловой системы в столбец FILESTREAM можно выполнить с помощью преобразования «Импорт столбца». Преобразование «Экспорт столбца» также можно использовать, чтобы извлечь файлы из столбца FILESTREAM в другую папку файловой системы.  
  
##  <a name="distqueries"></a> Распределенные запросы и связанные серверы  
 Вы можете работать с данными FILESTREAM при помощи распределенных запросов и связанных серверов, рассматривая их как данные **varbinary(max)** . Не допускается применение функции FILESTREAM **PathName()** в распределенных запросах, в которых используется четырехкомпонентное имя, даже если имя относится к локальному серверу. Однако вы можете применять функцию **PathName()** во внутреннем запросе передаваемого запроса, в котором используется **OPENQUERY()** .  
  
##  <a name="encryption"></a> Шифрование  
 Данные FILESTREAM не шифруются, даже если включено прозрачное шифрование данных.  
  
##  <a name="DatabaseSnapshot"></a> Моментальные снимки базы данных  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает [моментальные снимки базы данных](../../relational-databases/databases/database-snapshots-sql-server.md) для файловых групп FILESTREAM. Если файловая группа FILESTREAM включена в предложение CREATE DATABASE ON, выполнение этой инструкции завершится сбоем и приведет к возникновению ошибки.  
  
 При использовании FILESTREAM моментальные снимки базы данных можно создавать для стандартных файловых групп (отличных от FILESTREAM). В таких моментальных снимках баз данных файловые группы FILESTREAM отмечаются как вне сети.  
  
 В инструкции SELECT, выполняемой в отношении таблицы FILESTREAM в моментальном снимке базы данных, не должно содержаться столбцов FILESTREAM; в противном случае будет возвращено следующее сообщение об ошибке:  
  
 `Could not continue scan with NOLOCK due to data movement.`  
  
##  <a name="Replication"></a> Репликация  
 Столбец **varbinary(max)** , атрибут FILESTREAM которого включен на издателе, может быть реплицирован на подписчик с атрибутом FILESTREAM или без него. Чтобы указать способ репликации этого столбца, используйте диалоговое окно **Свойства статьи — \<статья>** либо параметр @schema_option процедуры [sp_addarticle](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) или [sp_addmergearticle](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Данные, реплицированные в столбец типа **varbinary(max)** без атрибута FILESTREAM, не должны превышать установленный в 2 ГБ предел для данного типа данных; в противном случае формируется ошибка выполнения. Рекомендуется выполнять репликацию атрибута FILESTREAM, если данные не реплицируются в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Репликация таблиц со столбцами FILESTREAM на подписчики [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] не поддерживается, независимо установленного параметра схемы.  
  
> [!NOTE]  
>  Репликация больших значений данных с подписчиков [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ограничена максимальным значением 256 МБ значений данных. Дополнительные сведения см. в разделе [Maximum Capacity Specifications](https://go.microsoft.com/fwlink/?LinkId=103810).  
  
### <a name="considerations-for-transactional-replication"></a>Вопросы использования репликации транзакций  
 При использовании столбцов FILESTREAM в таблицах, опубликованных для репликации транзакций, обратите внимание на следующие положения.  
  
-   Если в какой-либо из таблиц содержатся столбцы с атрибутом FILESTREAM, значения *database snapshot* или *database snapshot character* нельзя использовать для свойства @sync_method хранимой процедуры [sp_addpublication](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md).  
  
-   Параметр max text repl size задает максимально допустимый объем данных, добавляемых в опубликованный для репликации столбец. Этот параметр позволяет управлять размером реплицируемых данных FILESTREAM.  
  
-   Если указан параметр схемы для репликации атрибута FILESTREAM, но необходимый для FILESTREAM столбец **uniqueidentifier** был отфильтрован или если для этого столбца не задана репликация ограничения UNIQUE, то репликация атрибута FILESTREAM осуществлена не будет. Столбец будет реплицирован только как столбец типа **varbinary(max)** .  
  
### <a name="considerations-for-merge-replication"></a>Общие вопросы репликации слиянием  
 При использовании столбцов FILESTREAM в таблицах, опубликованных для репликации слиянием, обратите внимание на следующие положения.  
  
-   Как для репликации слиянием, так и для атрибута FILESTREAM необходим столбец типа данных **uniqueidentifier** , позволяющий идентифицировать каждую строку таблицы. Если в таблице такого столбца нет, репликация слиянием автоматически добавляет его. Для репликации слиянием требуется, чтобы было установлено свойство ROWGUIDCOL данного столбца и чтобы значениями по умолчанию для данного столбца являлись NEWID() или NEWSEQUENTIALID(). В дополнение к этим требованиям для атрибута FILESTREAM необходимо задание ограничения UNIQUE для данного столбца. Эти требования приводят к следующим последствиям.  
  
    -   При добавлении столбца FILESTREAM к таблице, уже опубликованной для репликации слиянием, необходимо убедиться, что у столбца **uniqueidentifier** имеется ограничение UNIQUE. Если ограничение UNIQUE отсутствует, добавьте именованное ограничение к таблице в базе данных публикации. По умолчанию репликация слиянием опубликует данное изменение схемы, и оно будет применено к каждой базе данных подписки.  
  
         Если ограничение UNIQUE добавляется вручную согласно описанию и репликацию слиянием требуется удалить, то сначала необходимо удалить ограничение UNIQUE, иначе удаление репликации завершится неуспешно.  
  
    -   По умолчанию в репликации слиянием используется значение NEWSEQUENTIALID(), поскольку, по сравнению с NEWID(), оно обеспечивает лучшую производительность. При добавлении столбца **uniqueidentifier** к таблице, уже опубликованной для репликации слиянием, в качестве значения по умолчанию следует указать NEWSEQUENTIALID().  
  
-   Репликация слиянием включает в себя оптимизацию репликации типов больших объектов. Оптимизация управляется при помощи параметра @stream_blob_columns хранимой процедуры [sp_addmergearticle](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Если параметр схемы настроен на репликацию атрибута FILESTREAM, параметру @stream_blob_columns присваивается значение **true**. Эта оптимизация может быть переопределена с помощью хранимой процедуры [sp_changemergearticle](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Эта хранимая процедура позволяет задать параметру @stream_blob_columns значение **false**. При добавлении столбца FILESTREAM в таблицу, уже опубликованную для репликации слиянием, значение **true** рекомендуется присвоить параметру при помощи хранимой процедуры sp_changemergearticle.  
  
-   Включение параметра схемы для FILESTREAM после создания статьи может привести к сбою репликации, если размер данных столбца FILESTREAM превышает 2 ГБ и если во время репликации возникает конфликт. Если возникновение данной ситуации не исключено, рекомендуется удалить и повторно создать статью таблицы с соответствующим параметром схемы FILESTREAM, включенным во время создания.  
  
-   Репликация слиянием позволяет синхронизировать данные FILESTREAM во время HTTPS-соединения при помощи [веб-синхронизации](../../relational-databases/replication/web-synchronization-for-merge-replication.md). Размер этих данных не должен превышать ограничение в 50 МБ для веб-синхронизации, иначе возникнет ошибка выполнения.  
  
##  <a name="LogShipping"></a> Доставка журналов  
 В[доставке журналов](../../database-engine/log-shipping/about-log-shipping-sql-server.md) предусмотрена поддержка FILESTREAM. Как на сервере-источнике, так и на сервере-получателе должна быть запущена версия [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]или более поздняя версия и должен быть включен параметр FILESTREAM.  
  
##  <a name="DatabaseMirroring"></a> Зеркальное отображение базы данных  
 Зеркальное отображение базы данных не поддерживает FILESTREAM. Создание файловой группы FILESTREAM на основном сервере невозможно. Настройка зеркального отображения для базы данных, содержащей файловые группы FILESTREAM, невозможна.  
  
##  <a name="FullText"></a> Полнотекстовое индексирование  
 [Полнотекстовое индексирование](../../relational-databases/search/populate-full-text-indexes.md) обрабатывает столбцы FILESTREAM так же, как и столбцы типа **varbinary(max)** . В таблице FILESTREAM должен присутствовать столбец, в котором содержится расширение имени файла для каждого блока больших двоичных объектов (BLOB) FILESTREAM. Дополнительные сведения см. в статьях [Запрос с полнотекстовым поиском](../../relational-databases/search/query-with-full-text-search.md), [Настройка и управление фильтрами для поиска](../../relational-databases/search/configure-and-manage-filters-for-search.md) и [sys.fulltext_document_types (Transact-SQL)](../../relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql.md).  
  
 Полнотекстовый поиск индексирует содержимое блоков больших двоичных объектов (BLOB) FILESTREAM. Индексирование таких файлов, как изображения, может оказаться нецелесообразным. При обновлении блоков больших двоичных объектов (BLOB) FILESTREAM выполняется их повторное индексирование.  
  
##  <a name="FailoverClustering"></a> Отказоустойчивая кластеризация  
 В целях отказоустойчивой кластеризации файловые группы FILESTREAM могут быть помещены на общий диск. Параметр FILESTREAM должен быть включен на каждом узле кластера, на котором будет размещен экземпляр FILESTREAM. Дополнительные сведения см. в статье [Установка FILESTREAM в отказоустойчивом кластере](../../relational-databases/blob/set-up-filestream-on-a-failover-cluster.md).  
  
##  <a name="SQLServerExpress"></a> SQL Server Express  
 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] предусмотрена поддержка FILESTREAM. Ограничение размера базы данных в 10 ГБ не включает контейнер данных FILESTREAM.  
  
##  <a name="contained"></a> Автономные базы данных  
 Для использования функции FILESTREAM требуется выполнение определенной настройки вне базы данных. Поэтому база данных, использующая FILESTREAM или FileTable, не является полностью автономной.  
  
 Для автономности базы данных можно установить значение PARTIAL при необходимости использовать некоторые функции автономных баз данных, например такие, как функция автономных пользователей. В этом случае следует иметь в виду, что некоторые параметры базы данных не хранятся в самой базе данных и не перемещаются автоматически при перемещении базы данных.  
  
## <a name="see-also"></a>См. также:  
 [Данные большого двоичного объекта (SQL Server)](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md)  
  
  
