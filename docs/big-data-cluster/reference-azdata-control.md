---
title: Справочник по элементу управления аздата
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам управления аздата.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 6fceea54c6ea7d5c904cc27c87033c4a40cff59f
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70158219"
---
# <a name="azdata-control"></a>элемент управления аздата

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

Эта статья содержит справочную статью по **аздата**. 

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
[Создание элемента управления аздата](#azdata-control-create) | Создание плоскости управления.
[Удаление элемента управления аздата](#azdata-control-delete) | Удаление плоскости управления.
## <a name="azdata-control-create"></a>Создание элемента управления аздата
В вашей системе требуется Create Control плоскость-KUBE config, а также следующие переменные среды [' CONTROLLER_USERNAME ', ' CONTROLLER_PASSWORD ', ' MSSQL_SA_PASSWORD ', ' KNOX_PASSWORD '].
```bash
azdata control create [--name -n] 
                      [--config-profile -c]  
                      [--accept-eula -a]  
                      [--node-label -l]  
                      [--force -f]
```
### <a name="examples"></a>Примеры
Развертывание элемента управления.
```bash
azdata control create
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--name -n`
Имя плоскости управления, используемое для пространств имен kubernetes.
#### `--config-profile -c`
Профиль конфигурации кластера, используемый для развертывания кластера: ["AKS-dev-test", "кубеадм-произв", "minikube-dev-test", "кубеадм-dev-test"]
#### `--accept-eula -a`
Вы принимаете условия лицензии? [да/нет]. Если вы не хотите использовать этот аргумент, можно присвоить переменной среды ACCEPT_EULA значение "yes". Условия лицензии для этого продукта можно просмотреть по адресу https://aka.ms/azdata-eula.
#### `--node-label -l`
Метка узла, используемая для обозначения узлов, на которых следует выполнить развертывание.
#### `--force -f`
Принудительное создание; пользователь не будет получать запросы на ввод значений; все ошибки будут выводиться в рамках потока stderr.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Повышение уровня детализации журнала для включения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: json, jsonc, table, tsv.  Значение по умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.
## <a name="azdata-control-delete"></a>Удаление элемента управления аздата
В системе требуется удаление плоскости управления-KUBE config.
```bash
azdata control delete --name -n 
                      [--force -f]
```
### <a name="examples"></a>Примеры
Развертывание элемента управления.
```bash
azdata control delete
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--name -n`
Имя плоскости управления, используемое для пространства имен kubernetes.
### <a name="optional-parameters"></a>Необязательные параметры
#### `--force -f`
Принудительно удалить плоскость управления.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Повышение уровня детализации журнала для включения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: json, jsonc, table, tsv.  Значение по умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.

## <a name="next-steps"></a>Следующие шаги

- Дополнительные сведения о других командах **azdata** см. в [справочнике по azdata](reference-azdata.md). 

- Дополнительные сведения об установке средства **azdata** см. в статье [Установка azdata для управления кластерами больших данных SQL Server 2019](deploy-install-azdata.md).
