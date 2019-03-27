---
title: Развертывание приложений с помощью mssqlctl
titleSuffix: SQL Server 2019 big data clusters
description: Разверните скрипт Python или R в качестве приложения в кластере SQL Server 2019 больших данных (Предварительная версия).
author: TheBharath
ms.author: bharaths
manager: craigg
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 9666192d667a5a2592ab32f346338d1b9963fa3d
ms.sourcegitcommit: 715683b5fc7a8e28a86be8949a194226b72ac915
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/26/2019
ms.locfileid: "58477659"
---
# <a name="how-to-deploy-an-app-on-sql-server-2019-big-data-cluster-preview"></a>Развертывание приложения в кластере SQL Server 2019 больших данных (Предварительная версия)

В этой статье описывается развертывание и управление ими скрипт R и Python, как приложение в кластере SQL Server 2019 больших данных (Предварительная версия).

## <a name="whats-new-and-improved"></a>Новые и улучшенные

- Одной программы командной строки для управления кластером и приложения.
- Упрощенное развертывание приложений, предоставляя точный контроль через спецификаций файлов.
- Поддерживает размещение типами приложений - служб SSIS и MLeap (новый компонент в CTP-версия 2.3)
- [Расширение VS Code](app-deployment-extension.md) для управления развертыванием приложений

Приложения развертываются и управляются с помощью `mssqlctl` программы командной строки. В этой статье приведены примеры того, как развертывать приложения из командной строки. Чтобы узнать, как использовать это в Visual Studio Code см [расширение VS Code](app-deployment-extension.md).

Поддерживаются следующие типы приложений:
- R и Python приложений (функции, моделей и приложения)
- MLeap обслуживания
- Службы SQL Server Integration Services (SSIS)

## <a name="prerequisites"></a>предварительные требования

- [Кластер SQL Server 2019 больших данных](deployment-guidance.md)
- [Программа командной строки mssqlctl](deploy-install-mssqlctl.md)

## <a name="capabilities"></a>Возможности

В SQL Server 2019 CTP-версии 2.3 (Предварительная версия) можно создавать, удалять, описания, инициализации список, выполнять и обновлять приложения. В следующей таблице описаны команды развертывания приложения, которые можно использовать с **mssqlctl**.

|Command |Описание |
|:---|:---|
|`mssqlctl login` | Войдите в кластер SQL Server больших данных |
|`mssqlctl app create` | Создайте приложение. |
|`mssqlctl app delete` | Для удаления приложения. |
|`mssqlctl app describe` | Описание приложения. |
|`mssqlctl app init` | Kickstart новый скелет приложения. |
|`mssqlctl app list` | Список приложений. |
|`mssqlctl app run` | Запустите приложение. |
|`mssqlctl app update`| Обновите приложение. |

Вы можете получить справку с `--help` параметра, как показано в следующем примере:

```bash
mssqlctl app create --help
```

Эти команды, более подробно в следующих разделах.

## <a name="log-in"></a>Войти

Перед развертыванием или взаимодействия с приложениями, сначала войдите в кластер для обработки больших данных с использованием SQL Server `mssqlctl login` команды. Укажите внешний IP-адрес `endpoint-service-proxy` службы (например: `https://ip-address:30777`), а также имя пользователя и пароль для кластера.

```bash
mssqlctl login -e https://<ip-address-of-endpoint-service-proxy>:30777 -u <user-name> -p <password>
```

## <a name="aks"></a>AKS

Если вы используете AKS, необходимо выполнить следующую команду, чтобы получить IP-адрес `endpoint-service-proxy` службу, выполнив следующую команду в окне bash или cmd:


```bash
kubectl get svc endpoint-service-proxy -n <name of your cluster>
```

## <a name="kubeadm-or-minikube"></a>Kubeadm или Minikube

Если вы используете Kubeadm или Minikube, выполните следующую команду для получения IP-адрес для входа в кластер

```bash
kubectl get node --selector='node-role.kubernetes.io/master'
```

## <a name="create-an-app"></a>Создание приложения

Чтобы создать приложение, используйте `mssqlctl` с `app create` команды. Эти файлы находятся локально на компьютере, который вы создаете приложение из.

Чтобы создать новое приложение в кластере большие данные, используйте следующий синтаксис:

```bash
mssqlctl app create -n <app_name> -v <version_number> --spec <directory containing spec file>
```

Следующая команда является примером как может выглядеть эта команда:

Это предполагает, что у вас есть файл с именем `spec.yaml` в `addpy` папку.
`addpy` Папка содержит `add.py` и `spec.yaml` `spec.yaml` — это файл спецификации для `add.py` приложения.


`add.py` создает следующие приложения python:

```py
#add.py
def add(x,y):
        result = x+y
        return result
result=add(x,y)
```

Следующий сценарий — пример содержимого для `spec.yaml`:

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

Чтобы попробовать сделать это, скопируйте приведенный выше код в два файла в каталоге `addpy` как `add.py` и `spec.yaml` и выполните следующую команду:

```bash
mssqlctl app create --spec ./addpy
```

> [!NOTE]
> `spec.yaml` Файл указывает оба ключевых слова `poolsize` и ряд `replicas`. Количество `replicas` указывает количество копий службы должны быть развернуты. `poolsize` Указывает количество пулов, которые вы хотите создать в одной реплики. Эти параметры оказывают влияние на количество запросов, которые можно обрабатывать развертывания в параллельном режиме. Максимальное количество запросов в один момент времени равен `replicas` раз `poolsize`, т. е. Если у вас есть 5 реплик и 2 пулов в каждой реплике развертывания может обрабатывать 10 запросов в параллельном режиме. См. на рисунке ниже для графическое представление `replicas` и `poolsize`: ![Poolsize и реплик](media/big-data-cluster-create-apps/poolsize-vs-replicas.png)

Вы можете проверить, если приложение развертывается с помощью команды списка:

```bash
mssqlctl app list
```

Если развертывание не будет завершено, вы должны увидеть `state` Показать `WaitingforCreate` как в примере ниже:

```json
[
  {
    "name": "add-app",
    "state": "WaitingforCreate",
    "version": "v1"
  }
]
```

После успешного завершения развертывания, вы увидите `state` измените `Ready` состояния:

```json
[
  {
    "name": "add-app",
    "state": "Ready",
    "version": "v1"
  }
]
```

## <a name="list-an-app"></a>Отобразить список приложений

Вы можете вывести список любых приложений, созданных с помощью `app list` команды.

Следующая команда перечисляет все доступные приложения в кластере большие данные:

```bash
mssqlctl app list
```

Если указать имя и версия, в ней этого конкретного приложения и его состояние ("Создание" или "Готово"):

```bash
mssqlctl app list --name <app_name> --version <app_version>
```

В следующем примере демонстрируется эта команда:

```bash
mssqlctl app list --name add-app --version v1
```

Вы должны увидеть результат, аналогичный приведенному ниже:

```json
[
  {
    "name": "add-app",
    "state": "Ready",
    "version": "v1"
  }
]
```

## <a name="run-an-app"></a>Запуск приложения

Если приложение находится в `Ready` состоянии, его можно использовать, запустив его с указанным входные параметры. Для запуска приложений, используйте следующий синтаксис:

```bash
mssqlctl app run --name <app_name> --version <app_version> --inputs <inputs_params>
```

Например, следующая команда демонстрирует выполнения команды:

```bash
mssqlctl app run --name add-app --version v1 --inputs x=1,y=2
```

Если выполнение прошло успешно, вы увидите выходные данные, указанные при создании приложения. Пример приведен ниже.

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

## <a name="create-an-app-skeleton"></a>Создайте схему приложения

Команда init предоставляет каркас с соответствующие артефакты, необходимые для развертывания приложения. В приведенном ниже примере создает hello, это можно сделать, выполнив следующую команду.

```bash
mssqlctl app init --name hello --version v1 --template python
```

Это создаст папку с именем hello.  Вы можете `cd` в каталог и проверять созданные файлы в папке. Spec.yaml определяет приложения, такие как имя, версию и исходного кода. Вы можете изменить спецификации, чтобы изменить имя, версию, входные и выходные данные.

Ниже приведен пример выходных данных команды init, которое будет отображаться в папке

```
hello.py
README.md
run-spec.yaml
spec.yaml

```

## <a name="describe-an-app"></a>Описание приложения

Команда describe содержит подробные сведения о приложении, включая конечную точку в кластере. Обычно это используется, разработчик приложения для создания приложения с помощью клиента swagger и использование веб-службы для взаимодействия с приложением в RESTful-образом. См. в разделе [использовать приложения, в кластерах больших данных](big-data-cluster-consume-apps.md) Дополнительные сведения.

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
    "app": "https://10.1.1.3:30777/api/app/add-app/v1",
    "swagger": "https://10.1.1.3:30777/api/app/add-app/v1/swagger.json"
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

## <a name="delete-an-app"></a>Удаление приложения

Чтобы удалить приложение из кластера больших данных, используйте следующий синтаксис:

```bash
mssqlctl app delete --name add-app --version v1
```

## <a name="next-steps"></a>Следующие шаги

Узнайте, как интегрировать приложения, развернутые на сервере SQL Server, больших данных кластеров под управлением Windows в собственных приложениях в [использовать приложения, в кластерах больших данных](big-data-cluster-consume-apps.md) Дополнительные сведения. Вы можете также проверить Дополнительные примеры по [примеры развертывания приложений](https://aka.ms/sql-app-deploy).

Дополнительные сведения о больших данных кластеров SQL Server, см. в разделе [Каковы кластеров SQL Server 2019 больших данных?](big-data-cluster-overview.md).
