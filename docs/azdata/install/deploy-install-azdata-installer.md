---
title: Установка azdata с помощью установщика Windows
titleSuffix: ''
description: Узнайте, как установить средство azdata с помощью установщика.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: a33e43386c44ec2ab60166ef57a502fc592c8d73
ms.sourcegitcommit: d56f1eca807c55cf606a6316f3872585f014fec1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/22/2020
ms.locfileid: "90914957"
---
# <a name="install-azdata-to-manage-big-data-clusters-2019-with-windows-installer"></a>Установка `azdata` для управления [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ss-nover.md)] с помощью установщика Windows

[!INCLUDE[SQL Server 2019](../../includes/applies-to-version/azdata.md)]

В этой статье описывается порядок установки `azdata` в Windows. Для того чтобы стала возможна установка в Windows, для установки `azdata` требуется `pip`.

>Для Linux (Ubuntu) см. статью [установка `azdata` с помощью установщика](./deploy-install-azdata-linux-package.md).

В настоящее время нет диспетчеров пакетов для установки `azdata` в других операционных системах или дистрибутивах. Об установке на этих платформах см. в разделе [Установка `azdata` без диспетчера пакетов](./deploy-install-azdata.md).

## <a name="install-azdata-with-the-microsoft-windows-installer"></a>Установка `azdata` с помощью установщика Microsoft Windows

Чтобы установить `azdata` с помощью установщика Microsoft Windows,

1. Удалите `azdata`, если он был установлен с помощью `pip`. Если `azdata` был установлен с помощью установщика Windows, перейдите к следующему шагу.
1. Установите `azdata` с помощью установщика Windows.

### <a name="uninstall-if-previous-installation-done-with-pip"></a>Удалите его, если предыдущая установка была выполнена с помощью `pip`

Если установлены какие-либо предыдущие выпуски `azdata`, нужно обязательно удалить их перед установкой последней версии.

   Чтобы удалить релиз-кандидат версию `azdata`, выполните следующую команду.

   ```bash
   pip3 uninstall -r https://azdatacli.blob.core.windows.net/python/azdata/2019-rc1/requirements.txt
   ```

После удаления [установите `azdata` на Windows](#install-azdata-windows).

>[!NOTE]
>Если предыдущая установка была выполнена с помощью MSI, то при использовании установщика MSI не нужно удалять никакие установленные версии.

### <a name="install-with-windows-installer"></a><a id="install-azdata-windows"></a>Установка с помощью установщика Windows

Используйте установщик Windows для установки или обновления `azdata` в Windows.

[Скачайте установщик Windows `azdata`](https://aka.ms/azdata-msi).

Когда установщик спросит, можно ли внести изменения в компьютер, нажмите кнопку `Yes`.

### <a name="uninstall-azdata-with-windows-installer"></a>Удаление `azdata` с помощью установщика Windows

Чтобы удалить `azdata` с помощью установщика Windows, следуйте инструкциям для соответствующей операционной системы.

| Платформа      | Instructions                                           |
| ------------- |--------------------------------------------------------|
| Windows 10| Пуск > Параметры > Приложения                                |
| Windows 8     | Пуск > Панель управления > Программы > Удалить программу |

Программа для удаления называется `Azdata CLI`. Выберите это приложение, а затем нажмите кнопку `Uninstall`.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о кластерах больших данных см. в статье [Что такое [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ver15.md)]?](../../big-data-cluster/big-data-cluster-overview.md)

Использование azdata со [службами данных с поддержкой Azure Arc](/azure/azure-arc/data/)
