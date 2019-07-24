---
title: Развертывание приложений с помощью аздата
titleSuffix: SQL Server big data clusters
description: Развертывание скрипта Python или R в качестве приложения в кластере больших данных SQL Server 2019 (Предварительная версия).
author: jeroenterheerdt
ms.author: jterh
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 06b76e7eb8eec8db1993ca558a1f57355457c4ad
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419491"
---
# <a name="how-to-deploy-an-app-on-sql-server-big-data-cluster-preview"></a>Развертывание приложения в кластере больших данных SQL Server (Предварительная версия)

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье описывается, как развернуть скрипты R и Python и управлять ими как приложением в кластере SQL Server 2019 больших данных (Предварительная версия).

## <a name="whats-new-and-improved"></a>Новые и улучшенные

- Единая программа командной строки для управления кластером и приложением.
- Упрощенное развертывание приложений, обеспечивающее детальный контроль с помощью файлов спецификаций.
- Поддержка размещения дополнительных типов приложений — SSIS и Млеап (новые в CTP-версии 2,3)
- [Расширение VS Code](app-deployment-extension.md) для управления развертыванием приложений

Приложения развертываются и управляются `azdata` с помощью программы командной строки. В этой статье приведены примеры развертывания приложений из командной строки. Сведения об использовании этого Visual Studio Code см. в разделе [расширение VS Code](app-deployment-extension.md).

Поддерживаются следующие типы приложений:
- Приложения R и Python (функции, модели и приложения)
- Млеап
- Службы SQL Server Integration Services (SSIS)

## <a name="prerequisites"></a>Предварительные требования

- [Кластер больших данных SQL Server 2019](deployment-guidance.md)
- [Служебная программа командной строки аздата](deploy-install-azdata.md)

## <a name="capabilities"></a>Речь

В SQL Server 2019 (Предварительная версия) можно создавать, удалять, описывать, инициализировать, выполнять перечисление и обновлять приложения. В следующей таблице описаны команды развертывания приложения, которые можно использовать с **аздата**.

|Command |Описание |
|:---|:---|
|`azdata login` | Вход в SQL Server кластер больших данных |
|`azdata app create` | Создать приложение. |
|`azdata app delete` | Удаление приложения. |
|`azdata app describe` | Описание приложения. |
|`azdata app init` | Kickstart новая схема приложения. |
|`azdata app list` | Вывод списка приложений. |
|`azdata app run` | Запустить приложение. |
|`azdata app update`| Обновление приложения. |

Справку `--help` по параметру можно получить, как показано в следующем примере:

```bash
azdata app create --help
```

В следующих разделах эти команды описаны более подробно.

## <a name="sign-in"></a>Вход

Прежде чем развертывать приложения или взаимодействовать с ними, сначала войдите в кластер больших данных SQL Server с помощью `azdata login` команды. Укажите внешний IP-адрес `controller-svc-external` службы ( `https://ip-address:30080`например,), а также имя пользователя и пароль для кластера.

```bash
azdata login --controller-endpoint https://<ip-address-of-controller-svc-external>:30080 --controller-username <user-name>
```

## <a name="aks"></a>AKS

При использовании AKS необходимо выполнить следующую команду, чтобы получить IP-адрес `mgmtproxy-svc-external` службы, выполнив эту команду в окне bash или cmd:


```bash
kubectl get svc mgmtproxy-svc-external -n <name of your big data cluster>
```

## <a name="kubeadm-or-minikube"></a>Кубеадм или Minikube

Если вы используете Кубеадм или Minikube, выполните следующую команду, чтобы получить IP-адрес для входа в кластер.

```bash
kubectl get node --selector='node-role.kubernetes.io/master'
```

## <a name="create-an-app"></a>Создание приложения

Чтобы создать приложение, используйте `azdata` `app create` команду. Эти файлы находятся локально на компьютере, на котором создается приложение.

Для создания нового приложения в кластере больших данных используйте следующий синтаксис:

```bash
azdata app create --spec <directory containing spec file>
```

Следующая команда показывает пример того, как может выглядеть эта команда:

```bash
azdata app create --spec ./addpy
```

Предполагается, что приложение хранится в `addpy` папке. Эта папка также должна содержать файл спецификации для приложения с именем `spec.yaml`. Дополнительные сведения `spec.yaml` о файле см. на [странице развертывания приложения](concept-application-deployment.md) .

Чтобы развернуть пример приложения приложения, создайте следующие файлы в каталоге с именем `addpy`:

- `add.py`. Скопируйте в этот файл следующий код Python:
   ```py
   #add.py
   def add(x,y):
        result = x+y
        return result
    result=add(x,y)
   ```
- `spec.yaml`. Скопируйте следующий код в этот файл:
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

Затем выполните следующую команду:

```bash
azdata app create --spec ./addpy
```

Проверить, развернуто ли приложение, можно с помощью команды List:

```bash
azdata app list
```

Если развертывание не завершено, вы увидите, `state` `WaitingforCreate` как показано в следующем примере:

```json
[
  {
    "name": "add-app",
    "state": "WaitingforCreate",
    "version": "v1"
  }
]
```

После успешного развертывания вы увидите `state` `Ready` изменение состояния:

```json
[
  {
    "name": "add-app",
    "state": "Ready",
    "version": "v1"
  }
]
```

## <a name="list-an-app"></a>Список приложений

Вы можете перечислить все приложения, которые были успешно `app list` созданы с помощью команды.

Следующая команда перечисляет все доступные приложения в кластере больших данных:

```bash
azdata app list
```

Если указать имя и версию, будет указано, что конкретное приложение и его состояние (создание или готовность):

```bash
azdata app list --name <app_name> --version <app_version>
```

Эта команда показана в следующем примере:

```bash
azdata app list --name add-app --version v1
```

Должны отобразиться выходные данные, аналогичные приведенным в следующем примере.

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

Если приложение находится в `Ready` состоянии, его можно использовать, запустив его с указанными входными параметрами. Для запуска приложения используйте следующий синтаксис:

```bash
azdata app run --name <app_name> --version <app_version> --inputs <inputs_params>
```

В следующем примере команды демонстрируется команда Run:

```bash
azdata app run --name add-app --version v1 --inputs x=1,y=2
```

Если выполнение прошло успешно, вы должны увидеть выходные данные, как указано при создании приложения. Пример приведен ниже.

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

## <a name="create-an-app-skeleton"></a>Создание каркаса приложения

Команда init обеспечивает формирование шаблонов с соответствующими артефактами, необходимыми для развертывания приложения. Приведенный ниже пример создает Hello. это можно сделать, выполнив следующую команду.

```bash
azdata app init --name hello --version v1 --template python
```

Будет создана папка с именем Hello.  Вы можете `cd` войти в каталог и проверить созданные файлы в папке. Спецификация Spec. YAML определяет приложение, например имя, версию и исходный код. Вы можете изменить спецификацию, чтобы изменить имя, версию, входные и выходные данные.

Ниже приведен пример выходных данных команды init, которая будет отображаться в папке.

```
hello.py
README.md
run-spec.yaml
spec.yaml

```

## <a name="describe-an-app"></a>Описание приложения

Команда описать предоставляет подробные сведения о приложении, включая конечную точку в кластере. Обычно это используется разработчиком приложения для создания приложения с помощью клиента Swagger и использования WebService для взаимодействия с приложением на основе RESTFUL. Дополнительные сведения см. [в статье Использование приложений в кластерах больших данных](big-data-cluster-consume-apps.md) .

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
azdata app delete --name add-app --version v1
```

## <a name="next-steps"></a>Следующие шаги

Узнайте, как интегрировать приложения, развернутые на SQL Server кластеры больших данных в собственных приложениях, для получения дополнительных сведений об [использовании приложений в кластерах больших данных](big-data-cluster-consume-apps.md) . Дополнительные примеры можно также просмотреть на странице [Примеры развертывания приложений](https://aka.ms/sql-app-deploy).

Дополнительные сведения о SQL Server кластерах больших данных см. в разделе [что такое кластеры больших данных SQL Server 2019?](big-data-cluster-overview.md).
