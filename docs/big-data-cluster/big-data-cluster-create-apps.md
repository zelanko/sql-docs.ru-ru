---
title: Развертывание приложений с помощью azdata
titleSuffix: SQL Server big data clusters
description: Развертывание скрипта Python или R как приложения в [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)].
author: jeroenterheerdt
ms.author: jterh
ms.reviewer: mikeray
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 1253863bcd2e1da804480a3e1d0e628024b0798b
ms.sourcegitcommit: b4ad3182aa99f9cbfd15f4c3f910317d6128a2e5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/06/2019
ms.locfileid: "73706700"
---
# <a name="how-to-deploy-an-app-on-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd"></a>Развертывание приложения в [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье описывается, как развернуть скрипт Python или R и управлять им как приложением в кластере больших данных SQL Server 2019.

## <a name="whats-new-and-improved"></a>Новые возможности и усовершенствования

- Единая служебная программа командной строки для управления кластером и приложением.
- Упрощенное развертывание приложений, обеспечивающее детальный контроль с помощью файлов спецификаций.
- Поддержка размещения дополнительных типов приложений — SSIS и MLeap.
- [Расширение Visual Studio Code](app-deployment-extension.md) для управления развертыванием приложений.

Для развертывания приложений и управления ими используется служебная программа командной строки `azdata`. В этой статье приведены примеры развертывания приложений из командной строки. Сведения об использовании этой функции в Visual Studio Code см. в разделе [Расширение Visual Studio Code](app-deployment-extension.md).

Поддерживаются следующие типы приложений.
- Приложения R и Python (функции, модели и приложения)
- MLeap Serving
- Службы SQL Server Integration Services (SSIS)

## <a name="prerequisites"></a>предварительные требования

- [Кластер больших данных SQL Server 2019](deployment-guidance.md)
- [Служебная программа командной строки azdata](deploy-install-azdata.md)

## <a name="capabilities"></a>Возможности

В SQL Server 2019 можно создать, удалить, описать, инициализировать, перечислить, запустить и обновить приложение. В следующей таблице описаны команды развертывания приложения, которые можно использовать с **azdata**.

|Command |Описание |
|:---|:---|
|`azdata login` | Вход в кластер больших данных SQL Server. |
|`azdata app create` | Создание приложения. |
|`azdata app delete` | Удаление приложения. |
|`azdata app describe` | Описание приложения. |
|`azdata app init` | Быстрое создание основы нового приложения. |
|`azdata app list` | Вывод списка приложений. |
|`azdata app run` | Выполнение приложения. |
|`azdata app update`| Обновление приложения. |

Справку по параметру `--help` можно получить, как показано в следующем примере.

```bash
azdata app create --help
```

В следующих разделах эти команды описаны более подробно.

## <a name="sign-in"></a>Вход

Прежде чем развертывать приложения или взаимодействовать с ними, сначала войдите в кластер больших данных SQL Server с помощью команды `azdata login`. Укажите внешний IP-адрес службы `controller-svc-external` (например, `https://ip-address:30080`), а также имя пользователя и пароль для кластера.

```bash
azdata login --controller-endpoint https://<ip-address-of-controller-svc-external>:30080 --controller-username <user-name>
```

## <a name="aks"></a>AKS

При использовании AKS нужно выполнить следующую команду в bash или окне cmd, чтобы получить IP-адрес службы `controller-svc-external`.


```bash
kubectl get svc controller-svc-external -n <name of your big data cluster>
```

## <a name="kubernetes-clusters-created-with-kubeadm"></a>Кластеры Kubernetes, созданные с помощью kubeadm

Чтобы получить IP-адрес для входа в кластер, выполните следующую команду.

```bash
kubectl get node --selector='node-role.kubernetes.io/master'
```

## <a name="create-an-app"></a>Создание приложения

Чтобы создать приложение, используйте `azdata` с командой `app create`. Эти файлы располагаются локально на компьютере, где вы создаете приложение.

Чтобы создать приложение в кластере больших данных, используйте следующий синтаксис.

```bash
azdata app create --spec <directory containing spec file>
```

Ниже показан пример того, как может выглядеть эта команда.

```bash
azdata app create --spec ./addpy
```

Предполагается, что ваше приложение хранится в папке `addpy`. Эта папка также должна содержать файл спецификации для приложения — `spec.yaml`. Дополнительные сведения о файле `spec.yaml` см. на [странице "Развертывание приложений"](concept-application-deployment.md).

Чтобы развернуть этот пример приложения, создайте следующие файлы в каталоге с именем `addpy`.

- `add.py`. Скопируйте в этот файл следующий код Python.
   ```py
   #add.py
  def add(x, y):
    result = x+y
    return result
  result=add(x,y)
   ```
- `spec.yaml`. Скопируйте в этот файл следующий код.
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

Затем выполните следующую команду.

```bash
azdata app create --spec ./addpy
```

Проверить, развернуто ли приложение, можно с помощью команды list.

```bash
azdata app list
```

Если развертывание не завершено, в `state` отображается `WaitingforCreate`, как показано в следующем примере.

```json
[
  {
    "name": "add-app",
    "state": "WaitingforCreate",
    "version": "v1"
  }
]
```

После успешного развертывания состояние `state` должно изменить на `Ready`.

```json
[
  {
    "name": "add-app",
    "state": "Ready",
    "version": "v1"
  }
]
```

## <a name="list-an-app"></a>Перечисление приложения

Вы можете перечислить любые приложения, которые были успешно созданы с помощью команды `app list`.

Следующая команда перечисляет все доступные приложения в кластере больших данных.

```bash
azdata app list
```

Если указать имя и версию, она перечисляет конкретное приложение и его состояние (создание или готовность).

```bash
azdata app list --name <app_name> --version <app_version>
```

Следующий пример демонстрирует использование этой команды.

```bash
azdata app list --name add-app --version v1
```

Выходные данные должны соответствовать следующему примеру.

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

Если приложение находится в состоянии `Ready`, его можно использовать, запустив с указанными входными параметрами. Для запуска приложения используйте следующий синтаксис.

```bash
azdata app run --name <app_name> --version <app_version> --inputs <inputs_params>
```

Следующий пример демонстрирует использование команды run.

```bash
azdata app run --name add-app --version v1 --inputs x=1,y=2
```

Если команда run выполнена успешно, вы увидите выходные данные, указанные при создании приложения. Пример приведен ниже.

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

## <a name="create-an-app-skeleton"></a>Создание основы приложения

Команда init обеспечивает формирование шаблонов с соответствующими артефактами, необходимое для развертывания приложения. В приведенном ниже примере создается hello с помощью следующей команды.

```bash
azdata app init --name hello --version v1 --template python
```

При этом создается папка с именем hello.  Вы можете перейди в каталог с помощью `cd` и проверить созданные файлы в папке. Спецификация spec. YAML определяет приложение, например имя, версию и исходный код. Вы можете изменить эту спецификацию, чтобы изменить имя, версию, входные и выходные данные.

Ниже приведен пример выходных данных команды init, которые будут отображаться в папке.

```
hello.py
run-spec.yaml
spec.yaml
```

## <a name="describe-an-app"></a>Описание приложения.

Команда describe предоставляет подробные сведения о приложении, включая конечную точку в кластере. Обычно она используется разработчиком приложения, чтобы создать приложение с помощью клиента Swagger и использовать веб-службу для взаимодействия с приложением на основе REST. Дополнительные сведения см. в статье [Использование приложений в кластерах больших данных](big-data-cluster-consume-apps.md).

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

## <a name="delete-an-app"></a>Удаление приложения

Чтобы удалить приложение из кластера больших данных, используйте следующий синтаксис.

```bash
azdata app delete --name add-app --version v1
```

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о том, как интегрировать приложения, развернутые в [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)], в собственные приложения, см. в статье [Использование приложений в кластерах больших данных](big-data-cluster-consume-apps.md). Дополнительные примеры можно просмотреть в наборе [примеров развертывания приложений](https://aka.ms/sql-app-deploy).

Дополнительные сведения о [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] см. в статье [Что такое [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md).
