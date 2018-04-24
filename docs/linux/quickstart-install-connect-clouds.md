---
title: Приступая к работе с 2017 г. SQL Server в облаке | Документы Microsoft
description: Краткого руководства показано, как выполнять 2017 г. SQL Server в Linux в облаке по своему усмотрению.
author: annashres
ms.author: annashres
manager: craigg
ms.date: 10/25/2017
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.component: ''
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: ''
ms.openlocfilehash: 29ed2b218f4d9c746f9356a2a57bbacd845b4df6
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="quickstart-run-the-sql-server-2017-in-the-cloud"></a>Краткое руководство: Запуск 2017 г. SQL Server в облаке

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этом кратком руководстве установит 2017 г. SQL Server в Red Hat Enterprise Linux (RHEL), SUSE Linux Enterprise Server (SLES) или Ubuntu в облаке по своему усмотрению. Последовательно выберите пункты [подготовки виртуальной машины Linux SQL Server на портале Azure](https://docs.microsoft.com/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json) для запуска SQL Server в Linux в Azure.

    > [!NOTE]
    > If you choose to run a paid edition of SQL Server then you need to bring your own license (BYOL)

## <a name="amazon-web-services"></a>Веб-службы Amazon
1.  Создайте по крайней мере 2 ГБ памяти в Marketplace Linux AMI 
    * [RHEL 7.3 +](https://aws.amazon.com/marketplace/pp/B00KWBZVK6)
    * [SLES версии 12 с пакетом обновления 2](https://aws.amazon.com/marketplace/pp/B00PMM99PI)
    * [Ubuntu 16.04](https://aws.amazon.com/marketplace/pp/B01JBL2M0O)
1.  Подключиться к AMI с ssh
1.  Выполните кратком руководстве для дистрибутив Linux, которые вы выбрали. 
    * [RHEL](quickstart-install-connect-red-hat.md)
    * [SLES](quickstart-install-connect-suse.md)
    * [Ubuntu](quickstart-install-connect-ubuntu.md)
1.  Настройка для удаленных соединений. 
    * Откройте [консоли Amazon EC2]( https://console.aws.amazon.com/ec2/)
    * В области навигации выберите **группы безопасности**. 
    * Выберите **входящих подключений, Правка, добавить правило**
    * Добавьте правило входящего трафика, разрешающее трафик через порт, который SQL Server прослушивает (по умолчанию порт TCP 1433)

    
## <a name="digital-ocean"></a>Цифровая подпись Аквамарин
1. Войдите на [панели управления](https://cloud.digitalocean.com/login) и нажмите кнопку Создание дроплета
1. Выберите по крайней мере 2 ГБ памяти Ubuntu 16.04 дроплета
1. Соединиться с дроплет ssh
1. Выполните [Ubuntu краткое руководство](quickstart-install-connect-ubuntu.md)
1. Настройка для удаленных соединений.
    * В верхней части панели управления, выполните **сети** связь, а затем выберите **брандмауэров**
    * Добавьте правило входящего трафика, разрешающее трафик через порт, который SQL Server прослушивает (по умолчанию порт TCP 1433)
    
## <a name="google-cloud-platform"></a>Google облачной платформы
1.  Создание образа Linux с по крайней мере 2 ГБ памяти, из облака запуска 
    * [RHEL 7.3 +](https://console.cloud.google.com/launcher/details/rhel-cloud/rhel-7)
    * [SLES версии 12 с пакетом обновления 2](https://console.cloud.google.com/launcher/details/suse-cloud/sles-12)
    * [Ubuntu 16.04](https://console.cloud.google.com/launcher/details/ubuntu-os-cloud/ubuntu-xenial)
1.  Подключитесь к образу с ssh
1.  Выполните кратком руководстве для дистрибутив Linux, которые вы выбрали. 
    * [RHEL](quickstart-install-connect-red-hat.md)
    * [SLES](quickstart-install-connect-suse.md)
    * [Ubuntu](quickstart-install-connect-ubuntu.md)
1.  Настройка для удаленных соединений. 
    * Последовательно выберите пункты [правила брандмауэра](https://console.cloud.google.com/networking/firewalls)
    * Добавьте правило входящего трафика, разрешающее трафик через порт, прослушиваемый SQL Server (по умолчанию tcp: 1433)
