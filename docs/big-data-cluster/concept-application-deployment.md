---
title: Что такое развертывание приложения?
titleSuffix: SQL Server 2019 big data clusters
description: В этой статье описывается развертывание приложения в кластере SQL Server 2019 больших данных (Предварительная версия).
author: jterh
ms.author: jroth
manager: craigg
ms.date: 03/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 44e0be15c9b9cc3abb8af3e8f2e7fc8049d385df
ms.sourcegitcommit: 323d2ea9cb812c688cfb7918ab651cce3246c296
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58872371"
---
# <a name="what-is-application-deployment-on-a-sql-server-2019-big-data-cluster"></a>Что такое развертывание приложения в кластере SQL Server 2019 больших данных?

Развертывание приложений позволяет развертывать приложения в кластере больших данных, предоставляя интерфейсы для создания, управления и запуска приложений. Приложения, развернутые в кластере большие данные преимущества вычислительных мощностей кластера и могут обращаться к данным, которая доступна в кластере. Это повышает масштабируемость и производительность приложений, при управлении приложениями, где находятся данные.
Архитектура и функциональные возможности развертывания приложений в следующих разделах.

## <a name="application-deployment-architecture"></a>Архитектура развертывания приложения

Развертывание приложения состоит из контроллера и обработчики среды выполнения приложения. При создании приложения, файл спецификации (`spec.yaml`) предоставляется. Это `spec.yaml` файл содержит все, что контроллер должен знать, для успешного развертывания приложения. Ниже приведен пример содержимого для `spec.yaml`:

```yaml
#spec.yaml
name: add-app #name of your python script
version: v1  #version of the app
runtime: Python #the language this app uses (R or Python)
src: ./add.py #full path to the location of the app
entrypoint: add #the function that will be called upon execution
replicas: 1  #number of replicas needed
poolsize: 1  #the pool size that you need your app to scale
inputs:  #input parameters that the app expects and the type
  x: int
  y: int
output: #output parameter the app expects and the type
  result: int
```

Контроллер проверяет `runtime` указано в `spec.yaml` файла и вызывает соответствующий обработчик среды выполнения. Обработчик среды выполнения создает приложение. Во-первых Kubernetes ReplicaSet будет создано, содержащее один или несколько модулей, каждый из которых содержит приложение для развертывания. Количество модулей определяется `replicas` набор параметров `spec.yaml` файл для приложения. Каждый модуль может иметь одно из дополнительные пулы. Количество пулов определяется `poolsize` набор параметров `spec.yaml` файл.

Эти параметры оказывают влияние на количество запросов, которые можно обрабатывать развертывания в параллельном режиме. Максимальное количество запросов в один момент времени — equals для `replicas` раз `poolsize`. Если у вас есть 5 реплик и 2 пулов в каждой реплике развертывания может обрабатывать 10 запросов в параллельном режиме. См. на рисунке ниже для графическое представление `replicas` и `poolsize`:

![Poolsize и реплик](media/big-data-cluster-create-apps/poolsize-vs-replicas.png)

После того как был создан набор реплик и начали модулей POD, задания cron создается, если `schedule` было задано в `spec.yaml` файл. Наконец, создается служба Kubernetes, можно использовать для управления и запустите приложение (см. ниже).

При выполнении приложения, службы Kubernetes прокси приложения, запросы к реплики и возвращает результаты.

## <a name="how-to-work-with-application-deployment"></a>Как работать с развертыванием приложения

Приведены два основных интерфейса для развертывания приложения. 
- [Интерфейс командной строки `mssqlctl`](big-data-cluster-create-apps.md)
- [Расширение Visual Studio Code и Azure Data Studio](app-deployment-extension.md)

Можно также для приложения должна выполняться с помощью веб-службу RESTful. Дополнительные сведения см. в разделе [использовать приложения, в кластерах больших данных](big-data-cluster-consume-apps.md).

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о способах создания и запуска приложений больших данных в кластерах SQL Server, см. в следующих:

- [Развертывание приложений с помощью mssqlctl](big-data-cluster-create-apps.md)
- [Развертывание приложения с помощью расширения развертывания приложения](app-deployment-extension.md)
- [Использование приложений в кластерах больших данных](big-data-cluster-consume-apps.md)

Дополнительные сведения о кластерах больших данных SQL Server, см. в разделе приведены общие:

- [Что такое кластеры SQL Server 2019 больших данных?](big-data-cluster-overview.md)
