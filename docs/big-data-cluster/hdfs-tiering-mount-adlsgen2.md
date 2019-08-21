---
title: Подключение Azure Data Lake Storage 2-го поколения для распределения по уровням HDFS
titleSuffix: How to mount ADLS Gen2
description: В этой статье объясняется, как настроить уровни HDFS для подключения внешней Azure Data Lake Storage файловой системы к HDFS в [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)].
author: nelgson
ms.author: negust
ms.reviewer: mikeray
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 822c10ad41232d213302e4bb5e328449d9f5f764
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2019
ms.locfileid: "69652310"
---
# <a name="how-to-mount-adls-gen2-for-hdfs-tiering-in-a-big-data-cluster"></a>Подключение ADLS 2-го поколения для распределения по уровням HDFS в кластере больших данных

В следующих разделах приводится пример настройки распределения по уровням HDFS для источника данных Azure Data Lake Storage 2-го поколения.

## <a name="prerequisites"></a>Предварительные требования

- [Развернутый кластер больших данных](deployment-guidance.md)
- [Средства работы с большими данными](deploy-big-data-tools.md)
  - **azdata**
  - **kubectl**

## <a id="load"></a> Загрузка данных в Azure Data Lake Storage

В следующем разделе описано, как настроить Azure Data Lake Storage 2-го поколения для тестирования распределения по уровням HDFS. Если у вас уже есть данные, хранящиеся в Azure Data Lake Storage, можно пропустить этот раздел, чтобы использовать собственные данные.

1. [Создайте учетную запись хранения с возможностями Data Lake Storage 2-го поколения](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-quickstart-create-account).

1. [Создайте контейнер BLOB-объектов](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-portal) в этой учетной записи хранения для своих внешних данных.

1. Отправьте файл CSV или Parquet в этот контейнер. Это внешние данные HDFS, которые будут подключены к HDFS в кластере больших данных.

## <a name="credentials-for-mounting"></a>Учетные данные для подключения

## <a name="use-oauth-credentials-to-mount"></a>Использование учетных данных OAuth для подключения

Чтобы использовать учетные данные OAuth для подключения, нужно выполнить следующие действия:

1. Перейдите на [портал Azure](https://portal.azure.com).
1. Перейдите в раздел "Службы" в левой области навигации и выберите "Azure Active Directory".
1. С помощью команды "Регистрация приложений" в меню создайте веб-приложение и следуйте указаниям мастера. **Запишите указанное здесь имя**. Его потребуется добавить в учетную запись ADLS в качестве полномочного пользователя.
1. После создания веб-приложения перейдите к разделу "Ключи" в области "Параметры" для приложения.
1. Выберите длительность ключа и нажмите кнопку "Сохранить". **Сохраните созданный ключ**.
1.  Вернитесь на страницу "Регистрация приложений" и нажмите сверху кнопку "Конечные точки". **Запишите URL-адрес "Конечная точка маркера"** .
1. Теперь вы должны располагать следующими компонентами для OAuth:

    - "Идентификатор приложения" для веб-приложения, созданного в шаге 3.
    - Ключ, созданный в шаге 5.
    - Конечная точка маркера из шага 6.

### <a name="adding-the-service-principal-to-your-adls-account"></a>Добавление субъекта-службы в вашу учетную запись ADLS

1. Снова перейдите на портал, откройте свою учетную запись ADLS и выберите в меню слева пункт "Управление доступом (IAM)".
1. Выберите "Добавление назначения роли" и найдите имя, созданное в шаге 3 выше (обратите внимание, что оно не отображается в списке, но будет найдено при поиске по полному имени).
1. Теперь добавьте роль "Участник для данных больших двоичных объектов хранилища (предварительная версия)".

Подождите 5–10 минут перед использованием учетных данных для подключения.

### <a name="set-environment-variable-for-oauth-credentials"></a>Установка переменной среды для учетных данных OAuth

Откройте командную строку на клиентском компьютере, который может получать доступ к кластеру больших данных. Задайте переменную среды в следующем формате: Обратите внимание, что учетные данные нужно задавать в виде списка с разделителями-запятыми. В Windows используется команда "set". В Linux следует использовать команду "export".

   ```text
    set MOUNT_CREDENTIALS=fs.azure.account.auth.type=OAuth,
    fs.azure.account.oauth.provider.type=org.apache.hadoop.fs.azurebfs.oauth2.ClientCredsTokenProvider,
    fs.azure.account.oauth2.client.endpoint=[token endpoint from step6 above],
    fs.azure.account.oauth2.client.id=[<Application ID> from step3 above],
    fs.azure.account.oauth2.client.secret=[<key> from step5 above]
   ```

## <a name="use-access-keys-to-mount"></a>Использование ключа доступа для подключения

Можно также подключиться с помощью ключей доступа, которые можно получить для своей учетной записи ADLS на портале Azure.

 > [!TIP]
   > Дополнительные сведения о том, как найти ключ доступа (`<storage-account-access-key>`) для своей учетной записи хранения, см. в разделе [Просмотр строки подключения и ключей учетной записи](/azure/storage/common/storage-account-manage#view-account-keys-and-connection-string).

### <a name="set-environment-variable-for-access-key-credentials"></a>Установка переменной среды для учетных данных ключей доступа

1. Откройте командную строку на клиентском компьютере, который может получать доступ к кластеру больших данных.

1. Откройте командную строку на клиентском компьютере, который может получать доступ к кластеру больших данных. Задайте переменную среды в следующем формате. Обратите внимание, что учетные данные нужно задавать в виде списка с разделителями-запятыми. В Windows используется команда "set". В Linux следует использовать команду "export".

   ```text
   set MOUNT_CREDENTIALS=fs.azure.abfs.account.name=<your-storage-account-name>.dfs.core.windows.net,
   fs.azure.account.key.<your-storage-account-name>.dfs.core.windows.net=<storage-account-access-key>
   ```

## <a id="mount"></a> Подключение удаленного хранилища HDFS

Теперь, когда вы задали переменную среды MOUNT_CREDENTIALS для ключей доступа или с помощью OAuth, можно приступать к подключению. Чтобы подключить удаленное хранилище HDFS в Azure Data Lake к локальному хранилищу HDFS в кластере больших данных, выполните указанные ниже действия.

1. Используйте **kubectl** для определения IP-адреса службы конечной точки **controller-svc-external** в кластере больших данных. Найдите параметр **External-IP**.

   ```bash
   kubectl get svc controller-svc-external -n <your-big-data-cluster-name>
   ```

1. Войдите в **azdata**, используя внешний IP-адрес конечной точки контроллера, а также имя и пароль пользователя кластера:

   ```bash
   azdata login -e https://<IP-of-controller-svc-external>:30080/
   ```
1. Задайте переменную среды MOUNT_CREDENTIALS (для получения инструкций прокрутите вверх).

1. Подключите удаленное хранилище HDFS в Azure с помощью **аздата BDC с подключением HDFS Create**. Замените значения заполнителей, после чего выполните следующую команду:

   ```bash
   azdata bdc hdfs mount create --remote-uri abfs://<blob-container-name>@<storage-account-name>.dfs.core.windows.net/ --mount-path /mounts/<mount-name>
   ```

   > [!NOTE]
   > Команда mount create выполняется асинхронной. Сейчас сообщения об успешном подключении не реализованы. Чтобы проверить состояние подключений, обратитесь к разделу [status](#status).

Если подключение выполнено успешно, вы сможете запрашивать данные HDFS и выполнять задания Spark для их обработки. Данные для вашего кластера больших данных будут отображаться в HDFS в месте, которое задается атрибутом `--mount-path`.

## <a id="status"></a> Получение информации о состоянии подключений

Чтобы просмотреть состояние всех подключений в вашем кластере больших данных, выполните следующую команду:

```bash
azdata bdc hdfs mount status
```

Чтобы просмотреть состояние подключения с заданным путем в HDFS, выполните следующую команду:

```bash
azdata bdc hdfs mount status --mount-path <mount-path-in-hdfs>
```

## <a name="refresh-a-mount"></a>Обновление подключения

В следующем примере выполняется обновление подключения.

```bash
azdata bdc hdfs mount refresh --mount-path <mount-path-in-hdfs>
```

## <a id="delete"></a> Удаление подключения

Чтобы удалить подключение, используйте команду **аздата BDC подключить Delete** и укажите путь подключения в HDFS:

```bash
azdata bdc hdfs mount delete --mount-path <mount-path-in-hdfs>
```

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]см. в разделе [что [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]такое?](big-data-cluster-overview.md).
