---
title: Что такое развертывание приложений?
titleSuffix: SQL Server 2019 big data clusters
description: В этой статье описывается развертывание приложений в кластере больших данных SQL Server 2019 (Предварительная версия).
author: jeroenterheerdt
ms.author: jterh
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d8cc44862af21c54bdbd0e4adbb35db912c3f7c9
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419405"
---
# <a name="what-is-application-deployment-on-a-sql-server-2019-big-data-cluster"></a>Что такое развертывание приложений в кластере больших данных SQL Server 2019?

Развертывание приложений позволяет развертывать приложения в кластере больших данных, предоставляя интерфейсы для создания, управления и запуска приложений. Приложения, развернутые в кластере больших данных, получают преимущество от вычислительных возможностей кластера и имеют доступ к данным, доступным в кластере. Это повышает масштабируемость и производительность приложений, а также Управление приложениями, в которых находятся данные.
В следующих разделах описывается архитектура и функциональные возможности развертывания приложений.

## <a name="application-deployment-architecture"></a>Архитектура развертывания приложений

Развертывание приложения состоит из обработчиков контроллера и среды выполнения приложений. При создании приложения предоставляется файл спецификации (`spec.yaml`). Этот `spec.yaml` файл содержит все необходимые контроллеру сведения для успешного развертывания приложения. Ниже приведен пример содержимого для `spec.yaml`:

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

Контроллер проверяет `runtime` указанный `spec.yaml` в файле и вызывает соответствующий обработчик среды выполнения. Обработчик среды выполнения создает приложение. Во-первых, создается набор реплик Kubernetes, содержащий один или несколько модулей Pod, каждый из которых содержит приложение для развертывания. Число модулей Pod определяется `replicas` параметром, заданным `spec.yaml` в файле для приложения. Каждый модуль может иметь один или несколько пулов. Количество пулов определяется `poolsize` параметром, заданным `spec.yaml` в файле.

Эти параметры влияют на количество запросов, которые может параллельно развертывать. Максимальное количество запросов в одном заданном времени `replicas` равно времени. `poolsize` При наличии 5 реплик и 2 пулов на одну реплику развертывание может параллельно выполнять 10 запросов. Графическое представление `replicas` и `poolsize`см. на рисунке ниже.

![Пулсизе и реплики](media/big-data-cluster-create-apps/poolsize-vs-replicas.png)

После создания набора реплик и запуска модулей Pod создается задание cron, если `schedule` оно было задано `spec.yaml` в файле. Наконец, создается служба Kubernetes, которая может использоваться для управления и запуска приложения (см. ниже).

При выполнении приложения служба Kubernetes для приложения создает прокси-сервер для запросов к реплике и возвращает результаты.

## <a name="how-to-work-with-application-deployment"></a>Работа с развертыванием приложений

Два основных интерфейса для развертывания приложений: 
- [Интерфейс командной строки`azdata`](big-data-cluster-create-apps.md)
- [Расширение Visual Studio Code и Azure Data Studio](app-deployment-extension.md)

Кроме того, приложение можно выполнять с помощью веб-службы RESTFUL. Дополнительные сведения см. [в статье Использование приложений в кластерах больших данных](big-data-cluster-consume-apps.md).

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о создании и запуске приложений на кластерах больших данных SQL Server см. в следующих статьях:

- [Развертывание приложений с помощью аздата](big-data-cluster-create-apps.md)
- [Развертывание приложений с помощью расширения развертывания приложения](app-deployment-extension.md)
- [Использование приложений в кластерах больших данных](big-data-cluster-consume-apps.md)

Дополнительные сведения о SQL Server кластерах больших данных см. в следующих обзорах:

- [Что такое SQL Server 2019 кластеры больших данных?](big-data-cluster-overview.md)
