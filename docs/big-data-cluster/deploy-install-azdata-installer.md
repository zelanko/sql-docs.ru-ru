---
title: Установка аздата с установщик Windows
titleSuffix: SQL Server big data clusters
description: Узнайте, как установить средство аздата для установки (предварительной [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] версии) и управления им с помощью установщика.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: a8dd5d2c7d0210880a82d774185a3f2a915608ec
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70158149"
---
# <a name="install-azdata-to-manage-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd-with-windows-installer"></a>Установка `azdata` для управления [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] с помощью установщик Windows

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье описывается, как `azdata` установить версию-кандидат для кластера больших данных SQL Server 2019 в Windows. Если установка Windows была доступна, установка `azdata` обязательно. `pip`

>Для Linux (Ubuntu) см. [статью `azdata` установка с помощью установщика](./deploy-install-azdata-linux-package.md).

В настоящее время нет диспетчеров пакетов для установки `azdata` в других операционных системах или дистрибутивах. Сведения об этих платформах см. в разделе [Install `azdata` без диспетчера пакетов](./deploy-install-azdata.md).

## <a name="install-azdata-with-the-microsoft-windows-installer"></a>Установка `azdata` с помощью установщик Windows Microsoft

Чтобы установить `azdata` на Microsoft установщик Windows,

1. Удалите `azdata` , если он был установлен `pip`с помощью. Если `azdata` установлен с помощью установщик Windows, перейдите к следующему шагу.
1. Установите `azdata` с помощью установщик Windows.

### <a name="uninstall-if-previous-installation-done-with-pip"></a>Удалить, если предыдущая установка выполнена`pip`

Если у вас установлены предыдущие версии **мссклктл** , удалите ее. Следующая команда удаляет версию **мссклктл**для CTP-версии 3,1.

   ```bash
   pip3 uninstall -r https://private-repo.microsoft.com/python/ctp3.1/mssqlctl/requirements.txt
   ```

Если у вас есть предыдущие выпуски `azdata` , важно сначала удалить ее перед установкой последней версии.

   Для CTP-версии 3,2 выполните следующую команду.

   ```bash
   pip3 uninstall -r https://azdatacli.blob.core.windows.net/python/azdata/2019-ctp3.2/requirements.txt
   ```

После удаления [ `azdata` установите в Windows](#install-azdata-windows).

>[!NOTE]
>Если предыдущая установка была выполнена с помощью MSI, то перед использованием установщика MSI не нужно будет удалять никакие текущие версии.

### <a id="install-azdata-windows"></a>Установка с помощью установщик Windows

Используйте установщик Windows для установки или обновления `azdata` в Windows.

[Скачайте установщикWindows`azdata` ](http://aka.ms/azdata-msi).

Когда установщик спрашивает, может ли он внести изменения в компьютер, нажмите кнопку `Yes`.

### <a name="uninstall-azdata-with-windows-installer"></a>Удаление `azdata` с помощью установщик Windows

Чтобы удалить `azdata` с установщик Windows, следуйте инструкциям по соответствующей операционной системе.

| Платформа      | Инструкция                                           |
| ------------- |--------------------------------------------------------|
| Windows 10    | Запуск > параметров > приложений                                |
| Windows 8     | Запуск > панели управления > программы > Удаление программы |

Программа для удаления называется **`Azdata CLI`** . Выберите это приложение, а затем нажмите `Uninstall` кнопку.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах больших данных см. в разделе [ [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]что такое?](big-data-cluster-overview.md).
