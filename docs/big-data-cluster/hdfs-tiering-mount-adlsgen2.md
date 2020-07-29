---
title: Подключение Azure Data Lake Storage 2-го поколения для распределения по уровням HDFS
titleSuffix: How to mount ADLS Gen2
description: В этой статье описывается настройка распределения по уровням HDFS для подключения внешней файловой системы Azure Data Lake Storage к HDFS в кластере больших данных SQL Server 2019.
author: nelgson
ms.author: negust
ms.reviewer: mikeray
ms.date: 06/29/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: b0206ca193e6c03624c0d40d0c66e7474b00a7a0
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85730655"
---
# <a name="how-to-mount-adls-gen2-for-hdfs-tiering-in-a-big-data-cluster"></a>Подключение ADLS 2-го поколения для распределения по уровням HDFS в кластере больших данных

В следующих разделах приводится пример настройки распределения по уровням HDFS для источника данных Azure Data Lake Storage 2-го поколения.

## <a name="prerequisites"></a>Предварительные требования

- [Развернутый кластер больших данных](deployment-guidance.md)
- [Средства работы с большими данными](deploy-big-data-tools.md)
  - **azdata**
  - **kubectl**

## <a name="load-data-into-azure-data-lake-storage"></a><a id="load"></a> Загрузка данных в Azure Data Lake Storage

В следующем разделе описано, как настроить Azure Data Lake Storage 2-го поколения для тестирования распределения по уровням HDFS. Если у вас уже есть данные, хранящиеся в Azure Data Lake Storage, можно пропустить этот раздел, чтобы использовать собственные данные.

1. [Создайте учетную запись хранения с возможностями Data Lake Storage 2-го поколения](/azure/storage/blobs/data-lake-storage-quickstart-create-account).

1. [Создайте файловую систему](/azure/storage/blobs/data-lake-storage-explorer) в этой учетной записи хранения для своих данных.

1. Отправьте файл CSV или Parquet в этот контейнер. Это внешние данные HDFS, которые будут подключены к HDFS в кластере больших данных.

## <a name="credentials-for-mounting"></a>Учетные данные для подключения

### <a name="use-oauth-credentials-to-mount"></a>Использование учетных данных OAuth для подключения

Чтобы использовать учетные данные OAuth для подключения, нужно выполнить следующие действия:

1. Перейдите на [портал Azure](https://portal.azure.com).
1. Перейдите в Azure Active Directory. Эта служба должна отображаться в левой панели навигации.
1. В правой панели навигации выберите "Регистрация приложений" и создайте новую регистрацию.
1. Создайте "веб-приложение" и следуйте указаниям мастера. **Запишите имя созданного здесь приложения**. Его потребуется добавить в учетную запись ADLS в качестве полномочного пользователя. Также обратите внимание на идентификатор клиента приложения в обзоре при выборе приложения.
1. После создания веб-приложения перейдите в раздел "Сертификаты и секреты", создайте **новый секрет клиента** и выберите длину ключа. **Добавьте** этот секрет.
1. Вернитесь на страницу "Регистрация приложений" и нажмите кнопку "Конечные точки", которая находится вверху. **Запишите URL-адрес конечной точки токена OAuth (v2)**
1. Теперь вы должны располагать следующими компонентами для OAuth:

    - идентификатором клиента приложения для веб-приложения;
    - секретом клиента;
    - конечной точкой маркера.

### <a name="adding-the-service-principal-to-your-adls-account"></a>Добавление субъекта-службы в вашу учетную запись ADLS

1. Снова перейдите на портал, перейдите в файловую систему своей учетной записи хранения ADLS и выберите в меню слева пункт "Управление доступом (IAM)".
1. Выберите "Добавить назначение ролей". 
1. Выберите роль "Участник данных BLOB-объектов хранилища".
1. Найдите имя, созданное выше (обратите внимание, что оно не отображается в списке, но будет найдено при поиске по полному имени).
1. Сохраните роль.

Подождите 5–10 минут перед использованием учетных данных для подключения.

### <a name="set-environment-variable-for-oauth-credentials"></a>Установка переменной среды для учетных данных OAuth

Откройте командную строку на клиентском компьютере, который может получать доступ к кластеру больших данных. Задайте переменную среды в следующем формате. Учетные данные должны быть в виде списка с разделителями-запятыми. В Windows используется команда "set". В Linux следует использовать команду "export".

**Обратите внимание**, что при вводе учетных данных необходимо удалить все разрывы строк и пробелы между запятыми (","). Формат, который используется ниже, выбран только для удобства чтения.

```console
   set MOUNT_CREDENTIALS=fs.azure.account.auth.type=OAuth,
   fs.azure.account.oauth.provider.type=org.apache.hadoop.fs.azurebfs.oauth2.ClientCredsTokenProvider,
   fs.azure.account.oauth2.client.endpoint=[token endpoint],
   fs.azure.account.oauth2.client.id=[Application client ID],
   fs.azure.account.oauth2.client.secret=[client secret]
```

## <a name="use-access-keys-to-mount"></a>Использование ключа доступа для подключения

Можно также подключиться с помощью ключей доступа, которые можно получить для своей учетной записи ADLS на портале Azure.

 > [!TIP]
   > Дополнительные сведения о том, как найти ключ доступа (`<storage-account-access-key>`) для своей учетной записи хранения, см. в разделе [Просмотр строки подключения и ключей учетной записи](/azure/storage/common/storage-account-keys-manage#view-access-keys-and-connection-string).

### <a name="set-environment-variable-for-access-key-credentials"></a>Установка переменной среды для учетных данных ключей доступа

1. Откройте командную строку на клиентском компьютере, который может получать доступ к кластеру больших данных.

1. Откройте командную строку на клиентском компьютере, который может получать доступ к кластеру больших данных. Задайте переменную среды в следующем формате. Учетные данные нужно задавать в виде списка с разделителями-запятыми. В Windows используется команда "set". В Linux следует использовать команду "export".

**Обратите внимание**, что при вводе учетных данных необходимо удалить все разрывы строк и пробелы между запятыми (","). Формат, который используется ниже, выбран только для удобства чтения.

```console
set MOUNT_CREDENTIALS=fs.azure.abfs.account.name=<your-storage-account-name>.dfs.core.windows.net,
fs.azure.account.key.<your-storage-account-name>.dfs.core.windows.net=<storage-account-access-key>
```

## <a name="mount-the-remote-hdfs-storage"></a><a id="mount"></a> Подключение удаленного хранилища HDFS

Теперь, когда вы задали переменную среды MOUNT_CREDENTIALS для ключей доступа или с помощью OAuth, можно приступать к подключению. Чтобы подключить удаленное хранилище HDFS в Azure Data Lake к локальному хранилищу HDFS в кластере больших данных, выполните указанные ниже действия.

1. Используйте **kubectl** для определения IP-адреса службы конечной точки **controller-svc-external** в кластере больших данных. Найдите параметр **External-IP**.

   ```bash
   kubectl get svc controller-svc-external -n <your-big-data-cluster-name>
   ```

1. Войдите в **azdata**, используя внешний IP-адрес конечной точки контроллера, а также имя и пароль пользователя кластера:

   ```bash
   azdata login -e https://<IP-of-controller-svc-external>:30080
   ```
1. Задайте переменную среды MOUNT_CREDENTIALS (для получения инструкций прокрутите вверх).

1. Подключите удаленное хранилище HDFS в Azure с помощью команды **azdata bdc hdfs mount create**. Замените значения заполнителей, после чего выполните следующую команду:

   ```bash
   azdata bdc hdfs mount create --remote-uri abfs://<blob-container-name>@<storage-account-name>.dfs.core.windows.net/ --mount-path /mounts/<mount-name>
   ```

   > [!NOTE]
   > Команда mount create выполняется асинхронной. Сейчас сообщения об успешном подключении не реализованы. Чтобы проверить состояние подключений, обратитесь к разделу [status](#status).

Если подключение выполнено успешно, вы сможете запрашивать данные HDFS и выполнять задания Spark для их обработки. Данные для вашего кластера больших данных будут отображаться в HDFS в месте, которое задается атрибутом `--mount-path`.

## <a name="get-the-status-of-mounts"></a><a id="status"></a> Получение информации о состоянии подключений

Чтобы просмотреть состояние всех подключений в вашем кластере больших данных, выполните следующую команду:

```bash
azdata bdc hdfs mount status
```

Чтобы просмотреть состояние подключения с заданным путем в HDFS, выполните следующую команду:

```bash
azdata bdc hdfs mount status --mount-path <mount-path-in-hdfs>
```

## <a name="refresh-a-mount"></a>Обновление подключения

В следующем примере выполняется обновление подключения. Это обновление также очистит и кэш подключения.

```bash
azdata bdc hdfs mount refresh --mount-path <mount-path-in-hdfs>
```

## <a name="delete-the-mount"></a><a id="delete"></a> Удаление подключения

Чтобы удалить подключение, выполните команду **azdata bdc hdfs mount delete** и укажите путь к подключению в HDFS:

```bash
azdata bdc hdfs mount delete --mount-path <mount-path-in-hdfs>
```

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] см. в статье [Что такое [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md).
