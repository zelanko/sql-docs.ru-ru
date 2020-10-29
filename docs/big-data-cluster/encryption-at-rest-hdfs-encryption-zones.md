---
title: Рекомендации по использованию зон шифрования HDFS в Кластерах больших данных SQL Server
titleSuffix: SQL Server big data clusters
description: В этой статье показано, как использовать функцию зон шифрования HDFS в BDC SQL Server.
author: DaniBunny
ms.author: dacoelho
ms.reviewer: mihaelab
ms.date: 10/19/2020
ms.topic: tutorial
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 904b07913a63e226e5e45876f2fc520226411223
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2020
ms.locfileid: "92199588"
---
# <a name="sql-server-big-data-clusters-hdfs-encryption-zones-usage-guide"></a>Рекомендации по использованию зон шифрования HDFS в Кластерах больших данных SQL Server

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

В этом руководстве показано, как использовать функции шифрования неактивных данных Кластеров больших данных SQL Server для шифрования папок HDFS с помощью зон шифрования.

Обратите внимание, что уже подключенная зона шифрования по умолчанию __```/securelake```__ готова к использованию. Она создана с помощью созданного системой 256-битного ключа с именем __securelakekey__ . Этот ключ можно использовать для создания дополнительных зон шифрования.

## <a name="prerequisites"></a><a id="prereqs"></a> Предварительные требования

- [Кластер больших данных SQL Server CU8 +](release-notes-big-data-cluster.md) с интеграцией Active Directory.
- Пользователь с правами администратора.

## <a name="login-into-the-name-node"></a>Вход в узел имени

Чтобы выполнить вход в кластер, используйте [инструкции по подключению Active Directory](active-directory-connect.md). Войдите в namenode (nmnode-0-0), чтобы выдать команды для выполнения ключей и шифрования зон.

   ```console
   kubectl exec -it -c hadoop -n <cluster_namespace> nmnode-0-0 -- /bin/bash
   ```

## <a name="create-an-encryption-zone-using-the-provided-system-managed-key"></a>Создание зоны шифрования с помощью предоставленного системой управляемого ключа

1. Создание папки HDFS

   ```console
   hdfs dfs -mkdir -p /user/zone/folder
   ```

1. Выдайте команду на создание зоны шифрования, чтобы зашифровать папку с помощью ключа __securelakekey__ .

   ```console
   hdfs crypto -createZone -keyName securelakekey -path /user/zone/folder
   ```

## <a name="create-a-custom-new-key-and-encryption-zone"></a>Создание нового ключа пользователя и зоны шифрования

1. Используйте следующий шаблон для создания 256-битного ключа.

   ```console
   kinit hdfs
   hadoop key create mydatalakekey -size 256
   ```

1. Создайте и зашифруйте новый путь HDFS с помощью ключа пользователя.

   ```console
   hdfs dfs -mkdir -p /user/mydatalake
   hdfs crypto -createZone -keyName mydatalakekey -path /user/mydatalake
   ```
