---
title: Установка azdata с помощью установщика Windows
titleSuffix: SQL Server big data clusters
description: Узнайте, как установить средство azdata для установки кластеров больших данных SQL Server и управления ими с помощью установщика.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 5b2e87cf96d6237521caeaae55802d2d72769603
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "73594330"
---
# <a name="install-azdata-to-manage-big-data-clusters-2019-with-windows-installer"></a>Установка `azdata` для управления [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] с помощью установщика Windows

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье описывается установка `azdata` для работы с кластерами больших данных SQL Server 2019 в Windows. Для того чтобы стала возможна установка в Windows, для установки `azdata` требуется `pip`.

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

Дополнительные сведения о кластерах больших данных см. в статье [Что такое [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md)