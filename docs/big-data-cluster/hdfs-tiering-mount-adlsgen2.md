---
title: Подключение Azure Data Lake Storage 2-го поколения для распределения по уровням HDFS
titleSuffix: How to mount ADLS Gen2
description: В этой статье объясняется, как настроить уровни HDFS для подключения внешней Azure Data Lake Storage файловой системы к HDFS в кластере SQL Server 2019 больших данных (Предварительная версия).
author: nelgson
ms.author: negust
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d7d8a6dd53452700853dca9774ed0196ed7546fe
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419344"
---
# <a name="how-to-mount-adls-gen2-for-hdfs-tiering-in-a-big-data-cluster"></a>Как подключить ADLS 2-го поколения для уровней HDFS в кластере больших данных

В следующих разделах приводится пример настройки уровня HDFS с помощью Azure Data Lake Storage 2-го поколения источника данных.

## <a name="prerequisites"></a>Предварительные требования

- [Развернутый кластер больших данных](deployment-guidance.md)
- [Инструменты для обработки больших данных](deploy-big-data-tools.md)
  - **аздата**
  - **kubectl**

## <a id="load"></a>Загрузка данных в Azure Data Lake Storage

В следующем разделе описано, как настроить Azure Data Lake Storage 2-го поколения для тестирования уровней HDFS. Если у вас уже есть данные, хранящиеся в Azure Data Lake Storage, можно пропустить этот раздел, чтобы использовать собственные данные.

1. [Создайте учетную запись хранения с возможностями Data Lake Storage 2-го поколения](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-quickstart-create-account).

1. [Создайте контейнер больших двоичных объектов](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-portal) в этой учетной записи хранения для внешних данных.

1. Отправьте файл CSV или Parquet в контейнер. Это внешние данные HDFS, которые будут подключены к HDFS в кластере больших данных.

## <a name="credentials-for-mounting"></a>Учетные данные для подключения

## <a name="use-oauth-credentials-to-mount"></a>Использовать учетные данные OAuth для подключения

Чтобы использовать учетные данные OAuth для подключения, необходимо выполнить следующие действия.

1. Перейдите к [портал Azure](https://portal.azure.com)
1. Перейдите в раздел "службы" в левой области навигации и синхронизируйте часы "Azure Active Directory".
1. С помощью команды "Регистрация приложений" в меню Создайте веб-приложение и следуйте указаниям мастера. **Запомните имя, которое вы создадите здесь**. Необходимо добавить это имя в учетную запись ADLS в качестве полномочного пользователя.
1. После создания веб-приложения перейдите к разделу "ключи" в разделе "Параметры" для приложения.
1. Выберите длительность ключа и нажмите кнопку Сохранить. **Сохраните созданный ключ.**
1.  Вернитесь на страницу регистрации приложений и нажмите кнопку "конечные точки" вверху. **Запишите URL-адрес конечной точки токена**
1. Теперь для OAuth необходимо отметить следующие моменты:

    - Идентификатор приложения веб-приложения, созданного на шаге 3.
    - Ключ, который был только что создан на шаге 5
    - Конечная точка маркера из шага 6

### <a name="adding-the-service-principal-to-your-adls-account"></a>Добавление субъекта-службы в учетную запись ADLS

1. Снова перейдите на портал и откройте учетную запись ADLS и выберите в меню слева пункт Управление доступом (IAM).
1. Выберите "добавить назначение ролей" и найдите имя, созданное в шаг 3 выше (Обратите внимание, что оно не отображается в списке, но будет найдено при поиске полного имени).
1. Теперь добавьте роль "участник данных BLOB-объекта хранилища (Предварительная версия)".

Подождите 5-10 минут перед использованием учетных данных для подключения.

### <a name="set-environment-variable-for-oauth-credentials"></a>Задание переменной среды для учетных данных OAuth

Откройте командную строку на клиентском компьютере, который может получить доступ к кластеру больших данных. Задайте переменную среды в следующем формате: Обратите внимание, что учетные данные должны находиться в списке с разделителями-запятыми. Команда "Set" используется в Windows. Если вы используете Linux, используйте вместо него команду "Export".

   ```text
    set MOUNT_CREDENTIALS=fs.azure.account.auth.type=OAuth,
    fs.azure.account.oauth.provider.type=org.apache.hadoop.fs.azurebfs.oauth2.ClientCredsTokenProvider,
    fs.azure.account.oauth2.client.endpoint=[token endpoint from step6 above],
    fs.azure.account.oauth2.client.id=[<Application ID> from step3 above],
    fs.azure.account.oauth2.client.secret=[<key> from step5 above]
   ```

## <a name="use-access-keys-to-mount"></a>Использование ключей доступа для подключения

Можно также подключить с помощью ключей доступа, которые можно получить для учетной записи ADLS на портал Azure.

 > [!TIP]
   > Дополнительные сведения о том, как найти ключ доступа (`<storage-account-access-key>`) для учетной записи хранения, см. в разделе [Просмотр ключей учетной записи и строки подключения](/azure/storage/common/storage-account-manage#view-account-keys-and-connection-string).

### <a name="set-environment-variable-for-access-key-credentials"></a>Задать переменную среды для учетных данных ключа доступа

1. Откройте командную строку на клиентском компьютере, который может получить доступ к кластеру больших данных.

1. Откройте командную строку на клиентском компьютере, который может получить доступ к кластеру больших данных. Задайте переменную среды в следующем формате: Обратите внимание, что учетные данные должны находиться в списке с разделителями-запятыми. Команда "Set" используется в Windows. Если вы используете Linux, используйте вместо него команду "Export".

   ```text
   set MOUNT_CREDENTIALS=fs.azure.abfs.account.name=<your-storage-account-name>.dfs.core.windows.net,
   fs.azure.account.key.<your-storage-account-name>.dfs.core.windows.net=<storage-account-access-key>
   ```

## <a id="mount"></a>Подключение удаленного хранилища HDFS

Теперь, когда вы установили переменную среды MOUNT_CREDENTIALS для ключей доступа или с помощью OAuth, можно приступить к подключению. Следующие шаги позволяют подключить удаленное хранилище HDFS в Azure Data Lake к локальному хранилищу HDFS кластера больших данных.

1. Используйте **kubectl** , чтобы найти IP-адрес для службы конечной точки **-SVC-External** в кластере больших данных. Найдите параметр **External-IP**.

   ```bash
   kubectl get svc controller-svc-external -n <your-big-data-cluster-name>
   ```

1. Войдите в систему с помощью **аздата** , используя внешний IP-адрес конечной точки контроллера и имя пользователя и пароль кластера:

   ```bash
   azdata login -e https://<IP-of-controller-svc-external>:30080/
   ```
1. Задать переменную среды MOUNT_CREDENTIALS (прокрутка вверх для получения инструкций)

1. Подключите удаленное хранилище HDFS в Azure, используя **хранилище BDC аздата. Создайте пул**. Замените значения заполнителей перед выполнением следующей команды:

   ```bash
   azdata bdc storage-pool mount create --remote-uri abfs://<blob-container-name>@<storage-account-name>.dfs.core.windows.net/ --mount-path /mounts/<mount-name>
   ```

   > [!NOTE]
   > Команда подключения Create является асинхронной. В настоящее время отсутствует сообщение о том, что подключение установлено. См. раздел [Status (состояние](#status) ), чтобы проверить состояние подключений.

Если подключение установлено успешно, вы сможете запросить данные HDFS и выполнить на нем задания Spark. Он будет отображаться в HDFS для кластера больших данных в расположении, указанном параметром `--mount-path`.

## <a id="status"></a>Получение состояния подключений

Чтобы просмотреть состояние всех подключений в кластере больших данных, используйте следующую команду:

```bash
azdata bdc storage-pool mount status
```

Чтобы получить список состояния подключения по указанному пути в HDFS, используйте следующую команду:

```bash
azdata bdc storage-pool mount status --mount-path <mount-path-in-hdfs>
```

## <a name="refresh-a-mount"></a>Обновление подключения

В следующем примере обновляется подключение.

```bash
azdata bdc hdfs mount refresh --mount-path <mount-path-in-hdfs>
```

## <a id="delete"></a>Удаление подключения

Чтобы удалить подключение, используйте команду Delete для подключения к **хранилищу данных аздата BDC** и укажите путь подключения в HDFS:

```bash
azdata bdc storage-pool mount delete --mount-path <mount-path-in-hdfs>
```

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах больших данных SQL Server 2019 см. в статье [что такое кластеры больших данных SQL Server 2019?](big-data-cluster-overview.md).
