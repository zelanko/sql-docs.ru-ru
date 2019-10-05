---
title: Заметки о выпуске
titleSuffix: SQL Server big data clusters
description: В этой статье описаны последние обновления и известные проблемы для [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] (Предварительная версия).
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 758e87a0c74df695c06cb0f0005f6a19d8978625
ms.sourcegitcommit: f6bfe4a0647ce7efebaca11d95412d6a9a92cd98
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/05/2019
ms.locfileid: "71974386"
---
# <a name="release-notes-for-sql-server-big-data-clusters"></a>Заметки о выпуске для SQL Server кластеров больших данных

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье перечислены обновления и известные проблемы для последних выпусков [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)].

## <a id="rc"></a>Версия-кандидат (август)

В следующих разделах описаны новые функции и известные проблемы для кластеров больших данных в SQL Server 2019 версии-кандидата.

### <a name="whats-new"></a>What's New

|Новые функции или обновления | Сведения |
|:---|:---|
|Группа доступности Always On SQL Server |При развертывании SQL Server кластера больших данных можно настроить развертывание, чтобы создать группу доступности для предоставления следующих данных.<br/><br/>— Высокий уровень доступности <br/><br/>— Чтение и масштабирование <br/><br/>— Вставка данных с горизонтальным масштабированием в пул данных<br/><br>См. раздел [развертывание с высоким уровнем доступности](../big-data-cluster/deployment-high-availability.md). |
|`azdata` |Упрощенная установка средства с помощью [диспетчера установки](./deploy-install-azdata-linux-package.md)<br/><br/>[`azdata notebook` команда](./reference-azdata-notebook.md)<br/><br/>[`azdata bdc status` команда](./reference-azdata-bdc-status.md) |
|Azure Data Studio|[Скачайте сборку версии-кандидата Azure Data Studio](deploy-big-data-tools.md#download-and-install-azure-data-studio-sql-server-2019-release-candidate-rc).<br/><br/>Добавлены сведения об устранении неполадок в записных книжках по SQL Server 2019 Jupyter.<br/><br/>Добавлен интерфейс входа контроллера.<br/><br/>Добавлена панель мониторинга контроллера для просмотра конечных точек служб, просмотра состояния работоспособности кластера и записных книжек по устранению неполадок доступа.<br/><br/>Улучшена производительность вывода и редактирования ячеек записной книжки.|
| &nbsp; | &nbsp; |

### <a name="known-issues"></a>Известные проблемы

* SQL Server 2019. кластеры больших данных имеют номер сборки версии-кандидата @no__t — 0.

* Профиль развертывания "кубеадм-производственных" не поддерживается в версии-кандидате кластера больших данных SQL Server 2019 с указанным выше номером сборки. Вместо этого используйте профиль "кубеадм-dev-test" для развертываний Кубеадм.

## <a id="ctp32"></a> CTP 3.2 (июль)

В следующих разделах описаны новые функции и известные проблемы для кластеров больших данных в SQL Server 2019 CTP 3.2.

### <a name="whats-new"></a>What's New

|Новые функции или обновления | Сведения |
|:---|:---|
|Общедоступная предварительная версия |До CTP-версии 3.2 кластер больших данных SQL Server был доступен для зарегистрированных ранних последователей. Этот выпуск позволяет любому пользователю работать с кластерами больших данных SQL Server. <br/><br/> См. статью Начало [работы с [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]](deploy-get-started.md).|
|`azdata` |В CTP 3.2 представлена `azdata` — служебная программа командной строки на языке Python, которая позволяет администраторам кластера провести начальную загрузку и управлять кластером больших данных с помощью интерфейсов API. `azdata` заменяет собой `mssqlctl`. См. раздел [Установка `azdata`](deploy-install-azdata.md). |
|PolyBase |Имена столбцов внешней таблицы теперь используются для запроса источников данных SQL Server, Oracle, Teradata, MongoDB и ODBC. В предыдущих выпусках CTP столбцы во внешнем источнике данных были привязаны только по порядковому номеру, а имена, указанные во определении внешней таблицы EXTERNAL TABLE, не использовались. |
|Обновление распределения по уровням HDFS |Представлена функция обновления для распределения по уровням HDFS, чтобы можно было обновить существующее подключение на основе последнего моментального снимка удаленных данных. См. раздел [Распределение по уровням HDFS](hdfs-tiering.md). |
|Устранение неполадок на основе записных книжек |В CTP 3.2 введены записные книжки Jupyter для помощи в [развертывании](deploy-notebooks.md) и [обнаружении, диагностике и устранении неполадок](manage-notebooks.md) для компонентов кластера больших данных SQL Server. |
| &nbsp; | &nbsp; |

### <a name="known-issues"></a>Известные проблемы

В следующих разделах перечислены известные проблемы и ограничения для этого выпуска.

#### <a name="polybase"></a>PolyBase

- В этом выпуске не поддерживается принудительная передача предложения TOP, когда счетчик > 1000. В таких случаях все строки будут считываться из удаленного источника данных. (Исправлено в версии-кандидате)

- В этом выпуске не поддерживается принудительная передача совместно размещенных соединений во внешние источники данных. Например, принудительная отправка двух таблиц пула данных с типом распределения ROUND_ROBIN приведет к передаче данных главному экземпляру SQL или экземпляру вычислительного пула для выполнения операции соединения.

#### <a name="compute-pool"></a>Вычислительный пул

- Развертывание кластера больших данных поддерживает только вычислительный пул с одним экземпляром. (Исправлено в версии-кандидате)

#### <a name="storage-pool"></a>Пул носителей

- Запрос файлов Parquet в пуле носителей не поддерживает определенные типы данных.

- К родительским столбцам MAP и LIST и родительским столбцам без присоединенного типа невозможно отправлять запросы. При этом происходит ошибка.

- К повторяющимся узлам невозможно отправлять запросы, это может давать неверные результаты.

## <a id="ctp31"></a> CTP 3.1 (июнь)

В следующих разделах описаны новые функции и известные проблемы для кластеров больших данных в SQL Server 2019 CTP 3.1.

### <a name="whats-new"></a>What's New

| Новые функции или обновления | Сведения |
|:---|:---|
| Команда `mssqlctl` изменена. | Команды `mssqlctl cluster` переименованы в `mssqlctl bdc`. См. подробнее в [справочнике по `mssqlctl`](reference-azdata.md). |
| Новые команды состояния `mssqlctl` и удаление портала администрирования кластера. | Портал администрирования кластера будет удален в этом выпуске. В `mssqlctl` добавлены новые команды состояния, дополняющие существующие команды мониторинга. |
| Пул вычислительных ресурсов Spark | Вы можете создавать дополнительные узлы для увеличения вычислительной мощности Spark без необходимости масштабировать хранилище. Кроме того, вы можете запускать узлы пула хранилища, которые не используются для Spark. Spark и хранилище используются раздельно. См. подробнее о [настройке хранилища без Spark](deployment-custom-configuration.md#sparkstorage). |
| Соединитель MSSQL Spark | Поддержка операций чтения и записи для внешних таблиц пула данных. В предыдущих выпусках эти операции поддерживались только для таблиц главного экземпляра. См. подробнее об [операциях чтения и записи для SQL Server из Spark с помощью соединителя Spark MSSQL](spark-mssql-connector.md). |
| Использование Машинного обучения с MLeap | [Вы можете обучать модель машинного обучения MLeap в Spark и оценивать ее в SQL Server с помощью расширения языка Java](spark-create-machine-learning-model.md). |

### <a name="known-issues"></a>Известные проблемы

В следующих разделах перечислены известные проблемы и ограничения для этого выпуска.

#### <a name="hdfs"></a>HDFS

- Если щелкнуть правой кнопкой мыши файл в HDFS для его предварительного просмотра, может появиться следующая ошибка.

   `Error previewing file: File exceeds max size of 30MB`

   Сейчас не существует способа предварительного просмотра файлов больше 30 МБ в Azure Data Studio.

- Изменения конфигурации в HDFS, затрагивающие изменения в hdfs-site.xml, не поддерживаются.

#### <a name="deployment"></a>Развертывание

- Обновление кластера больших данных с предыдущего выпуска не поддерживается.

   > [!IMPORTANT]
   > Перед развертыванием последнего выпуска нужно создать резервную копию данных, а затем удалить существующий кластер больших данных (с помощью предыдущей версии **azdata**). Дополнительные сведения см. в статье [Обновление до нового выпуска](deployment-upgrade.md).

- После развертывания в AKS могут отобразиться следующие два события предупреждения из развертывания. Оба эти события являются известными проблемами, но они не препятствуют успешному развертыванию кластера больших данных в AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- При сбое развертывания кластера больших данных связанное пространство имен не удаляется. Это может привести к тому, что в кластере появится потерянное пространство имен. Обходной путь состоит в том, чтобы удалить пространство имен вручную перед развертыванием кластера с тем же именем.

#### <a name="external-tables"></a>Внешние таблицы

- Развертывание кластера больших данных больше не создает внешние источники данных **SqlDataPool** и **SqlStoragePool**. Эти источники данных можно создать вручную для поддержки виртуализации данных в пулах данных и носителей.

   > [!NOTE]
   > Универсальный код ресурса (URI) для создания этих внешних источников данных отличается между выпусками CTP. Чтобы узнать, как создать их, см. приведенные ниже команды Transact-SQL. 

   ```sql
   -- Create default data sources for SQL Big Data Cluster
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
       CREATE EXTERNAL DATA SOURCE SqlDataPool
       WITH (LOCATION = 'sqldatapool://controller-svc/default');
 
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
       CREATE EXTERNAL DATA SOURCE SqlStoragePool
       WITH (LOCATION = 'sqlhdfs://controller-svc/default');
   ```

- Можно создать внешнюю таблицу пула данных для таблицы с неподдерживаемыми типами столбцов. При выполнении запроса к внешней таблице вы получите сообщение, аналогичное следующему.

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- При запросе внешней таблицы пула носителей может возникнуть ошибка, если одновременно с этим выполняется копирование базового файла в HDFS.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- При создании внешней таблицы для Oracle, которая использует символьные типы данных, мастер виртуализации Azure Data Studio интерпретирует эти столбцы как VARCHAR в определении внешней таблицы. Это приведет к сбою в DDL внешней таблице. Либо измените схему Oracle для использования типа NVARCHAR2, либо вручную создайте инструкции EXTERNAL TABLE и укажите NVARCHAR вместо использования мастера.

#### <a name="application-deployment"></a>Развертывание приложения

- При вызове приложения R, Python или MLeap из API на основе REST время ожидания вызова истекает через 5 минут.

#### <a name="spark-and-notebooks"></a>Spark и записные книжки

- IP-адреса объектов pod могут измениться в среде Kubernetes при перезапуске объектов pod. В сценарии, где master-pod перезагружается, сеанс Spark может завершиться с ошибкой `NoRoteToHostException`. Это вызвано тем, что кэши JVM не обновляются с использованием новых IP-адресов.

- Если вы уже установили Jupyter и используете отдельную установку Python в Windows, то записные книжки Spark могут завершиться ошибкой. Чтобы обойти эту ошибку, обновите Jupyter до последней версии.

- Если в записной книжке щелкнуть команду **Добавить текст**, текстовая ячейка добавляется в режиме предварительного просмотра, а не в режиме редактирования. Вы можете щелкнуть значок предварительного просмотра, чтобы переключиться в режим редактирования и изменить ячейку.

#### <a name="security"></a>безопасность

- SA_PASSWORD является частью среды и обнаруживается (например, в файле дампа cord). После развертывания нужно сбросить SA_PASSWORD в главном экземпляре. Это не ошибка, а мера безопасности. Дополнительные сведения об изменении SA_PASSWORD в контейнере Linux см. в разделе [Смена пароля администратора](../linux/quickstart-install-connect-docker.md#sapassword).

- Журналы AKS могут содержать пароль системного администратора (SA) для развертываний кластера больших данных.

#### <a name="kibana-logs-dashboards"></a>Панели мониторинга журналов Kibana

- Между CTP 3,0 и 3,1 версия Kibana обновлена с 6.3.1 до 7.0.1.  Это сделал браузер Microsoft ребр несовместимым с Kibana. При загрузке текущей версии панелей мониторинга Kibana в Microsoft ребра пользователи увидят пустую страницу. Поддерживаемые браузеры для Kibana см. [здесь]( https://www.elastic.co/support/matrix#matrix_browse) .


## <a id="ctp30"></a> CTP 3.0 (май)

В следующих разделах описаны новые функции и известные проблемы для кластеров больших данных в SQL Server 2019 CTP 3.0.

### <a name="whats-new"></a>What's New

| Новые функции или обновления | Сведения |
|:---|:---|
| Обновления **mssqlctl** | Несколько [обновлений команд и параметров](reference-azdata.md) **mssqlctl**. Сюда входит обновление команды **mssqlctl login**, которая теперь использует имя пользователя и конечную точку контроллера. |
| Усовершенствования хранилища | Поддержка разных конфигураций хранилища для журналов и данных. Кроме того, было уменьшено количество утверждений постоянного тома для больших кластеров данных. |
| Несколько экземпляров вычислительного пула | Поддержка нескольких экземпляров вычислительного пула. |
| Новые возможности и поведение пулов | Теперь вычислительный пул используется по умолчанию для операций с пулом носителей и пулом данных только при распределении **ROUND_ROBIN**. Пул данных теперь может использовать новый тип распределения **REPLICATED**, то есть одни и те же данные присутствуют во всех экземплярах пула данных. |
| Усовершенствования внешних таблиц | Внешние таблицы, имеющие тип источника данных HADOOP, теперь поддерживают чтение строк размером до 1 МБ. Внешние таблицы (ODBC, пул носителей, пул данных) теперь поддерживают строки шириной с таблицу SQL Server. |

### <a name="known-issues"></a>Известные проблемы

В следующих разделах перечислены известные проблемы и ограничения для этого выпуска.

#### <a name="hdfs"></a>HDFS

- Azure Data Studio возвращает ошибку при попытке создать папку в HDFS. Чтобы включить эту функцию, установите сборку предварительной оценки Azure Data Studio.
  
   - [Пользовательский установщик Windows — **сборка предварительной оценки**](https://azuredatastudio-update.azurewebsites.net/latest/win32-x64-user/insider)
   - [Системный установщик Windows — **сборка предварительной оценки**](https://azuredatastudio-update.azurewebsites.net/latest/win32-x64/insider)
   - [Файл ZIP для Windows — **сборка предварительной оценки**](https://azuredatastudio-update.azurewebsites.net/latest/win32-x64-archive/insider)
   - [Файл ZIP для macOS — **сборка предварительной оценки**](https://azuredatastudio-update.azurewebsites.net/latest/darwin/insider)
   - [Файл TAR.GZ для Windows — **сборка предварительной оценки**](https://azuredatastudio-update.azurewebsites.net/latest/linux-x64/insider)

- Если щелкнуть правой кнопкой мыши файл в HDFS для его предварительного просмотра, может появиться следующая ошибка.

   `Error previewing file: File exceeds max size of 30MB`

   Сейчас не существует способа предварительного просмотра файлов больше 30 МБ в Azure Data Studio.

- Изменения конфигурации в HDFS, затрагивающие изменения в hdfs-site.xml, не поддерживаются.

#### <a name="deployment"></a>Развертывание

- Предыдущие процедуры развертывания для кластеров больших данных с поддержкой GPU не поддерживаются в CTP 3.0. Выполняется анализ альтернативной процедуры развертывания. Сейчас публикация статьи "Развертывание кластера больших данных с поддержкой GPU и запуск TensorFlow" была временно отменена, чтобы избежать путаницы.

- Обновление кластера больших данных с предыдущего выпуска не поддерживается.

   > [!IMPORTANT]
   > Перед развертыванием последнего выпуска нужно создать резервную копию данных, а затем удалить существующий кластер больших данных (с помощью предыдущей версии **azdata**). Дополнительные сведения см. в статье [Обновление до нового выпуска](deployment-upgrade.md).

- После развертывания в AKS могут отобразиться следующие два события предупреждения из развертывания. Оба эти события являются известными проблемами, но они не препятствуют успешному развертыванию кластера больших данных в AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- При сбое развертывания кластера больших данных связанное пространство имен не удаляется. Это может привести к тому, что в кластере появится потерянное пространство имен. Обходной путь состоит в том, чтобы удалить пространство имен вручную перед развертыванием кластера с тем же именем.

#### <a name="external-tables"></a>Внешние таблицы

- Развертывание кластера больших данных больше не создает внешние источники данных **SqlDataPool** и **SqlStoragePool**. Эти источники данных можно создать вручную для поддержки виртуализации данных в пулах данных и носителей.

   > [!NOTE]
   > Универсальный код ресурса (URI) для создания этих внешних источников данных отличается между выпусками CTP. Чтобы узнать, как создать их, см. приведенные ниже команды Transact-SQL. 

   ```sql
   -- Create default data sources for SQL Big Data Cluster
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
       CREATE EXTERNAL DATA SOURCE SqlDataPool
       WITH (LOCATION = 'sqldatapool://controller-svc/default');
 
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
       CREATE EXTERNAL DATA SOURCE SqlStoragePool
       WITH (LOCATION = 'sqlhdfs://controller-svc/default');
   ```

- Можно создать внешнюю таблицу пула данных для таблицы с неподдерживаемыми типами столбцов. При выполнении запроса к внешней таблице вы получите сообщение, аналогичное следующему.

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- При запросе внешней таблицы пула носителей может возникнуть ошибка, если одновременно с этим выполняется копирование базового файла в HDFS.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- При создании внешней таблицы для Oracle, которая использует символьные типы данных, мастер виртуализации Azure Data Studio интерпретирует эти столбцы как VARCHAR в определении внешней таблицы. Это приведет к сбою в DDL внешней таблице. Либо измените схему Oracle для использования типа NVARCHAR2, либо вручную создайте инструкции EXTERNAL TABLE и укажите NVARCHAR вместо использования мастера.

#### <a name="application-deployment"></a>Развертывание приложения

- При вызове приложения R, Python или MLeap из API на основе REST время ожидания вызова истекает через 5 минут.

#### <a name="spark-and-notebooks"></a>Spark и записные книжки

- IP-адреса объектов pod могут измениться в среде Kubernetes при перезапуске объектов pod. В сценарии, где master-pod перезагружается, сеанс Spark может завершиться с ошибкой `NoRoteToHostException`. Это вызвано тем, что кэши JVM не обновляются с использованием новых IP-адресов.

- Если вы уже установили Jupyter и используете отдельную установку Python в Windows, то записные книжки Spark могут завершиться ошибкой. Чтобы обойти эту ошибку, обновите Jupyter до последней версии.

- Если в записной книжке щелкнуть команду **Добавить текст**, текстовая ячейка добавляется в режиме предварительного просмотра, а не в режиме редактирования. Вы можете щелкнуть значок предварительного просмотра, чтобы переключиться в режим редактирования и изменить ячейку.

#### <a name="security"></a>безопасность

- SA_PASSWORD является частью среды и обнаруживается (например, в файле дампа cord). После развертывания нужно сбросить SA_PASSWORD в главном экземпляре. Это не ошибка, а мера безопасности. Дополнительные сведения об изменении SA_PASSWORD в контейнере Linux см. в разделе [Смена пароля администратора](../linux/quickstart-install-connect-docker.md#sapassword).

- Журналы AKS могут содержать пароль системного администратора (SA) для развертываний кластера больших данных.

## <a id="ctp25"></a> CTP 2.5 (апрель)

В следующих разделах описаны новые функции и известные проблемы для кластеров больших данных в SQL Server 2019 CTP 2.5.

### <a name="whats-new"></a>What's New

| Новые функции или обновления | Сведения |
|:---|:---|
| Профили развертывания | Используйте стандартные и настраиваемые [JSON-файлы конфигурации развертывания](deployment-guidance.md#configfile) для развертывания кластера больших данных вместо переменных среды. |
| Развертывания с подсказками | `azdata cluster create` теперь запрашивает все необходимые параметры для развертывания по умолчанию. |
| Изменение имен конечной точки службы и pod | Изменились имена следующих внешних конечных точек.<br/>&nbsp;&nbsp;&nbsp;- **endpoint-master-pool** => **master-svc-external**<br/>&nbsp;&nbsp;&nbsp;- **endpoint-controller** => **controller-svc-external**<br/>&nbsp;&nbsp;&nbsp;- **endpoint-service-proxy** => **mgmtproxy-svc-external**<br/>&nbsp;&nbsp;&nbsp;- **endpoint-security** => **gateway-svc-external**<br/>&nbsp;&nbsp;&nbsp;- **endpoint-app-service-proxy** => **appproxy-svc-external**|
| Усовершенствования **azdata** | Используйте **azdata** для [перечисления внешних конечных точек](deployment-guidance.md#endpoints) и проверяйте версию **azdata** с помощью параметра `--version`. |
| Автономная установка | Руководство по развертываниям автономного кластера больших данных. |
| Усовершенствования распределения по уровням HDFS | Распределения по уровням S3, кэширование подключения и поддержка OAuth для ADLS 2-го поколения. |
| Новый соединитель Spark и SQL Server `mssql` | |

### <a name="known-issues"></a>Известные проблемы

В следующих разделах перечислены известные проблемы и ограничения для этого выпуска.

#### <a name="deployment"></a>Развертывание

- Обновление кластера больших данных с предыдущего выпуска не поддерживается.

   > [!IMPORTANT]
   > Перед развертыванием последнего выпуска нужно создать резервную копию данных, а затем удалить существующий кластер больших данных (с помощью предыдущей версии **azdata**). Дополнительные сведения см. в статье [Обновление до нового выпуска](deployment-upgrade.md).

- После развертывания в AKS могут отобразиться следующие два события предупреждения из развертывания. Оба эти события являются известными проблемами, но они не препятствуют успешному развертыванию кластера больших данных в AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- При сбое развертывания кластера больших данных связанное пространство имен не удаляется. Это может привести к тому, что в кластере появится потерянное пространство имен. Обходной путь состоит в том, чтобы удалить пространство имен вручную перед развертыванием кластера с тем же именем.

#### <a name="external-tables"></a>Внешние таблицы

- Развертывание кластера больших данных больше не создает внешние источники данных **SqlDataPool** и **SqlStoragePool**. Эти источники данных можно создать вручную для поддержки виртуализации данных в пулах данных и носителей.

   ```sql
   -- Create default data sources for SQL Big Data Cluster
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
       CREATE EXTERNAL DATA SOURCE SqlDataPool
       WITH (LOCATION = 'sqldatapool://service-mssql-controller:8080/datapools/default');
 
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
       CREATE EXTERNAL DATA SOURCE SqlStoragePool
       WITH (LOCATION = 'sqlhdfs://nmnode-0-svc:50070');
   ```

- Можно создать внешнюю таблицу пула данных для таблицы с неподдерживаемыми типами столбцов. При выполнении запроса к внешней таблице вы получите сообщение, аналогичное следующему.

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- При запросе внешней таблицы пула носителей может возникнуть ошибка, если одновременно с этим выполняется копирование базового файла в HDFS.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- При создании внешней таблицы для Oracle, которая использует символьные типы данных, мастер виртуализации Azure Data Studio интерпретирует эти столбцы как VARCHAR в определении внешней таблицы. Это приведет к сбою в DDL внешней таблице. Либо измените схему Oracle для использования типа NVARCHAR2, либо вручную создайте инструкции EXTERNAL TABLE и укажите NVARCHAR вместо использования мастера.

#### <a name="application-deployment"></a>Развертывание приложения

- При вызове приложения R, Python или MLeap из API на основе REST время ожидания вызова истекает через 5 минут.

#### <a name="spark-and-notebooks"></a>Spark и записные книжки

- IP-адреса объектов pod могут измениться в среде Kubernetes при перезапуске объектов pod. В сценарии, где master-pod перезагружается, сеанс Spark может завершиться с ошибкой `NoRoteToHostException`. Это вызвано тем, что кэши JVM не обновляются с использованием новых IP-адресов.

- Если вы уже установили Jupyter и используете отдельную установку Python в Windows, то записные книжки Spark могут завершиться ошибкой. Чтобы обойти эту ошибку, обновите Jupyter до последней версии.

- Если в записной книжке щелкнуть команду **Добавить текст**, текстовая ячейка добавляется в режиме предварительного просмотра, а не в режиме редактирования. Вы можете щелкнуть значок предварительного просмотра, чтобы переключиться в режим редактирования и изменить ячейку.

#### <a name="hdfs"></a>HDFS

- Если щелкнуть правой кнопкой мыши файл в HDFS для его предварительного просмотра, может появиться следующая ошибка.

   `Error previewing file: File exceeds max size of 30MB`

   Сейчас не существует способа предварительного просмотра файлов больше 30 МБ в Azure Data Studio.

- Изменения конфигурации в HDFS, затрагивающие изменения в hdfs-site.xml, не поддерживаются.

#### <a name="security"></a>безопасность

- SA_PASSWORD является частью среды и обнаруживается (например, в файле дампа cord). После развертывания нужно сбросить SA_PASSWORD в главном экземпляре. Это не ошибка, а мера безопасности. Дополнительные сведения об изменении SA_PASSWORD в контейнере Linux см. в разделе [Смена пароля администратора](../linux/quickstart-install-connect-docker.md#sapassword).

- Журналы AKS могут содержать пароль системного администратора (SA) для развертываний кластера больших данных.

## <a id="ctp24"></a> CTP 2.4 (март)

В следующих разделах описаны новые функции и известные проблемы для кластеров больших данных в SQL Server 2019 CTP 2.4.

### <a name="whats-new"></a>What's New

| Новые функции или обновления | Сведения |
|:---|:---|
| Руководство по использованию GPU для выполнения глубокого обучения с помощью библиотеки TensorFlow в Spark. | [Развертывание кластера больших данных с поддержкой GPU и запуск TensorFlow](spark-gpu-tensorflow.md). |
| Источники данных **SqlDataPool** и **SqlStoragePool** больше не создаются по умолчанию. | Создайте их вручную при необходимости. Ознакомьтесь с [известными проблемами](#externaltablesctp24). |
| Поддержка `INSERT INTO SELECT` для пула данных. | Пример см. в разделе [Учебник. Прием данных в пул данных SQL Server с помощью Transact-SQL](tutorial-data-pool-ingest-sql.md). |
| Параметры `FORCE SCALEOUTEXECUTION` и `DISABLE SCALEOUTEXECUTION`. | Принудительно использует вычислительный пул для запросов к внешним таблицам или отключает его. Например, `SELECT TOP(100) * FROM web_clickstreams_hdfs_book_clicks OPTION(FORCE SCALEOUTEXECUTION)`. |
| Обновленные рекомендации по развертыванию AKS. | При анализе кластеров больших данных в AKS теперь рекомендуется использовать один узел размера **Standard_L8s**. |
| Обновление среды выполнения Spark до версии Spark 2.4. | |

### <a name="known-issues"></a>Известные проблемы

В следующих разделах перечислены известные проблемы и ограничения для этого выпуска.

#### <a name="deployment"></a>Развертывание

- Обновление кластера больших данных с предыдущего выпуска не поддерживается.

   > [!IMPORTANT]
   > Перед развертыванием последнего выпуска нужно создать резервную копию данных, а затем удалить существующий кластер больших данных (с помощью предыдущей версии **azdata**). Дополнительные сведения см. в статье [Обновление до нового выпуска](deployment-upgrade.md).

- После развертывания в AKS могут отобразиться следующие два события предупреждения из развертывания. Оба эти события являются известными проблемами, но они не препятствуют успешному развертыванию кластера больших данных в AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- При сбое развертывания кластера больших данных связанное пространство имен не удаляется. Это может привести к тому, что в кластере появится потерянное пространство имен. Обходной путь состоит в том, чтобы удалить пространство имен вручную перед развертыванием кластера с тем же именем.

#### <a name="kubeadm-deployments"></a>Развертывания kubeadm

Если для развертывания Kubernetes на нескольких компьютерах используется kubeadm, портал администрирования кластера неправильно отображает конечные точки, необходимые для подключения к кластеру больших данных. Если у вас возникла эта проблема, выполните следующие действия, чтобы обнаружить IP-адреса конечных точек службы.

- При подключении из кластера запросите в Kubernetes IP-адрес службы для конечной точки, к которой вы хотите подключиться. Например, следующая команда **kubectl** отображает IP-адрес главного экземпляра SQL Server.

   ```bash
   kubectl get service endpoint-master-pool -n <clusterName> -o=custom-columns="IP:.spec.clusterIP,PORT:.spec.ports[*].nodePort"
   ```

- Если вы подключаетесь извне кластера, выполните следующие действия для подключения.

   1. Получите IP-адрес узла, где выполняется главный экземпляр SQL Server: `kubectl get pod mssql-master-pool-0 -o jsonpath="Name: {.metadata.name} Status: {.status.hostIP}" -n <clusterName>`.

   1. Подключитесь к главному экземпляру SQL Server с помощью этого IP-адреса.

   1. Запросите **cluster_endpoint_table** в базе данных master для других внешних конечных точек.

      Если это не удается сделать из-за истечения времени ожидания подключения, возможно, что соответствующий узел защищен брандмауэром. В этом случае нужно обратиться к администратору кластера Kubernetes и запросить IP-адрес узла, который доступен извне. Это может быть любой узел. Затем можно использовать этот IP-адрес и соответствующий порт для подключения к различным службам, запущенным в кластере. Например, администратор может определить этот IP-адрес, выполнив следующую команду.

      ```
      [root@m12hn01 config]# kubectl cluster-info
      Kubernetes master is running at https://172.50.253.99:6443
      KubeDNS is running at https://172.30.243.91:6443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy
      ```

#### <a name="delete-cluster-fails"></a>Сбой при удалении кластера

При попытке удалить кластер с помощью **azdata** возникает следующая ошибка.

```
2019-03-26 20:38:11.0614 UTC | INFO | Deleting cluster ...
Error processing command: "TypeError"
delete_namespaced_service() takes 3 positional arguments but 4 were given
Makefile:61: recipe for target 'delete-cluster' failed
make[2]: *** [delete-cluster] Error 1
Makefile:223: recipe for target 'deploy-clean' failed
make[1]: *** [deploy-clean] Error 2
Makefile:203: recipe for target 'deploy-clean' failed
make: *** [deploy-clean] Error 2
```

Новый клиент Kubernetes Python(версия 9.0.0) изменил API удаленных пространств имен, что приводит к нарушению работы **azdata**. Это происходит, только если установлен более новый клиент Kubernetes Python. Эту проблему можно обойти, напрямую удалив кластер с помощью **kubectl** (`kubectl delete ns <ClusterName>`), либо можно установить более старую версию с помощью `sudo pip install kubernetes==8.0.1`.

#### <a id="externaltablesctp24"></a> Внешние таблицы

- Развертывание кластера больших данных больше не создает внешние источники данных **SqlDataPool** и **SqlStoragePool**. Эти источники данных можно создать вручную для поддержки виртуализации данных в пулах данных и носителей.

   ```sql
   -- Create default data sources for SQL Big Data Cluster
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
       CREATE EXTERNAL DATA SOURCE SqlDataPool
       WITH (LOCATION = 'sqldatapool://service-mssql-controller:8080/datapools/default');
 
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
       CREATE EXTERNAL DATA SOURCE SqlStoragePool
       WITH (LOCATION = 'sqlhdfs://service-master-pool:50070');
   ```

- Можно создать внешнюю таблицу пула данных для таблицы с неподдерживаемыми типами столбцов. При выполнении запроса к внешней таблице вы получите сообщение, аналогичное следующему.

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- При запросе внешней таблицы пула носителей может возникнуть ошибка, если одновременно с этим выполняется копирование базового файла в HDFS.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- При создании внешней таблицы для Oracle, которая использует символьные типы данных, мастер виртуализации Azure Data Studio интерпретирует эти столбцы как VARCHAR в определении внешней таблицы. Это приведет к сбою в DDL внешней таблице. Либо измените схему Oracle для использования типа NVARCHAR2, либо вручную создайте инструкции EXTERNAL TABLE и укажите NVARCHAR вместо использования мастера.

#### <a name="application-deployment"></a>Развертывание приложения

- При вызове приложения R, Python или MLeap из API на основе REST время ожидания вызова истекает через 5 минут.

#### <a name="spark-and-notebooks"></a>Spark и записные книжки

- IP-адреса объектов pod могут измениться в среде Kubernetes при перезапуске объектов pod. В сценарии, где master-pod перезагружается, сеанс Spark может завершиться с ошибкой `NoRoteToHostException`. Это вызвано тем, что кэши JVM не обновляются с использованием новых IP-адресов.

- Если вы уже установили Jupyter и используете отдельную установку Python в Windows, то записные книжки Spark могут завершиться ошибкой. Чтобы обойти эту ошибку, обновите Jupyter до последней версии.

- Если в записной книжке щелкнуть команду **Добавить текст**, текстовая ячейка добавляется в режиме предварительного просмотра, а не в режиме редактирования. Вы можете щелкнуть значок предварительного просмотра, чтобы переключиться в режим редактирования и изменить ячейку.

#### <a name="hdfs"></a>HDFS

- Если щелкнуть правой кнопкой мыши файл в HDFS для его предварительного просмотра, может появиться следующая ошибка.

   `Error previewing file: File exceeds max size of 30MB`

   Сейчас не существует способа предварительного просмотра файлов больше 30 МБ в Azure Data Studio.

- Изменения конфигурации в HDFS, затрагивающие изменения в hdfs-site.xml, не поддерживаются.

#### <a name="security"></a>безопасность

- SA_PASSWORD является частью среды и обнаруживается (например, в файле дампа cord). После развертывания нужно сбросить SA_PASSWORD в главном экземпляре. Это не ошибка, а мера безопасности. Дополнительные сведения об изменении SA_PASSWORD в контейнере Linux см. в разделе [Смена пароля администратора](../linux/quickstart-install-connect-docker.md#sapassword).

- Журналы AKS могут содержать пароль системного администратора (SA) для развертываний кластера больших данных.

## <a id="ctp23"></a> CTP 2.3 (февраль)

В следующих разделах описаны новые функции и известные проблемы для кластеров больших данных в SQL Server 2019 CTP 2.3.

### <a name="whats-new"></a>What's New

| Новые функции или обновления | Сведения |
| :---------- | :------ |
| Отправка заданий Spark в кластерах больших данных в IntelliJ. | [Отправка заданий Spark на [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] в IntelliJ](spark-submit-job-intellij-tool-plugin.md) |
| Общий интерфейс командной строки для развертывания приложений и управления кластерами. | [Развертывание приложения на [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]](big-data-cluster-create-apps.md) |
| Расширение VS Code для развертывания приложений в кластере больших данных. | [Использование VS Code для развертывания приложений в [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]](app-deployment-extension.md) |
| Изменения в использовании команд средства **azdata**. | Дополнительные сведения см. в разделе [Известные проблемы azdata](#azdatactp23). |
| Использование Sparklyr в кластере больших данных | [Использование Sparklyr в кластерах больших данных SQL Server 2019](sparklyr-from-RStudio.md) |
| Подключение внешнего HDFS-совместимого хранилища к кластеру больших данных с **распределением HDFS по уровням**. | См. раздел [Распределение по уровням HDFS](hdfs-tiering.md). |
| Новые возможности единого подключения для главного экземпляра SQ Server и шлюза HDFS или Spark. | См. раздел [Главный экземпляр SQL Server и шлюз HDFS или Spark](connect-to-big-data-cluster.md). |
| При удалении кластера с помощью команды **azdata cluster delete** теперь удаляются только объекты в пространстве имен, которые были частью кластера больших данных. | Пространство имен не удаляется. Однако в более ранних выпусках эта команда удаляла все пространство имен. |
| Имена конечных точек _безопасности_ были изменены и консолидированы. | Точки **service-security-lb** и **service-security-nodeport** были объединены в конечной точке **endpoint-security**. |
| Имена конечных точек _прокси_ были изменены и консолидированы. | Точки **service-proxy-lb** и **service-proxy-nodeport** были объединены в конечной точке **endpoint-service-proxy**. |
| Имена конечных точек _контроллера_ были изменены и консолидированы. | Точки **service-mssql-controller-lb** и **service-mssql-controller-nodeport** были объединены в конечную точку **endpoint-controller**. |
| &nbsp; | &nbsp; |

### <a name="known-issues"></a>Известные проблемы

В следующих разделах перечислены известные проблемы и ограничения для этого выпуска.

#### <a name="deployment"></a>Развертывание

- Обновление кластера больших данных с предыдущего выпуска не поддерживается.

   > [!IMPORTANT]
   > Перед развертыванием последнего выпуска нужно создать резервную копию данных, а затем удалить существующий кластер больших данных (с помощью предыдущей версии **azdata**). Дополнительные сведения см. в статье [Обновление до нового выпуска](deployment-upgrade.md).

- Переменная среды **ACCEPT_EULA** должна иметь значение yes или Yes для принятия условий лицензионного соглашения. В предыдущих выпусках можно было использовать значения "y" и "Y", но они больше не принимаются и приводят к сбою развертывания.

- Переменные среды **CLUSTER_PLATFORM** не имеют значения по умолчанию, как это было в предыдущих выпусках.

- После развертывания в AKS могут отобразиться следующие два события предупреждения из развертывания. Оба эти события являются известными проблемами, но они не препятствуют успешному развертыванию кластера больших данных в AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- При сбое развертывания кластера больших данных связанное пространство имен не удаляется. Это может привести к тому, что в кластере появится потерянное пространство имен. Обходной путь состоит в том, чтобы удалить пространство имен вручную перед развертыванием кластера с тем же именем.

#### <a name="kubeadm-deployments"></a>Развертывания kubeadm

Если для развертывания Kubernetes на нескольких компьютерах используется kubeadm, портал администрирования кластера неправильно отображает конечные точки, необходимые для подключения к кластеру больших данных. Если у вас возникла эта проблема, выполните следующие действия, чтобы обнаружить IP-адреса конечных точек службы.

- При подключении из кластера запросите в Kubernetes IP-адрес службы для конечной точки, к которой вы хотите подключиться. Например, следующая команда **kubectl** отображает IP-адрес главного экземпляра SQL Server.

   ```bash
   kubectl get service endpoint-master-pool -n <clusterName> -o=custom-columns="IP:.spec.clusterIP,PORT:.spec.ports[*].nodePort"
   ```

- Если вы подключаетесь извне кластера, выполните следующие действия для подключения.

   1. Получите IP-адрес узла, где выполняется главный экземпляр SQL Server: `kubectl get pod mssql-master-pool-0 -o jsonpath="Name: {.metadata.name} Status: {.status.hostIP}" -n <clusterName>`.

   1. Подключитесь к главному экземпляру SQL Server с помощью этого IP-адреса.

   1. Запросите **cluster_endpoint_table** в базе данных master для других внешних конечных точек.

      Если это не удается сделать из-за истечения времени ожидания подключения, возможно, что соответствующий узел защищен брандмауэром. В этом случае нужно обратиться к администратору кластера Kubernetes и запросить IP-адрес узла, который доступен извне. Это может быть любой узел. Затем можно использовать этот IP-адрес и соответствующий порт для подключения к различным службам, запущенным в кластере. Например, администратор может определить этот IP-адрес, выполнив следующую команду.

      ```
      [root@m12hn01 config]# kubectl cluster-info
      Kubernetes master is running at https://172.50.253.99:6443
      KubeDNS is running at https://172.30.243.91:6443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy
      ```

#### <a id="azdatactp23"></a> Средство azdata

- Для средства **azdata** порядок команд изменен с "команда — объект" на "объект — команда". Например, `azdata create cluster` теперь имеет вид `azdata cluster create`.

- Теперь параметр `--name` требуется при создании кластера с помощью `azdata cluster create`.

   ```bash
   azdata cluster create --name <cluster_name>
   ```

- Важные сведения по обновлению до последней версии кластеров больших данных и **azdata** см. в статье [Обновление до нового выпуска](deployment-upgrade.md).

#### <a name="external-tables"></a>Внешние таблицы

- Можно создать внешнюю таблицу пула данных для таблицы с неподдерживаемыми типами столбцов. При выполнении запроса к внешней таблице вы получите сообщение, аналогичное следующему.

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- При запросе внешней таблицы пула носителей может возникнуть ошибка, если одновременно с этим выполняется копирование базового файла в HDFS.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- При создании внешней таблицы для Oracle, которая использует символьные типы данных, мастер виртуализации Azure Data Studio интерпретирует эти столбцы как VARCHAR в определении внешней таблицы. Это приведет к сбою в DDL внешней таблице. Либо измените схему Oracle для использования типа NVARCHAR2, либо вручную создайте инструкции EXTERNAL TABLE и укажите NVARCHAR вместо использования мастера.

#### <a name="application-deployment"></a>Развертывание приложения

- При вызове приложения R, Python или MLeap из API на основе REST время ожидания вызова истекает через 5 минут.

#### <a name="spark-and-notebooks"></a>Spark и записные книжки

- IP-адреса объектов pod могут измениться в среде Kubernetes при перезапуске объектов pod. В сценарии, где master-pod перезагружается, сеанс Spark может завершиться с ошибкой `NoRoteToHostException`. Это вызвано тем, что кэши JVM не обновляются с использованием новых IP-адресов.

- Если вы уже установили Jupyter и используете отдельную установку Python в Windows, то записные книжки Spark могут завершиться ошибкой. Чтобы обойти эту ошибку, обновите Jupyter до последней версии.

- Если в записной книжке щелкнуть команду **Добавить текст**, текстовая ячейка добавляется в режиме предварительного просмотра, а не в режиме редактирования. Вы можете щелкнуть значок предварительного просмотра, чтобы переключиться в режим редактирования и изменить ячейку.

#### <a name="hdfs"></a>HDFS

- Если щелкнуть правой кнопкой мыши файл в HDFS для его предварительного просмотра, может появиться следующая ошибка.

   `Error previewing file: File exceeds max size of 30MB`

   Сейчас не существует способа предварительного просмотра файлов больше 30 МБ в Azure Data Studio.

- Изменения конфигурации в HDFS, затрагивающие изменения в hdfs-site.xml, не поддерживаются.

#### <a name="security"></a>безопасность

- SA_PASSWORD является частью среды и обнаруживается (например, в файле дампа cord). После развертывания нужно сбросить SA_PASSWORD в главном экземпляре. Это не ошибка, а мера безопасности. Дополнительные сведения об изменении SA_PASSWORD в контейнере Linux см. в разделе [Смена пароля администратора](../linux/quickstart-install-connect-docker.md#sapassword).

- Журналы AKS могут содержать пароль системного администратора (SA) для развертываний кластера больших данных.

## <a id="ctp22"></a> CTP 2.2 (декабрь 2018 г.)

В следующих разделах описаны новые функции и известные проблемы для кластеров больших данных в SQL Server 2019 CTP 2.2.

### <a name="new-features"></a>Новые возможности

- Доступ к порталу администрирования кластера с помощью `/portal` (**https://\<ip-адрес\>:30777/portal**).
- Имя службы главного пула изменилось с `service-master-pool-lb` и `service-master-pool-nodeport` на `endpoint-master-pool`.
- Новая версия **azdata** и обновленные образы.
- Разнообразные исправления ошибок и улучшения.

### <a name="known-issues"></a>Известные проблемы

В следующих разделах перечислены известные проблемы и ограничения для этого выпуска.

#### <a name="deployment"></a>Развертывание

- Обновление кластера больших данных с предыдущего выпуска не поддерживается. Перед развертыванием последнего выпуска нужно создать резервную копию и удалить существующий кластер больших данных. Дополнительные сведения см. в статье [Обновление до нового выпуска](deployment-upgrade.md).

- После развертывания в AKS могут отобразиться следующие два события предупреждения из развертывания. Оба эти события являются известными проблемами, но они не препятствуют успешному развертыванию кластера больших данных в AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- При сбое развертывания кластера больших данных связанное пространство имен не удаляется. Это может привести к тому, что в кластере появится потерянное пространство имен. Обходной путь состоит в том, чтобы удалить пространство имен вручную перед развертыванием кластера с тем же именем.

#### <a name="cluster-administration-portal"></a>Портал администрирования кластера

Портал администрирования кластера не отображает конечную точку для главного экземпляра SQL Server. Чтобы определить IP-адрес и порт для главного экземпляра, используйте следующую команду **kubectl**:

```
kubectl get svc endpoint-master-pool -n <your-big-data-cluster-name>
```

#### <a name="external-tables"></a>Внешние таблицы

- Можно создать внешнюю таблицу пула данных для таблицы с неподдерживаемыми типами столбцов. При выполнении запроса к внешней таблице вы получите сообщение, аналогичное следующему.

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- При запросе внешней таблицы пула носителей может возникнуть ошибка, если одновременно с этим выполняется копирование базового файла в HDFS.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

#### <a name="spark-and-notebooks"></a>Spark и записные книжки

- IP-адреса объектов pod могут измениться в среде Kubernetes при перезапуске объектов pod. В сценарии, где master-pod перезагружается, сеанс Spark может завершиться с ошибкой `NoRoteToHostException`. Это вызвано тем, что кэши JVM не обновляются с использованием новых IP-адресов.

- Если вы уже установили Jupyter и используете отдельную установку Python в Windows, то записные книжки Spark могут завершиться ошибкой. Чтобы обойти эту ошибку, обновите Jupyter до последней версии.

- Если в записной книжке щелкнуть команду **Добавить текст**, текстовая ячейка добавляется в режиме предварительного просмотра, а не в режиме редактирования. Вы можете щелкнуть значок предварительного просмотра, чтобы переключиться в режим редактирования и изменить ячейку.

#### <a name="hdfs"></a>HDFS

- Если щелкнуть правой кнопкой мыши файл в HDFS для его предварительного просмотра, может появиться следующая ошибка.

   `Error previewing file: File exceeds max size of 30MB`

   Сейчас не существует способа предварительного просмотра файлов больше 30 МБ в Azure Data Studio.

- Изменения конфигурации в HDFS, затрагивающие изменения в hdfs-site.xml, не поддерживаются.

#### <a name="security"></a>безопасность

- SA_PASSWORD является частью среды и обнаруживается (например, в файле дампа cord). После развертывания нужно сбросить SA_PASSWORD в главном экземпляре. Это не ошибка, а мера безопасности. Дополнительные сведения об изменении SA_PASSWORD в контейнере Linux см. в разделе [Смена пароля администратора](../linux/quickstart-install-connect-docker.md#sapassword).

- Журналы AKS могут содержать пароль системного администратора (SA) для развертываний кластера больших данных.

## <a id="ctp21"></a> CTP 2.1 (ноябрь 2018 г.)

В следующих разделах описаны новые функции и известные проблемы для кластеров больших данных в SQL Server 2019 CTP 2.1.

### <a name="new-features"></a>Новые возможности

- [Развертывание приложений Python и R](big-data-cluster-create-apps.md) в кластере больших данных.
- Новая версия **azdata** и обновленные образы. 
- Разнообразные исправления ошибок и улучшения.

### <a name="known-issues"></a>Известные проблемы

В следующих разделах приведены известные проблемы для [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] в CTP 2,1.

#### <a name="deployment"></a>Развертывание

- Обновление кластера больших данных с предыдущего выпуска не поддерживается. Перед развертыванием последнего выпуска нужно создать резервную копию и удалить существующий кластер больших данных. Дополнительные сведения см. в статье [Обновление до нового выпуска](deployment-upgrade.md).

- После развертывания в AKS могут отобразиться следующие два события предупреждения из развертывания. Оба эти события являются известными проблемами, но они не препятствуют успешному развертыванию кластера больших данных в AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- При сбое развертывания кластера больших данных связанное пространство имен не удаляется. Это может привести к тому, что в кластере появится потерянное пространство имен. Обходной путь состоит в том, чтобы удалить пространство имен вручную перед развертыванием кластера с тем же именем.

#### <a name="admin-portal"></a>Портал администрирования

- Когда вы [создаете приложение с помощью команды msqlctl-ctp](big-data-cluster-create-apps.md) и развертываете его в кластере больших данных SQL Server, на портале администрирования кластера объекты pod, где было развернуто приложение, отображаются с состоянием "Неизвестно" в разделе "Контроллер" области администрирования.

#### <a name="external-tables"></a>Внешние таблицы

- Можно создать внешнюю таблицу пула данных для таблицы с неподдерживаемыми типами столбцов. При выполнении запроса к внешней таблице вы получите сообщение, аналогичное следующему.

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- При запросе внешней таблицы пула носителей может возникнуть ошибка, если одновременно с этим выполняется копирование базового файла в HDFS.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

#### <a name="spark-and-notebooks"></a>Spark и записные книжки

- IP-адреса объектов pod могут измениться в среде Kubernetes при перезапуске объектов pod. В сценарии, где master-pod перезагружается, сеанс Spark может завершиться с ошибкой `NoRoteToHostException`. Это вызвано тем, что кэши JVM не обновляются с использованием новых IP-адресов.

- Если вы уже установили Jupyter и используете отдельную установку Python в Windows, то записные книжки Spark могут завершиться ошибкой. Чтобы обойти эту ошибку, обновите Jupyter до последней версии.

- Если в записной книжке щелкнуть команду **Добавить текст**, текстовая ячейка добавляется в режиме предварительного просмотра, а не в режиме редактирования. Вы можете щелкнуть значок предварительного просмотра, чтобы переключиться в режим редактирования и изменить ячейку.

#### <a name="hdfs"></a>HDFS

- Если щелкнуть правой кнопкой мыши файл в HDFS для его предварительного просмотра, может появиться следующая ошибка.

   `Error previewing file: File exceeds max size of 30MB`

   Сейчас не существует способа предварительного просмотра файлов больше 30 МБ в Azure Data Studio.

- Изменения конфигурации в HDFS, затрагивающие изменения в hdfs-site.xml, не поддерживаются.

#### <a name="security"></a>безопасность

- SA_PASSWORD является частью среды и обнаруживается (например, в файле дампа cord). После развертывания нужно сбросить SA_PASSWORD в главном экземпляре. Это не ошибка, а мера безопасности. Дополнительные сведения об изменении SA_PASSWORD в контейнере Linux см. в разделе [Смена пароля администратора](../linux/quickstart-install-connect-docker.md#sapassword).

- Журналы AKS могут содержать пароль системного администратора (SA) для развертываний кластера больших данных.

## <a id="ctp20"></a> CTP 2.0 (октябрь 2018 г.)

В следующих разделах описаны новые функции и известные проблемы для кластеров больших данных в SQL Server 2019 CTP 2.0.

### <a name="new-features"></a>Новые возможности

- Простой интерфейс развертывания с использованием средства управления azdata
- Собственный интерфейс записных книжек в Azure Data Studio
- Запрос файлов HDFS через экземпляр хранилища SQL Server
- Виртуализация данных через главный экземпляр в SQL Server, Oracle, MongoDB и HDFS
- Мастер виртуализации данных для SQL Server и Oracle в Azure Data Studio
- Службы машинного обучения в главном экземпляре
- Портал администрирования кластера, который можно использовать для мониторинга и устранения неполадок
- Отправка заданий Spark в Azure Data Studio 
- Пользовательский интерфейс Spark на портале администрирования кластера
- Подключение тома к классам хранилища
- Запросы к пулам данных из главного экземпляра
- Отображение плана для распределенных запросов в SSMS
- Пакет PIP для средства управления azdata
- Встроенный механизм развертывания через службу контроллера

### <a name="known-issues"></a>Известные проблемы

В следующих разделах приведены известные проблемы для [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] в CTP 2,0.

#### <a name="deployment"></a>Развертывание

- Если вы используете Службу Azure Kubernetes (AKS), рекомендуемой версией Kubernetes является 1.10. *, которая не поддерживает изменение размера диска. Нужно проследить за тем, чтобы размер хранилища был задан должным образом во время развертывания. Дополнительные сведения о настройке размеров хранилища см. в статье [Сохраняемость данных](concept-data-persistence.md). Для Kubernetes, развернутой на виртуальных машинах, рекомендуется использовать версию 1.11.

- После развертывания в AKS могут отобразиться следующие два события предупреждения из развертывания. Оба эти события являются известными проблемами, но они не препятствуют успешному развертыванию кластера больших данных в AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- При сбое развертывания кластера больших данных связанное пространство имен не удаляется. Это может привести к тому, что в кластере появится потерянное пространство имен. Обходной путь состоит в том, чтобы удалить пространство имен вручную перед развертыванием кластера с тем же именем.

#### <a name="external-tables"></a>Внешние таблицы

- Можно создать внешнюю таблицу пула данных для таблицы с неподдерживаемыми типами столбцов. При выполнении запроса к внешней таблице вы получите сообщение, аналогичное следующему.

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- При запросе внешней таблицы пула носителей может возникнуть ошибка, если одновременно с этим выполняется копирование базового файла в HDFS.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

#### <a name="spark-and-notebooks"></a>Spark и записные книжки

- IP-адреса объектов pod могут измениться в среде Kubernetes при перезапуске объектов pod. В сценарии, где master-pod перезагружается, сеанс Spark может завершиться с ошибкой `NoRoteToHostException`. Это вызвано тем, что кэши JVM не обновляются с использованием новых IP-адресов.

- Если вы уже установили Jupyter и используете отдельную установку Python в Windows, то записные книжки Spark могут завершиться ошибкой. Чтобы обойти эту ошибку, обновите Jupyter до последней версии.

- Если в записной книжке щелкнуть команду **Добавить текст**, текстовая ячейка добавляется в режиме предварительного просмотра, а не в режиме редактирования. Вы можете щелкнуть значок предварительного просмотра, чтобы переключиться в режим редактирования и изменить ячейку.

#### <a name="hdfs"></a>HDFS

- Если щелкнуть правой кнопкой мыши файл в HDFS для его предварительного просмотра, может появиться следующая ошибка.

   `Error previewing file: File exceeds max size of 30MB`

   Сейчас не существует способа предварительного просмотра файлов больше 30 МБ в Azure Data Studio.

- Изменения конфигурации в HDFS, затрагивающие изменения в hdfs-site.xml, не поддерживаются.

#### <a name="security"></a>безопасность

- SA_PASSWORD является частью среды и обнаруживается (например, в файле дампа cord). После развертывания нужно сбросить SA_PASSWORD в главном экземпляре. Это не ошибка, а мера безопасности. Дополнительные сведения об изменении SA_PASSWORD в контейнере Linux см. в разделе [Смена пароля администратора](../linux/quickstart-install-connect-docker.md#sapassword).

- Журналы AKS могут содержать пароль системного администратора (SA) для развертываний кластера больших данных.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] см. в разделе [что такое [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md).
