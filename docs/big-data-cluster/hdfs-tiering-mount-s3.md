---
title: Подключение S3 для распределения по уровням HDFS
titleSuffix: SQL Server big data clusters
description: В этой статье описывается настройка распределения по уровням HDFS для подключения внешней файловой системы S3 к HDFS в кластере больших данных SQL Server 2019 (предварительная версия).
author: nelgson
ms.author: negust
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 28c80d6076f07c8a4f1605149f4b5c730c8349a1
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "68419340"
---
# <a name="how-to-mount-s3-for-hdfs-tiering-in-a-big-data-cluster"></a>Подключение S3 для распределения по уровням HDFS в кластере больших данных

В следующих разделах приводится пример настройки распределения по уровням HDFS для источника данных хранилища S3.

## <a name="prerequisites"></a>предварительные требования

- [Развернутый кластер больших данных](deployment-guidance.md)
- [Средства работы с большими данными](deploy-big-data-tools.md)
  - **azdata**
  - **kubectl**
- Создание и загрузка данных в контейнер S3 
  - Загрузка файлов CSV или Parquet в контейнер S3. Это внешние данные HDFS, которые будут подключены к HDFS в кластере больших данных.

## <a name="access-keys"></a>Ключи доступа

### <a name="set-environment-variable-for-access-key-credentials"></a>Установка переменной среды для учетных данных ключей доступа

Откройте командную строку на клиентском компьютере, который может получать доступ к кластеру больших данных. Задайте переменную среды в следующем формате. Обратите внимание, что учетные данные должны задаваться в списке с разделителями-запятыми. В Windows используется команда "set". В Linux следует использовать команду "export".

   ```text
    set MOUNT_CREDENTIALS=fs.s3a.access.key=<Access Key ID of the key>,
    fs.s3a.secret.key=<Secret Access Key of the key>
   ```

   > [!TIP]
   > Дополнительные сведения о создании ключей доступа S3 см. в разделе [Ключи доступа S3](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys).

## <a id="mount"></a> Подключение удаленного хранилища HDFS

После подготовки файла учетных данных с ключами доступа вы можете начать процесс подключения. Чтобы подключить удаленное хранилище HDFS в S3 к локальному хранилищу HDFS в кластере больших данных, выполните следующие действия.

1. Используйте **kubectl** для определения IP-адреса службы конечной точки **controller-svc-external** в кластере больших данных. Найдите параметр **External-IP**.

   ```bash
   kubectl get svc controller-svc-external -n <your-big-data-cluster-name>
   ```

1. Войдите в **azdata**, используя внешний IP-адрес конечной точки контроллера, а также имя и пароль пользователя кластера:

   ```bash
   azdata login -e https://<IP-of-controller-svc-external>:30080/
   ```
   
1. Задайте переменную среды MOUNT_CREDENTIALS в соответствии с приведенными выше инструкциями.

1. Подключите удаленное хранилище HDFS к Azure с помощью команды **azdata bdc storage-pool mount create**. Замените значения заполнителей, после чего выполните следующую команду:

   ```bash
   azdata bdc storage-pool mount create --remote-uri s3a://<S3 bucket name> --mount-path /mounts/<mount-name>
   ```

   > [!NOTE]
   > Команда mount create выполняется асинхронно. В настоящее время сообщения об успешном подключении не реализованы. Чтобы проверить состояние подключений, ознакомьтесь с разделом [status](#status).

Если подключение выполнено успешно, вы сможете запрашивать данные HDFS и выполнять задания Spark для их обработки. Данные вашего кластера больших данных будут отображаться в HDFS в месте, которое задается атрибутом `--mount-path`.

## <a id="status"></a> Получение информации о состоянии подключений

Чтобы просмотреть состояние всех подключений в вашем кластере больших данных, выполните следующую команду:

```bash
azdata bdc storage-pool mount status
```

Чтобы просмотреть состояние подключения с заданным путем в HDFS, выполните следующую команду:

```bash
azdata bdc storage-pool mount status --mount-path <mount-path-in-hdfs>
```

## <a name="refresh-a-mount"></a>Обновление подключения

В следующем примере выполняется обновление подключения.

```bash
azdata bdc hdfs mount refresh --mount-path <mount-path-in-hdfs>
```

## <a id="delete"></a> Удаление подключения

Чтобы удалить подключение, выполните команду **azdata bdc storage-pool mount delete** и укажите путь к подключению в HDFS:

```bash
azdata bdc storage-pool mount delete --mount-path <mount-path-in-hdfs>
```

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах больших данных SQL Server 2019 см. в [этой статье](big-data-cluster-overview.md).
