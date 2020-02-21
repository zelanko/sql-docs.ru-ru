---
author: MikeRayMSFT
ms.prod: sql
ms.topic: include
ms.date: 01/07/2020
ms.author: mikeray
ms.openlocfilehash: 401d214495cd8df8ec3401c0b18db8ebe8773226
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "75721540"
---
### <a name="pythonpip-installation"></a>Установка Python и PIP

Вы можете установить `azdata` в ОС Linux с помощью yum, apt или zypper, или в MacOS с помощью диспетчеров пакетов установки Homebrew. Пока не появились эти диспетчеры пакетов,для установки требовалось наличие Python и PIP.

>[!IMPORTANT]
>Прежде чем продолжать работу, удалите все установки `azdata`, установленные в глобальной системе Python. Новые установщики или собственные пакеты добавляют к переменной пути значение `azdata`, и очередность вызова предсказать невозможно.
Если в глобальной системе Python уже есть `azdata`, удалите его перед продолжением.

Чтобы просмотреть характеристики текущей установки, выполните следующую команду:

```bash
$ pip list --format columns
```

Если `azdata` устанавливается с помощью PIP, он возвращает пакет и версию. Пример:

```
 Package             Version
------------------- ----------
azdata-cli          15.0.X
azdata-cli-app      15.0.X
azdata-cli-cluster  15.0.X
azdata-cli-core     15.0.X
azdata-cli-hdfs     15.0.X
azdata-cli-notebook 15.0.X
azdata-cli-profile  15.0.X
azdata-cli-spark    15.0.X
azdata-cli-sql      15.0.X
```

В следующем примере удаляется установка PIP для `azdata`.

```bash
$ pip freeze | grep azdata-* | xargs pip uninstall -y
```

Убедившись, что вы успешно удалили все установки `azdata`, установленные с помощью PIP, продолжайте текущую установку.