---
title: Запуск приложений с помощью azdata
titleSuffix: SQL Server Big Data Clusters
description: Запуск приложений с помощью azdata в кластерах больших данных SQL Server 2019.
author: cloudmelon
ms.author: melqin
ms.reviewer: mikeray
ms.metadata: seo-lt-2019
ms.date: 08/16/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: bf1608ed13a6a6de4ff0b2b3191520e07a01205d
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/05/2020
ms.locfileid: "91725017"
---
# <a name="run-apps-with-azdata---sql-server-big-data-clusters"></a>Запуск приложений с помощью azdata — Кластеры больших данных SQL Server

В этой статье описывается запуск приложений в Кластерах больших данных SQL Server.

## <a name="prerequisites"></a>Предварительные требования

- [Кластер больших данных SQL Server 2019](deployment-guidance.md)
- [Служебная программа командной строки azdata](../azdata/install/deploy-install-azdata.md)

## <a name="capabilities"></a>Возможности

В SQL Server 2019 можно создать, удалить, описать, инициализировать, перечислить, запустить и обновить приложение. В следующей таблице описаны команды развертывания приложения, которые можно использовать с **azdata**.

|Get-Help |Описание |
|:---|:---|
|`azdata app describe` | Описание приложения. |
|`azdata app run` | Выполнение приложения. |


В следующих разделах эти команды описаны более подробно.


## <a name="run-an-app"></a>Запуск приложения

Если приложение находится в состоянии `Ready`, его можно использовать, запустив с указанными входными параметрами. Для запуска приложения используйте следующий синтаксис.

```bash
azdata app run --name <app_name> --version <app_version> --inputs <inputs_params>
```

Следующий пример демонстрирует использование команды run.

```bash
azdata app run --name add-app --version v1 --inputs x=1,y=2
```

Если команда run выполнена успешно, вы увидите выходные данные, указанные при создании приложения. Ниже приведен пример выходных данных.

```json
{
  "changedFiles": [],
  "consoleOutput": "",
  "errorMessage": "",
  "outputFiles": {},
  "outputParameters": {
    "result": 3
  },
  "success": true
}
```


## <a name="describe-an-app"></a>Описание приложения.

Команда describe предоставляет подробные сведения о приложении, включая конечную точку в кластере. Обычно она используется разработчиком приложения, чтобы создать приложение с помощью клиента Swagger и использовать веб-службу для взаимодействия с приложением на основе REST. Дополнительные сведения см. в статье [Использование приложений в кластерах больших данных](app-consume.md).

```json
{
  "input_param_defs": [
    {
      "name": "x",
      "type": "int"
    },
    {
      "name": "y",
      "type": "int"
    }
  ],
  "links": {
    "app": "https://10.1.1.3:30080/api/app/add-app/v1",
    "swagger": "https://10.1.1.3:30080/api/app/add-app/v1/swagger.json"
  },
  "name": "add-app",
  "output_param_defs": [
    {
      "name": "result",
      "type": "int"
    }
  ],
  "state": "Ready",
  "version": "v1"
}
```

Дополнительные сведения о том, как интегрировать приложения, развернутые в [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)], в собственные приложения, см. в статье [Использование приложений в кластерах больших данных](app-consume.md). Дополнительные примеры можно просмотреть в наборе [примеров развертывания приложений](https://aka.ms/sql-app-deploy).

Дополнительные сведения о [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] см. в статье [Что такое [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md).