---
title: Подключение Azure Data Lake Storage 2-го поколения для распределения по уровням HDFS
titleSuffix: How to mount ADLS Gen2
description: В этой статье описывается настройка HDFS, распределение по уровням для монтажа внешней системы хранилище Azure Data Lake файл в HDFS в кластере SQL Server 2019 больших данных (Предварительная версия).
author: nelgson
ms.author: negust
ms.reviewer: mikeray
manager: jroth
ms.date: 06/27/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 94835b3ae041aa721e915bb5399737b35c52799f
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67728783"
---
# <a name="how-to-mount-adls-gen2-for-hdfs-tiering-in-a-big-data-cluster"></a>Как Gen2 ADLS подключения для HDFS, распределение по уровням в кластере больших данных

Следующие разделы содержат пример, демонстрирующий настройку HDFS, распределение по уровням с источником данных Gen2 хранилища Озера данных Azure.

## <a name="prerequisites"></a>предварительные требования

- [Развернутые больших данных кластера](deployment-guidance.md)
- [Средства работы с большими данными](deploy-big-data-tools.md)
  - **mssqlctl**
  - **kubectl**

## <a id="load"></a> Загрузка данных в хранилище Azure Data Lake

Следующий раздел описывает способы настройки Gen2 хранилища Озера данных Azure для тестирования HDFS распределение по уровням. Если у вас уже есть данные, хранящиеся в хранилище Azure Data Lake, можно пропустить этот раздел, чтобы использовать собственные данные.

1. [Создание учетной записи хранения с помощью возможности Gen2 хранилища Озера данных](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-quickstart-create-account).

1. [Создайте контейнер больших двоичных объектов](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-portal) данной учетной записи хранения для внешних данных.

1. Отправьте файл CSV или Parquet в контейнер. Это внешние данные HDFS, который будет подключен к HDFS в кластере больших данных.

## <a name="credentials-for-mounting"></a>Учетные данные для подключения

## <a name="use-oauth-credentials-to-mount"></a>Используйте учетные данные OAuth для подключения

Чтобы использовать учетные данные OAuth для подключения, необходимо выполнить следующие действия:

1. Перейдите к [портала Azure](https://portal.azure.com)
1. Перейдите к «службы» в левой области навигации, а также время на «Azure Active Directory»
1. С помощью «Регистрация приложений» в меню, создание «веб-приложение и следуйте подсказкам мастера. **Запомните название, созданный здесь**. Необходимо добавить это имя учетной записи ADLS как авторизованного пользователя.
1. После создания веб-приложение, перейдите к «ключи» в разделе «параметры» для приложения.
1. Выберите срок действия ключа и щелкните Сохранить. **Сохраните созданный ключ.**
1.  Вернитесь на страницу регистрации приложений и нажмите кнопку «Конечные точки» вверху. **Запишите URL-адрес «Конечная точка маркера»**
1. Теперь у вас взяли для OAuth следующее:

    - «Идентификатор приложения» веб-приложения, созданный выше на шаге 3
    - Ключ, который вы только что создан на шаге 5
    - Конечная точка маркера из шага 6

### <a name="adding-the-service-principal-to-your-adls-account"></a>Добавление субъекта-службы для учетной записи ADLS

1. Опять же, перейдите на портал и откройте учетную запись ADLS и выберите элемент управления доступом (IAM) в меню слева.
1. Выберите «Добавить назначение ролей» и поиск по имени, созданную из шага 3 выше (Обратите внимание, что он не отображается в списке, но будет найдено при поиске для полного имени).
1. Теперь добавьте «хранилища BLOB-объектов данных (Предварительная версия)» роль "участник".

Подождите 5 – 10 минут, прежде чем использовать учетные данные для подключения

### <a name="set-environment-variable-for-oauth-credentials"></a>Задайте учетные данные OAuth в переменной среды

Откройте командную строку на клиентском компьютере с доступом к кластеру больших данных. Задайте переменную среды, используя следующий формат: Обратите внимание, что учетные данные должны быть в разделенном запятыми списке. Команда «set» используется в Windows. Если вы используете Linux, затем используйте «export».

   ```text
    set MOUNT_CREDENTIALS=fs.azure.account.auth.type=OAuth,
    fs.azure.account.oauth.provider.type=org.apache.hadoop.fs.azurebfs.oauth2.ClientCredsTokenProvider,
    fs.azure.account.oauth2.client.endpoint=[token endpoint from step6 above],
    fs.azure.account.oauth2.client.id=[<Application ID> from step3 above],
    fs.azure.account.oauth2.client.secret=[<key> from step5 above]
   ```

## <a name="use-access-keys-to-mount"></a>Используйте ключи доступа для подключения

Кроме того, можно подключить с помощью клавиши доступа, которые можно получить для учетной записи ADLS на портале Azure.

 > [!TIP]
   > Дополнительные сведения о том, как найти ключ доступа (`<storage-account-access-key>`) для учетной записи хранения, см. в разделе [просматривать ключи учетной записи и строку подключения](/azure/storage/common/storage-account-manage#view-account-keys-and-connection-string).

### <a name="set-environment-variable-for-access-key-credentials"></a>Задайте учетные данные ключа доступа в переменной среды

1. Откройте командную строку на клиентском компьютере с доступом к кластеру больших данных.

1. Откройте командную строку на клиентском компьютере с доступом к кластеру больших данных. Задайте переменную среды, используя следующий формат. Обратите внимание, что учетные данные должны быть в разделенном запятыми списке. Команда «set» используется в Windows. Если вы используете Linux, затем используйте «export».

   ```text
   set MOUNT_CREDENTIALS=fs.azure.abfs.account.name=<your-storage-account-name>.dfs.core.windows.net,
   fs.azure.account.key.<your-storage-account-name>.dfs.core.windows.net=<storage-account-access-key>
   ```

## <a id="mount"></a> Подключение удаленного хранилища HDFS

Теперь, когда вы задали переменную среды MOUNT_CREDENTIALS ключи доступа или с помощью OAuth, можно начать подключение. Следующие действия подключить внешнее хранилище HDFS в Azure Data Lake в локальном хранилище HDFS кластера больших данных.

1. Используйте **kubectl** найти IP-адрес для конечной точки **контроллера svc-external** службы в кластере больших данных. Найдите **внешний IP-** .

   ```bash
   kubectl get svc controller-svc-external -n <your-big-data-cluster-name>
   ```

1. Входа в систему **mssqlctl** с помощью внешний IP-адрес конечной точки контроллера с помощью имени пользователя кластера и пароль:

   ```bash
   mssqlctl login -e https://<IP-of-controller-svc-external>:30080/
   ```
1. Задание переменной среды MOUNT_CREDENTIALS (прокрутки для использования инструкции)

1. Подключение удаленного хранилища HDFS в Azure с помощью **создать подключения пула носителей bdc mssqlctl**. Замените значения заполнителей перед выполнением следующей команды:

   ```bash
   mssqlctl bdc storage-pool mount create --remote-uri abfs://<blob-container-name>@<storage-account-name>.dfs.core.windows.net/ --mount-path /mounts/<mount-name>
   ```

   > [!NOTE]
   > Подключения «создать» является асинхронным. В настоящее время отсутствуют сообщения, указывающее, успешно ли выполнено присоединение. См. в разделе [состояние](#status) раздела, чтобы проверить состояние вашей подключение.

В случае если успешно, можно запросить данные HDFS и выполнения заданий Spark на ее основе. Он будет отображаться в HDFS для кластера больших данных в расположении, заданном параметром `--mount-path`.

## <a id="status"></a> Получение состояния подключение

Чтобы получить список состояние всех подключение кластера больших данных, используйте следующую команду:

```bash
mssqlctl bdc storage-pool mount status
```

Чтобы получить список состояние подключения в указанную папку в файловой системе HDFS, используйте следующую команду:

```bash
mssqlctl bdc storage-pool mount status --mount-path <mount-path-in-hdfs>
```

## <a id="delete"></a> Удаление подключения

Чтобы удалить подключение, используйте **mssqlctl bdc пула носителей подключения delete** команды и укажите путь подключения в HDFS:

```bash
mssqlctl bdc storage-pool mount delete --mount-path <mount-path-in-hdfs>
```

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах SQL Server 2019 большие данные см. в разделе [Каковы кластеров SQL Server 2019 больших данных?](big-data-cluster-overview.md).
