---
title: Подключение S3 для распределения по уровням HDFS
titleSuffix: SQL Server big data clusters
description: В этой статье объясняется, как настроить распределение по уровням HDFS для подключения внешней файловой системы S3 к HDFS в кластере SQL Server 2019 больших данных (Предварительная версия).
author: nelgson
ms.author: negust
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 28c80d6076f07c8a4f1605149f4b5c730c8349a1
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419340"
---
# <a name="how-to-mount-s3-for-hdfs-tiering-in-a-big-data-cluster"></a>Как подключить S3 для уровней HDFS в кластере больших данных

В следующих разделах приводится пример настройки уровня HDFS с помощью источника данных хранилища S3.

## <a name="prerequisites"></a>Предварительные требования

- [Развернутый кластер больших данных](deployment-guidance.md)
- [Инструменты для обработки больших данных](deploy-big-data-tools.md)
  - **аздата**
  - **kubectl**
- Создание и передача данных в контейнер S3 
  - Отправьте файлы CSV или Parquet в контейнер S3. Это внешние данные HDFS, которые будут подключены к HDFS в кластере больших данных.

## <a name="access-keys"></a>Ключи доступа

### <a name="set-environment-variable-for-access-key-credentials"></a>Задать переменную среды для учетных данных ключа доступа

Откройте командную строку на клиентском компьютере, который может получить доступ к кластеру больших данных. Задайте переменную среды в следующем формате: Обратите внимание, что учетные данные должны находиться в списке с разделителями-запятыми. Команда "Set" используется в Windows. Если вы используете Linux, используйте вместо него команду "Export".

   ```text
    set MOUNT_CREDENTIALS=fs.s3a.access.key=<Access Key ID of the key>,
    fs.s3a.secret.key=<Secret Access Key of the key>
   ```

   > [!TIP]
   > Дополнительные сведения о создании ключей доступа S3 см. в разделе [ключи доступа S3](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys).

## <a id="mount"></a>Подключение удаленного хранилища HDFS

Теперь, когда вы подготовили файл учетных данных с ключами доступа, можно приступить к подключению. Следующие шаги позволяют подключить удаленное хранилище HDFS в S3 к локальному хранилищу HDFS кластера больших данных.

1. Используйте **kubectl** , чтобы найти IP-адрес для службы конечной точки **-SVC-External** в кластере больших данных. Найдите параметр **External-IP**.

   ```bash
   kubectl get svc controller-svc-external -n <your-big-data-cluster-name>
   ```

1. Войдите в систему с помощью **аздата** , используя внешний IP-адрес конечной точки контроллера и имя пользователя и пароль кластера:

   ```bash
   azdata login -e https://<IP-of-controller-svc-external>:30080/
   ```
   
1. Задайте переменную среды MOUNT_CREDENTIALS, следуя приведенным выше инструкциям.

1. Подключите удаленное хранилище HDFS в Azure, используя **хранилище BDC аздата. Создайте пул**. Замените значения заполнителей перед выполнением следующей команды:

   ```bash
   azdata bdc storage-pool mount create --remote-uri s3a://<S3 bucket name> --mount-path /mounts/<mount-name>
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
