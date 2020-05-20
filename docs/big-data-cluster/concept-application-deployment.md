---
title: Что такое развертывание приложения
titleSuffix: SQL Server Big Data Clusters
description: В этой статье описывается развертывание приложения в кластере больших данных для SQL Server 2019.
author: jeroenterheerdt
ms.author: jterh
ms.reviewer: mikeray
ms.metadata: seo-lt-2019
ms.date: 12/13/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 4b647ab4d03d110ce303388a8b62461f28033b6c
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "76831570"
---
# <a name="what-is-application-deployment-on-a-big-data-cluster"></a>Развертывание приложения в кластере больших данных

Развертывание приложения позволяет развертывать приложения в кластере больших данных, предоставляя интерфейсы для создания и выполнения приложений, а также управления ими. Приложения, развертываемые в кластере больших данных, могут использовать его вычислительные возможности и обращаться к размещенным в нем данным. Это повышает масштабируемость и производительность приложений, а также позволяет управлять ими в месте размещения данных. Поддерживаемые среды выполнения приложений в Кластерах больших данных SQL Server: R, Python, SSIS, MLeap.

В следующих разделах описываются архитектура и функциональные возможности развертывания приложения.

## <a name="application-deployment-architecture"></a>Архитектура развертывания приложения

Развертывание приложения состоит из контроллера и обработчиков среды выполнения приложений. При создании приложения предоставляется файл спецификации (`spec.yaml`). Этот файл `spec.yaml` содержит все сведения, которые нужны контроллеру для успешного развертывания приложения. Ниже приведен пример содержимого файла `spec.yaml`.

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

Контроллер проверяет элемент `runtime` в файле `spec.yaml` и вызывает соответствующий обработчик среды выполнения. Обработчик среды выполнения создает приложение. Во-первых, создается объект ReplicaSet Kubernetes, содержащий один или несколько объектов pod, каждый из которых содержит развертываемое приложение. Количество объектов pod определяется параметром `replicas`, указанным в файле `spec.yaml` для приложения. Каждый объект pod может иметь один или несколько пулов. Количество пулов определяется параметром `poolsize`, указанным в файле `spec.yaml`.

Эти параметры влияют на количество запросов, которые могут обрабатываться параллельно. Максимальное количество запросов в определенный момент времени равно значению `replicas`, умноженному на `poolsize`. Если имеется 5 реплик с двумя пулами в каждой, параллельно могут обрабатываться 10 запросов. Графическое представление параметров `replicas` и `poolsize` см. на рисунке ниже.

![Poolsize и replicas](media/big-data-cluster-create-apps/poolsize-vs-replicas.png)

После создания объекта ReplicaSet и запуска пулов создается задание cron, если в файле `spec.yaml` был задан параметр `schedule`. Наконец, создается служба Kubernetes, которую можно использовать для управления приложением и его запуска (см. ниже).

При выполнении приложения служба Kubernetes передает запросы в реплику и возвращает результаты.

## <a name="how-to-work-with-application-deployment"></a>Работа с развертыванием приложения

Развертывание приложения имеет два основных интерфейса: 
- [интерфейс командной строки `azdata`;](big-data-cluster-create-apps.md)
- [расширение для Visual Studio Code и Azure Data Studio.](app-deployment-extension.md)

Приложение может также выполняться с помощью веб-службы RESTful. Дополнительные сведения см. в статье [Использование приложений в кластерах больших данных](big-data-cluster-consume-apps.md).

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о создании и выполнении приложений в [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] см. в следующих статьях:

- [Развертывание приложений с помощью azdata](big-data-cluster-create-apps.md)
- [Развертывание приложений с помощью расширения "Развертывание приложения"](app-deployment-extension.md)
- [Использование приложений в кластерах больших данных](big-data-cluster-consume-apps.md)

Дополнительные сведения о [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] см. в следующем обзоре:

- [Что такое [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md)
