---
title: Развертывание приложения в кластере SQL Server больших данных | Документация Майкрософт
description: Разверните скрипт Python или R в качестве приложения в кластере SQL Server 2019 больших данных (Предварительная версия).
author: TheBharath
ms.author: bharaths
manager: craigg
ms.date: 11/07/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: dd24b4379f50a5b974e7a0a90412d1e13bf6db22
ms.sourcegitcommit: 87fec38a515a7c524b7c99f99bc6f4d338e09846
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/08/2018
ms.locfileid: "51272562"
---
# <a name="how-to-deploy-an-app-on-sql-server-2019-big-data-cluster-preview"></a>Развертывание приложения в кластере SQL Server 2019 больших данных (Предварительная версия)

В этой статье описывается развертывание и управление ими скрипт R и Python, как приложение в кластере SQL Server 2019 больших данных (Предварительная версия).

Развертываются и управляются с помощью приложения Python и R **mssqlctl-pre** программы командной строки, который включен в CTP 2.1. В этой статье приведены примеры того, как развернуть эти скрипты R и Python в качестве приложения из командной строки.

## <a name="prerequisites"></a>предварительные требования

Необходимо иметь кластер SQL Server 2019 больших данных, настроенный. Дополнительные сведения см. в разделе [развертывание сервера SQL, большие данные кластера в Kubernetes](deployment-guidance.md). 

## <a name="installation"></a>Установка

**Mssqlctl-pre** командной строки служебная программа для предварительного просмотра средство развертывания приложений Python и R. Чтобы установить программу, используйте следующую команду:

```cmd
pip3 install --extra-index-url https://private-repo.microsoft.com/python/ctp-2.1 mssqlctlpre
```

## <a name="capabilities"></a>Возможности

В CTP-версии 2.1, которые можно создавать удалять, выводить список и запускать приложение R или Python. В следующей таблице описаны команды развертывания приложения, которые можно использовать с **mssqlctl-pre**.

| Command | Описание |
|---|---|
| `mssqlctl-pre login` | Войдите в кластер SQL Server больших данных |
| `mssqlctl-pre app create` | Создание приложения |
| `mssqlctl-pre app list` | Список развернутых приложений |
| `mssqlctl-pre app delete` | Удаление приложения |
| `mssqlctl-pre app run` | Список запущенных приложений |

Вы можете получить справку с `--help` параметра, как показано в следующем примере:

```bash
mssqlctl-pre app create --help
```

Эти команды, более подробно в следующих разделах.

## <a name="log-in"></a>Войти

Перед настройкой приложения Python и R, сначала выполнить вход в кластер для обработки больших данных с использованием SQL Server `mssqlctl-pre login` команды. Укажите IP-адрес (внешний) `service-proxy-lb` (например: `https://ip-address:30777`), а также имя пользователя и пароль для кластера.

IP-адрес службы прокси-сервера балансировки нагрузки службы можно получить, выполнив следующую команду в окне bash или cmd:
```bash 
kubectl get svc service-proxy-lb -n <name of your cluster>
```

```bash
mssqlctl-pre login -e https://<ip-address-of-service-proxy-lb> -u <user-name> -p <password>
```

## <a name="create-an-app"></a>Создание приложения

Чтобы создать приложение, следует передать файлы кода Python или R, чтобы **mssqlctl-pre** с `app create` команды. Эти файлы находятся локально на компьютере, который вы создаете приложение из.

Чтобы создать новое приложение в кластере большие данные, используйте следующий синтаксис:

```bash
mssqlctl-pre app create -n <app_name> -v <version_number> -r <runtime> -i <path_to_code_init> -c <path_to_code> --inputs <input_params> --outputs <output_params> 
```

Следующая команда является примером как может выглядеть эта команда:

```py
#add.py
def add(x,y):
        result = x+y
        return result;
result=add(x,y)
```
Чтобы попробовать сделать это, сохраните приведенный выше код в локальный каталог, как `add.py` и выполните приведенную ниже команду

```bash
mssqlctl-pre app create --name add-app --version v1 --runtime Python --code ./add.py  --inputs x=int,y=int --outputs result=int 
```

Вы можете проверить, если приложение развертывается с помощью команды списка:

```bash
mssqlctl-pre app list
```

Если развертывание не будет завершено, вы должны увидеть «штат» Показать «Создание»: 

```
[
  {
    "name": "add-app",
    "state": "Creating",
    "version": "v1"
  }
]
```

После успешного завершения развертывания вы увидите «состояние» изменить на «Готово»:

```
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
mssqlctl-pre app list
```

Если указать имя и версию, будут перечислены этого конкретного приложения и его состояние ("Создание" или "Готово"):

```bash
mssqlctl-pre app list --name <app_name> --version <app_version>
```

В следующем примере демонстрируется эта команда:

```bash
mssqlctl-pre app list --name add-app --version v1
```

Вы должны увидеть результат, аналогичный приведенному ниже:

```
[
  {
    "name": "add-app",
    "state": "Ready",
    "version": "v1"
  }
]
```

## <a name="run-an-app"></a>Запуск приложения

Если приложение находится в состоянии «Готово», можно использовать его, запустив его с указанным входные параметры. Для запуска приложений, используйте следующий синтаксис:

```bash
mssqlctl-pre app run --name <app_name> --version <app_version> --inputs <inputs_params>
```

Например, следующая команда демонстрирует выполнения команды:

```bash
mssqlctl-pre app run --name add-app --version v1 --inputs x=1,y=2
```

Если выполнение прошло успешно, вы увидите выходные данные, указанные при создании приложения. Пример приведен ниже.

```
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

## <a name="delete-an-app"></a>Удаление приложения

Чтобы удалить приложение из кластера больших данных, используйте следующий синтаксис:

```bash
mssqlctl-pre app delete --name add-app --version v1
```

## <a name="next-steps"></a>Следующие шаги

Вы можете также проверить Дополнительные примеры по [ https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster ](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster). 

Дополнительные сведения о больших данных кластеров SQL Server, см. в разделе [Каковы кластеров SQL Server 2019 больших данных?](big-data-cluster-overview.md).
