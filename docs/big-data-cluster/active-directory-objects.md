---
title: Объекты Active Directory
titleSuffix: SQL Server Big Data Cluster
description: Узнайте больше о развертывании кластера больших данных SQL Server в домене Active Directory.
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 06/22/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: e4f8736beeac2e92d25092c60c3fe7e60127ea94
ms.sourcegitcommit: 591bbf4c7e4e2092f8abda6a2ffed263cb61c585
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86942746"
---
# <a name="auto-generated-active-directory-objects"></a>Автоматически созданные объекты Active Directory

В этой статье описываются учетные записи и группы Active Directory (AD), которые SQL Server создает во время развертывания кластера больших данных.

## <a name="accounts--groups"></a>Учетные записи и группы

Учетные записи пользователей и группы создаются в предоставленном [подразделении](/windows-server/identity/ad-ds/plan/reviewing-ou-design-concepts) во время развертывания кластера.

Каждая из учетных записей представляет собой службу в кластере больших данных. У учетных записей есть имена субъектов-служб (SPN), необходимые для каждой службы. Имена субъектов-служб, принадлежащие каждой учетной записи, можно получить с помощью команды [setspn](https://social.technet.microsoft.com/wiki/contents/articles/717.service-principal-names-spn-setspn-syntax.aspx).

При развертывании автоматически создаются имена учетных записей и групп. Начиная с SQL Server 2019 CU5 префикс имени учетной записи или группы — это имя пространства имен развертывания (имя кластера больших данных). Если имя кластера в этой статье — `bdc`, замените `<prefix>` на `bdc` для поиска учетных записей.

Суффикс pod (-x) обозначает переменную с идентификатором pod ниже. Указанные ниже имена не включают в себя префикс переменной, указанный пользователем во время развертывания.

Имя классической учетной записи применяется к развертываниям с использованием версий, предшествующих SQL Server 2019 CU5, а также к развертываниям, выполненным с параметром useSubdomain, для которого задано значение false в конфигурации безопасности.

| Имя учетной записи или группы|Дополнительные сведения|
|----|---|
|`<prefix>-ctrl`|[Учетная запись службы контроллера](#controller-service-account)|
|`<prefix>-ngxm`|[Учетная запись службы прокси-сервера службы мониторинга](#monitoring-service-proxy-service-account)|
|`<prefix>-ldap`|[Пользователь поиска LDAP](#ldap-lookup-user)|
|`<prefix>-sqc0-x/<prefix>-sqc0`|[Пользователь SQL Server пула вычислений](#compute-pool-sql-server-user)|
|`<prefix>-dmc0-x`|[Пользователь DMS хранилища данных пула вычислений](#compute-pool-data-warehouse-dms-user)|
|`<prefix>-dec0-x`|[Пользователь подсистемы хранилища данных пула вычислений](#compute-pool-data-warehouse-engine-user)|
|`<prefix>-sqd0`|[Пользователь SQL Server пула данных](#data-pool-sql-server-user)|
|`<prefix>-sqs0`|[Пользователь SQL Server пула носителей](#storage-pool-sql-server-user)|
|`<prefix>-ynt0-x`|[Пользователь службы диспетчера узлов Yarn пула носителей](#storage-pool-yarn-node-manager-service-user)|
|`<prefix>-htt0`|[Пользователь службы HTTP пула носителей](#storage-pool-http-service-user)|
|`<prefix>-hdt0`|[Пользователь службы узлов данных HDFS пула носителей](#storage-pool-hdfs-datanode-service-user)|
|`<prefix>-hdnn`|[Пользователь службы узла имен HDFS](#hdfs-name-node-service-user)|
|`<prefix>-htnn`|[Пользователь службы HTTP узла имен HDFS](#hdfs-name-node-http-service-user)|
|`<prefix>-kmnn-x`|[Пользователь службы KMS узла имен](#name-node-kms-service-user)|
|`<prefix>-jnzk-x`|[Пользователи службы Zookeeper JournalNode](#zookeeper-journalnode-service-users)|
|`<prefix>-htzk`|[Пользователь службы HTTP Zookeeper](#zookeeper-http-service-user)|
|`<prefix>-yrsh-x`|[Пользователь службы диспетчера ресурсов Sparkhead Yarn](#sparkhead-yarn-resource-manager-service-user)|
|`<prefix>-htsh`|[Пользователь Sparkhead HTTP](#sparkhead-http-user)|
|`<prefix>-shsh-x`|[Пользователь службы журнала Sparkhead Spark](#sparkhead-spark-history-service-user)|
|`<prefix>-lvsh-x`|[Пользователь службы Sparkhead Livy](#sparkhead-livy-service-user)|
|`<prefix>-hvsh-x`|[Пользователь службы Sparkhead Hive](#sparkhead-hive-service-user)|
|`<prefix>-yns0-x`|[Пользователь службы диспетчера узлов Yarn пула Spark](#spark-pool-yarn-node-manager-service-user)|
|`<prefix>-hts0`|[Пользователь HTTP диспетчера узлов Yarn пула Spark](#spark-pool-yarn-node-manager-http-user)|
|`<prefix>-knox-x`|[Пользователь шлюза Knox](#knox-gateway-user)|
|`<prefix>-htgw`|[Пользователь HTTP шлюза Knox](#knox-gateway-http-user)|
|`<prefix>-apst`|[Пользователь установки приложения](#app-setup-user)|
|`<prefix>-dmsvc`|[Группа службы DMS хранилища данных](#data-warehouse-dms-service-group)|
|`<prefix>-desvc`|[Группа службы подсистемы хранилища данных](#data-warehouse-engine-service-group)|

В следующем разделе приведены дополнительные сведения о каждой учетной записи. Чтобы получить сведения о группах, перейдите к разделу [Группы](#groups).

## <a name="controller-management--ldap-related-accounts"></a>Контроллеры, управление и учетные записи, связанные с LDAP

### <a name="controller-service-account"></a>Учетная запись службы контроллера

|Объект|Имя учетной записи|
|---|---|
|Имя масштабируемого набора|`control`|
|Имя объекта pod|`control-x`|
|Имя контейнера|`controller`|
|Имя службы|`controller`|
|Имя учетной записи (без префикса)| `ctrl`|
|Учетная запись (с префиксом пространства имен)|`<prefix>-ctrl`|
|Имя классической учетной записи|`ctrl-controller`|

### <a name="monitoring-service-proxy-service-account"></a>Учетная запись службы прокси-сервера службы мониторинга

|Объект|Имя учетной записи|
|---|---|
|Имя масштабируемого набора|`mgmtproxy`|
|Имя объекта pod|`mgmtproxy-x`|
|Имя контейнера|`service-proxy`|
|Имя службы|`nginx`|
|Учетная запись (без префикса)| `ngxm`|
|Учетная запись (с префиксом пространства имен)|`<prefix>-ngxm`|
|Имя классической учетной записи|`nginx-mgmtproxy`|

### <a name="ldap-lookup-user"></a>Пользователь поиска LDAP

Используется службами Grafana и Hadoop для поиска пользователей по протоколу LDAP.

|Объект|Имя учетной записи|
|---|---|
|Имя масштабируемого набора|`metricsui`|
|Имя объекта pod|`metricsui-x`|
|Имя контейнера|`grafana`|
|Имя службы|`grafana`|
|Имя учетной записи (без префикса)| `ldap`|
|Имя учетной записи (с префиксом пространства имен)|`<prefix>-ldap`|
|Имя классической учетной записи|`ldap-user`|

## <a name="master-pool-accounts"></a>Учетные записи главного пула

### <a name="master-pool-sql-server-user"></a>Пользователь SQL Server главного пула

|Объект|Имя учетной записи|
|---|---|
|Имя масштабируемого набора|`master`|
|Имя объекта pod|`master-x`|
|Имя контейнера|`mssql-server`|
|Имя службы|`mssql`|
|Имя учетной записи (без префикса)| `sqmp-x/sqmp`|
|Имя учетной записи (с префиксом пространства имен)|`<prefix>-sqmp-x/<prefix>-sqmp`|
|Имя классической учетной записи|`mssql-master-x`|

### <a name="master-pool-data-warehouse-dms-user"></a>Пользователь DMS хранилища данных главного пула

|Объект|Имя учетной записи|
|---|---|
|Имя масштабируемого набора|`master`|
|Имя объекта pod|`master-x`|
|Имя контейнера|`mssql-server`|
|Имя службы|`dwdms`|
|Учетная запись (без префикса)| `dmmp-x`|
|Учетная запись (с префиксом пространства имен)|`<prefix>-dmmp-x`|
|Имя классической учетной записи|`dwdms-master-x`|

### <a name="master-pool-data-warehouse-engine-user"></a>Пользователь подсистемы хранилища данных главного пула

|Объект|Имя учетной записи|
|---|---|
|Имя масштабируемого набора|`master`|
|Имя объекта pod|`master-x`|
|Имя контейнера|`mssql-server`|
|Имя службы|`dweng`|
|Учетная запись (без префикса)| `demp`|
|Учетная запись (с префиксом пространства имен)|`<prefix>-demp-x`|
|Имя классической учетной записи|`dweng-master-x`|

## <a name="compute-pool-accounts"></a>Учетные записи вычислительного пула

### <a name="compute-pool-sql-server-user"></a>Пользователь SQL Server пула вычислений

|Объект|Имя учетной записи|
|---|---|
|Имя масштабируемого набора|`compute-0`|
|Имя объекта pod|`compute-0-x`|
|Имя контейнера|`mssql-server`|
|Имя службы|`mssql`|
|Учетная запись (без префикса)| `sqc0-x/sqlc0`|
|Учетная запись (с префиксом пространства имен)|`<prefix>-sqc0-x/<prefix>-sqc0`|
|Имя классической учетной записи|`mssql-compute-0-x`|

### <a name="compute-pool-data-warehouse-dms-user"></a>Пользователь DMS хранилища данных пула вычислений

|Объект|Имя учетной записи|
|---|---|
|Имя масштабируемого набора|`compute-0`|
|Имя объекта pod|`compute-0-x`|
|Имя контейнера|`mssql-server`|
|Имя службы|`dwdms`|
|Учетная запись (без префикса)| `dmc0-x`|
|Учетная запись (с префиксом пространства имен)|`<prefix>-dmc0-x`|
|Имя классической учетной записи|`dwdms-compute-0-x`|

### <a name="compute-pool-data-warehouse-engine-user"></a>Пользователь подсистемы хранилища данных пула вычислений

|Объект|Имя учетной записи|
|---|---|
|Имя масштабируемого набора|`compute-0`|
|Имя объекта pod|`compute-0-x`|
|Имя контейнера|`mssql-server`|
|Имя службы|`dweng`|
|Учетная запись (без префикса)| `dec0-x`|
|Учетная запись (с префиксом пространства имен)|`<prefix>-dec0-x`|
|Имя классической учетной записи|`dweng-compute-0-x`|

## <a name="data-pool-accounts"></a>Учетные записи пула данных

### <a name="data-pool-sql-server-user"></a>Пользователь SQL Server пула данных

|Объект|Имя учетной записи|
|---|---|
|Имя масштабируемого набора|`data-0`|
|Имя объекта pod|`data-0-x`|
|Имя контейнера|`mssql-server`|
|Имя службы|`mssql`|
|Учетная запись (без префикса)| `sqd0`|
|Учетная запись (с префиксом пространства имен)|`<prefix>-sqd0`|
|Имя классической учетной записи|`mssql-data-0`|

## <a name="storage-pool-accounts"></a>Учетные записи пула носителей

### <a name="storage-pool-sql-server-user"></a>Пользователь SQL Server пула носителей

|Объект|Имя учетной записи|
|---|---|
|Имя масштабируемого набора|`storage-0`|
|Имя объекта pod|`storage-0-x`|
|Имя контейнера|`mssql-server`|
|Имя службы|`mssql`|
|Учетная запись (без префикса)| `sqs0`|
|Учетная запись (с префиксом пространства имен)|`<prefix>-sqs0`|
|Имя классической учетной записи|`mssql-storage-0`|

### <a name="storage-pool-yarn-node-manager-service-user"></a>Пользователь службы диспетчера узлов Yarn пула носителей

|Объект|Имя учетной записи|
|---|---|
|Имя масштабируемого набора|`storage-0`|
|Имя объекта pod|`storage-0-x`|
|Имя контейнера|`hadoop`|
|Имя службы|`Yarn Node Manager`|
|Учетная запись (без префикса)| `ynt0-x`|
|Учетная запись (с префиксом пространства имен)|`<prefix>-ynt0-x`|
|Имя классической учетной записи|`yarnnm-storage-0-x`|

### <a name="storage-pool-http-service-user"></a>Пользователь службы HTTP пула носителей

|Объект|Имя учетной записи|
|---|---|
|Имя масштабируемого набора|`storage-0`|
|Имя объекта pod|`storage-0-x`|
|Имя контейнера|`hadoop`|
|Имя службы|`HDFS Datanode`|
|Учетная запись (без префикса)| `hdt0`|
|Учетная запись (с префиксом пространства имен)|`<prefix>-hdt0`|
|Имя классической учетной записи|`http-storage-0`|

### <a name="storage-pool-hdfs-datanode-service-user"></a>Пользователь службы узлов данных HDFS пула носителей

|Объект|Имя учетной записи|
|---|---|
|Имя масштабируемого набора|`storage-0`|
|Имя объекта pod|`storage-0-x`|
|Имя контейнера|`hadoop`|
|Имя службы|`HDFS Datanode`|
|Учетная запись (без префикса)| `hdt0`|
|Учетная запись (с префиксом пространства имен)|`<prefix>-hdt0`|
|Имя классической учетной записи|`hdfsdn-storage-0`|

## <a name="hdfs-accounts"></a>Учетные записи HDFS

### <a name="hdfs-name-node-service-user"></a>Пользователь службы узла имен HDFS

|Объект|Имя учетной записи|
|---|---|
|Имя масштабируемого набора|`nmnode-0`|
|Имя объекта pod|`nmnode-0-x`|
|Имя контейнера|`hadoop`|
|Имя службы|`HDFS Namenode`|
|Учетная запись (без префикса)| `hdnn`|
|Учетная запись (с префиксом пространства имен)|`<prefix>-hdnn`|
|Имя классической учетной записи|`hdfsnn-nmnode`|

### <a name="hdfs-name-node-http-service-user"></a>Пользователь службы HTTP узла имен HDFS

|Объект|Имя учетной записи|
|---|---|
|Имя масштабируемого набора|`nmnode-0`|
|Имя объекта pod|`nmnode-0-x`|
|Имя контейнера|`hadoop`|
|Имя службы|`HDFS Namenode`|
|Учетная запись (без префикса)| `htnn`|
|Учетная запись (с префиксом пространства имен)|`<prefix>-htnn`|
|Имя классической учетной записи|`http-nmnode`|

## <a name="kms-accounts"></a>Учетные записи KMS

### <a name="name-node-kms-service-user"></a>Пользователь службы KMS узла имен

|Объект|Имя учетной записи|
|---|---|
|Имя масштабируемого набора|`nmnode-0`|
|Имя объекта pod|`nmnode-0-x`|
|Имя контейнера|`hadoop`|
|Имя службы|`KMS`|
|Учетная запись (без префикса)| `kmnn-x`|
|Учетная запись (с префиксом пространства имен)|`<prefix>-kmnn-x`|
|Имя классической учетной записи|`kms-nmnode-x`|

## <a name="zookeeper-accounts"></a>Учетные записи Zookeeper

### <a name="zookeeper-journalnode-service-users"></a>Пользователи службы Zookeeper JournalNode

|Объект|Имя учетной записи|
|---|---|
|Имя масштабируемого набора|`zookeeper`|
|Имя объекта pod|`zookeeper-x`|
|Имя контейнера|`zookeeper`|
|Имя службы|`Journal node`|
|Учетная запись (без префикса)| `jnzk-x`|
|Учетная запись (с префиксом пространства имен)|`<prefix>-jnzk-x`|
|Имя классической учетной записи|`jn-zookeeper-x`|

### <a name="zookeeper-http-service-user"></a>Пользователь службы HTTP Zookeeper

|Объект|Имя учетной записи|
|---|---|
|Имя масштабируемого набора|`zookeeper`|
|Имя объекта pod|`zookeeper-x`|
|Имя контейнера|`zookeeper`|
|Имя службы|`Zookeeper`|
|Учетная запись (без префикса)| `htzk`|
|Учетная запись (с префиксом пространства имен)|`<prefix>-htzk`|
|Имя классической учетной записи|`http-zookeeper`|

## <a name="spark-related-accounts"></a>Учетные записи, связанные со Spark

### <a name="sparkhead-yarn-resource-manager-service-user"></a>Пользователь службы диспетчера ресурсов Sparkhead Yarn

|Объект|Имя учетной записи|
|---|---|
|Имя масштабируемого набора|`sparkhead`|
|Имя объекта pod|`sparkhead-x`|
|Имя контейнера|`hadoop-yarn-jobhistory`|
|Имя службы|`Yarn Resource Manager`|
|Учетная запись (без префикса)| `yrsh-x`|
|Учетная запись (с префиксом пространства имен)|`<prefix>-yrsh-x`|
|Имя классической учетной записи|`yarnrm-sparkhead-x`|

### <a name="sparkhead-http-user"></a>Пользователь Sparkhead HTTP

|Объект|Имя учетной записи|
|---|---|
|Имя масштабируемого набора|`sparkhead`|
|Имя объекта pod|`sparkhead-x`|
|Имя контейнера|`*`|
|Имя службы|`*`|
|Учетная запись (без префикса)| `htsh`|
|Учетная запись (с префиксом пространства имен)|`<prefix>-htsh`|
|Имя классической учетной записи|`http-sparkhead`|

### <a name="sparkhead-spark-history-service-user"></a>Пользователь службы журнала Sparkhead Spark

|Объект|Имя учетной записи|
|---|---|
|Имя масштабируемого набора|`sparkhead`|
|Имя объекта pod|`sparkhead-x`|
|Имя контейнера|`hadoop-livy-sparkhistory`|
|Имя службы|`Spark History Server`|
|Учетная запись (без префикса)| `shsh-x`|
|Учетная запись (с префиксом пространства имен)|`<prefix>-shsh-x`|
|Имя классической учетной записи|`sph-sparkhead-x`|

### <a name="sparkhead-livy-service-user"></a>Пользователь службы Sparkhead Livy

|Объект|Имя учетной записи|
|---|---|
|Имя масштабируемого набора|`sparkhead`|
|Имя объекта pod|`sparkhead-x`|
|Имя контейнера|`hadoop-livy-sparkhistory`|
|Имя службы|`Livy`|
|Учетная запись (без префикса)| `lvsh-x`|
|Учетная запись (с префиксом пространства имен)|`<prefix>-lvsh-x`|
|Имя классической учетной записи|`livy-sparkhead-x`|

### <a name="sparkhead-hive-service-user"></a>Пользователь службы Sparkhead Hive

|Объект|Имя учетной записи|
|---|---|
|Имя масштабируемого набора|`sparkhead`|
|Имя объекта pod|`sparkhead-x`|
|Имя контейнера|`hadoop-hivemetastore`|
|Имя службы|`Hive Metastore`|
|Учетная запись (без префикса)| `hvsh-x`|
|Учетная запись (с префиксом пространства имен)|`<prefix>-hvsh-x`|
|Имя классической учетной записи|`hive-sparkhead-x`|

### <a name="spark-pool-yarn-node-manager-service-user"></a>Пользователь службы диспетчера узлов Yarn пула Spark

|Объект|Имя учетной записи|
|---|---|
|Имя масштабируемого набора|`spark-0`|
|Имя объекта pod|`spark-0-x`|
|Имя контейнера|`hadoop`|
|Имя службы|`Yarn Node Manager`|
|Учетная запись (без префикса)| `yns0-x`|
|Учетная запись (с префиксом пространства имен)|`<prefix>-yns0-x`|
|Имя классической учетной записи|`yarnnm-spark-0-x`|

### <a name="spark-pool-yarn-node-manager-http-user"></a>Пользователь HTTP диспетчера узлов Yarn пула Spark

|Объект|Имя учетной записи|
|---|---|
|Имя масштабируемого набора|`spark-0`|
|Имя объекта pod|`spark-0-x`|
|Имя контейнера|`hadoop`|
|Имя службы|`Yarn Node Manager`|
|Учетная запись (без префикса)| `hts0`|
|Учетная запись (с префиксом пространства имен)|`<prefix>-hts0`|
|Имя классической учетной записи|`http-spark-0`|

## <a name="knox-accounts"></a>Учетные записи Knox

### <a name="knox-gateway-user"></a>Пользователь шлюза Knox

|Объект|Имя учетной записи|
|---|---|
|Имя масштабируемого набора|`gateway`|
|Имя объекта pod|`gateway-x`|
|Имя контейнера|`knox`|
|Имя службы|`Knox`|
|Учетная запись (без префикса)| `knox-x`|
|Учетная запись (с префиксом пространства имен)|`<prefix>-knox-x`|
|Имя классической учетной записи|`knox-gateway-x`|

### <a name="knox-gateway-http-user"></a>Пользователь HTTP шлюза Knox

|Объект|Имя учетной записи|
|---|---|
|Имя масштабируемого набора|`gateway`|
|Имя объекта pod|`gateway-x`|
|Имя контейнера|`knox`|
|Имя службы|`Knox`|
|Учетная запись (без префикса)| `htgw`|
|Учетная запись (с префиксом пространства имен)|`<prefix>-htgw`|
|Имя классической учетной записи|`http-gateway`|

## <a name="app-accounts"></a>Учетные записи приложений

### <a name="app-setup-user"></a>Пользователь установки приложения

|Объект|Имя учетной записи|
|---|---|
|Имя масштабируемого набора|`appproxy`|
|Имя объекта pod|`appproxy-x`|
|Имя контейнера|`App Service Proxy`|
|Имя службы|`nginx`|
|Учетная запись (без префикса)| `apst`|
|Учетная запись (с префиксом пространства имен)|`<prefix>-apst`|
|Имя классической учетной записи|`app-setup`|

## <a name="groups"></a>Группы

Следующие группы создаются в подразделении, указанном пользователем. Члены групп — это пользователи, созданные выше для соответствующих служб.

### <a name="data-warehouse-dms-service-group"></a>Группа службы DMS хранилища данных

|Объект|Имя группы|
|---|---|
|Имя масштабируемого набора|`master/compute-0`|
|Имя объекта pod|`master-x/compute-0-x`|
|Имя контейнера|`mssql-server`|
|Имя службы|`dwdms`|
|Группа (без префикса)| `dmsvc`|
|Учетная запись (с префиксом пространства имен)|`<prefix>-dmsvc`|
|Имя классической учетной записи|`dwdms-service`|

### <a name="data-warehouse-engine-service-group"></a>Группа службы подсистемы хранилища данных

|Объект|Имя группы|
|---|---|
|Имя масштабируемого набора|`master/compute-0`|
|Имя объекта pod|`master-x/compute-0-x`|
|Имя контейнера|`mssql-server`|
|Имя службы|`dweng`|
|Группа (без префикса)| `desvc`|
|Учетная запись (с префиксом пространства имен)|`<prefix>-desvc`|
|Имя классической учетной записи|`desvc`|

## <a name="next-steps"></a>Дальнейшие действия

[Развертывание [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] в режиме Active Directory](deploy-active-directory.md)

[Развертывание нескольких [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] в одном домене Active Directory](active-directory-deployment-background.md)
