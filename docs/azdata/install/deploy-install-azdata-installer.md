---
title: Установка Azure Data CLI (azdata) с помощью установщика Windows
titleSuffix: ''
description: Узнайте, как установить средство Azure Data CLI (azdata) с помощью установщика.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 09/30/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 9dd953a78a992a9a5fed7135ae0aee02f88e4de9
ms.sourcegitcommit: ae474d21db4f724523e419622ce79f611e956a22
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/20/2020
ms.locfileid: "92257497"
---
# <a name="install-azure-data-cli-azdata-with-windows-installer"></a>Установка [!INCLUDE [azure-data-cli-azdata](../../includes/azure-data-cli-azdata.md)] с помощью установщика Windows

[!INCLUDE [azdata](../../includes/applies-to-version/azdata.md)]

В этой статье описывается порядок установки `azdata` в Windows с помощью установщика. Используйте `azdata` для управления Кластерами больших данных SQL Server и службами данных с поддержкой Azure Arc.

## <a name="steps-to-install-azdata-with-the-microsoft-windows-installer"></a>Порядок установки `azdata` с помощью установщика Microsoft Windows

Чтобы установить `azdata` с помощью установщика Microsoft Windows,

1. Удалите `azdata`, если он был установлен с помощью `pip`. Если `azdata` был установлен с помощью установщика Windows, перейдите к следующему шагу.
1. Установите `azdata` с помощью [установщика Windows](https://aka.ms/azdata-msi).

### <a name="uninstall-azdata-with-windows-installer"></a>Удаление `azdata` с помощью установщика Windows

Чтобы удалить `azdata` с помощью установщика Windows, следуйте инструкциям для соответствующей операционной системы.

| Платформа      | Instructions                                           |
| ------------- |--------------------------------------------------------|
| Windows 10| Пуск > Параметры > Приложения                                |
| Windows 8     | Пуск > Панель управления > Программы > Удалить программу |

Программа для удаления называется `Azdata CLI`. Выберите это приложение, а затем нажмите кнопку `Uninstall`.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о кластерах больших данных см. в статье [Что такое [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ver15.md)]?](../../big-data-cluster/big-data-cluster-overview.md)

Использование `azdata` в [службах данных с поддержкой Azure Arc](/azure/azure-arc/data/)
