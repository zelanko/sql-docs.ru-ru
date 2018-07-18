---
title: Начало работы с SQL Server 2017 в облаке | Документация Майкрософт
description: В этом кратком руководстве показано, как SQL Server 2017 под управлением Linux в облаке по своему усмотрению.
author: annashres
ms.author: annashres
manager: craigg
ms.date: 10/25/2017
ms.topic: article
ms.prod: sql
ms.component: ''
ms.custom: sql-linux
ms.technology: linux
ms.assetid: ''
ms.openlocfilehash: f5d67ff25cb5d2816672fafe0602d56921c034bb
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "37995893"
---
# <a name="quickstart-run-the-sql-server-2017-in-the-cloud"></a>Краткое руководство: Запуск SQL Server 2017 в облаке

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этом кратком руководстве будет устанавливаться SQL Server 2017 на Red Hat Enterprise Linux (RHEL), SUSE Linux Enterprise Server (SLES) или Ubuntu в облаке по своему усмотрению. Перейдите к [Подготовка виртуальной машины SQL Server для Linux на портале Azure](https://docs.microsoft.com/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json) SQL Server под управлением Linux в Azure.

    > [!NOTE]
    > If you choose to run a paid edition of SQL Server then you need to bring your own license (BYOL)

## <a name="amazon-web-services"></a>Amazon Web Services
1.  Создание Linux AMI с помощью по крайней мере 2 ГБ памяти, из marketplace 
    * [RHEL 7.3 +](https://aws.amazon.com/marketplace/pp/B00KWBZVK6)
    * [SLES версии 12 с пакетом обновления 2](https://aws.amazon.com/marketplace/pp/B00PMM99PI)
    * [Ubuntu 16.04](https://aws.amazon.com/marketplace/pp/B01JBL2M0O)
1.  Подключение к AMI с ssh
1.  Выполните быстрый запуск для выбранного дистрибутива Linux. 
    * [RHEL](quickstart-install-connect-red-hat.md)
    * [SLES](quickstart-install-connect-suse.md)
    * [Ubuntu](quickstart-install-connect-ubuntu.md)
1.  Настройка удаленных подключений: 
    * Откройте [консоли Amazon EC2]( https://console.aws.amazon.com/ec2/)
    * В области навигации выберите **группы безопасности**. 
    * Выберите **входящим трафиком, Правка, добавить правило**
    * Добавьте правило входящего трафика, разрешающее прохождение трафика через порт, на котором SQL Server ожидает передачи данных (по умолчанию порт TCP 1433)

    
## <a name="digital-ocean"></a>Digital Ocean
1. Войдите в [панели управления](https://cloud.digitalocean.com/login) и нажмите кнопку Создать дроплет
1. Выберите по крайней мере 2 ГБ памяти дроплет Ubuntu 16.04
1. Подключение к дроплет с ssh
1. Выполните [Ubuntu быстрого запуска](quickstart-install-connect-ubuntu.md)
1. Настройка удаленных подключений:
    * В верхней части панели управления, выполните **сети** ссылку, а затем выберите **брандмауэры**
    * Добавьте правило входящего трафика, разрешающее прохождение трафика через порт, на котором SQL Server ожидает передачи данных (по умолчанию порт TCP 1433)
    
## <a name="google-cloud-platform"></a>Google Cloud Platform
1.  Создание образа Linux с помощью по крайней мере 2 ГБ памяти из средства запуска Cloud 
    * [RHEL 7.3 +](https://console.cloud.google.com/launcher/details/rhel-cloud/rhel-7)
    * [SLES версии 12 с пакетом обновления 2](https://console.cloud.google.com/launcher/details/suse-cloud/sles-12)
    * [Ubuntu 16.04](https://console.cloud.google.com/launcher/details/ubuntu-os-cloud/ubuntu-xenial)
1.  Подключение к образу с помощью ssh
1.  Выполните быстрый запуск для выбранного дистрибутива Linux. 
    * [RHEL](quickstart-install-connect-red-hat.md)
    * [SLES](quickstart-install-connect-suse.md)
    * [Ubuntu](quickstart-install-connect-ubuntu.md)
1.  Настройка удаленных подключений: 
    * Перейдите к [правила брандмауэра](https://console.cloud.google.com/networking/firewalls)
    * Добавьте правило входящего трафика, разрешающее прохождение трафика через порт, прослушиваемый SQL Server (по умолчанию tcp: 1433)
