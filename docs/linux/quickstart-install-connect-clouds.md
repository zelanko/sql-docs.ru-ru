---
title: Начало работы с SQL Server (на Linux) в облаке
titleSuffix: SQL Server
description: Сведения о том, как установить SQL Server в Red Hat Enterprise Linux (RHEL), SUSE Linux Enterprise Server (SLES) или Ubuntu в облаке по вашему выбору.
author: VanMSFT
ms.author: vanto
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: ''
ms.openlocfilehash: 49f47819a6ca128ce45f950c9cd6881e325bec59
ms.sourcegitcommit: 22102f25db5ccca39aebf96bc861c92f2367c77a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2020
ms.locfileid: "92115607"
---
# <a name="quickstart-run-sql-server-in-the-cloud"></a>Краткое руководство. Запуск SQL Server в облаке
[!INCLUDE [SQL Server - Linux](../includes/applies-to-version/sql-linux.md)]

В этом кратком руководстве содержатся инструкции по установке SQL Server в Red Hat Enterprise Linux (RHEL), SUSE Linux Enterprise Server (SLES) или Ubuntu в выбранном облаке. Сведения о запуске SQL Server на Linux в Azure см. в статье о [подготовке виртуальной машины Linux с SQL Server на портале Azure](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%252fsql%252ftoc%252ftoc.json).

> [!NOTE]
> Чтобы запустить платный выпуск SQL Server, потребуется использовать собственную лицензию (BYOL).

## <a name="amazon-web-services"></a>Amazon Web Services
1.  Воспользуйтесь Marketplace и создайте Linux AMI с объемом памяти не менее 2 ГБ. 
    * [RHEL 7.3 и выше](https://aws.amazon.com/marketplace/pp/B00KWBZVK6)
    * [SLES версии 12 с пакетом обновления 2 (SP2) и более поздних версий](https://aws.amazon.com/marketplace/pp/B00PMM99PI)
    * [Ubuntu 16.04](https://aws.amazon.com/marketplace/pp/B01JBL2M0O)
1.  Подключитесь к AMI по протоколу SSH.
1.  Выполните инструкции из краткого руководства по выбранному дистрибутиву Linux: 
    * [RHEL](quickstart-install-connect-red-hat.md)
    * [SLES](quickstart-install-connect-suse.md)
    * [Ubuntu](quickstart-install-connect-ubuntu.md)
1.  Настройте удаленные подключения. 
    * Откройте [консоль Amazon EC2]( https://console.aws.amazon.com/ec2/).
    * В области навигации выберите **Группы безопасности**. 
    * Последовательно выберите **"Входящий трафик", "Изменить", "Добавить правило"** .
    * Добавьте правило входящего трафика, разрешающее прохождение данных через порт, прослушиваемый SQL Server (по умолчанию используется TCP-порт 1433).

    
## <a name="digital-ocean"></a>Digital Ocean
1. Войдите на [панель управления](https://cloud.digitalocean.com/login) и щелкните "Create a droplet" (Создать дроплет).
1. Выберите дроплет Ubuntu 16.04 с объемом памяти не менее 2 ГБ.
1. Подключитесь к дроплету по протоколу SSH.
1. Следуйте инструкциям в [кратком руководстве по Ubuntu](quickstart-install-connect-ubuntu.md).
1. Настройте удаленные подключения.
    * В верхней части панели управления перейдите по ссылке **Сеть** и выберите **Брандмауэры**.
    * Добавьте правило входящего трафика, разрешающее прохождение данных через порт, прослушиваемый SQL Server (по умолчанию используется TCP-порт 1433).
    
## <a name="google-cloud-platform"></a>Google Cloud Platform
1.  Воспользуйтесь Cloud Launcher и создайте образ Linux с объемом памяти не менее 2 ГБ. 
    * [RHEL 7.3 и выше](https://console.cloud.google.com/launcher/details/rhel-cloud/rhel-7)
    * [SLES версии 12 с пакетом обновления 4 (SP4)](https://console.cloud.google.com/launcher/details/suse-cloud/sles-12)
    * [Ubuntu 16.04](https://console.cloud.google.com/launcher/details/ubuntu-os-cloud/ubuntu-xenial)
1.  Подключитесь к образу по протоколу SSH.
1.  Выполните инструкции из краткого руководства по выбранному дистрибутиву Linux: 
    * [RHEL](quickstart-install-connect-red-hat.md)
    * [SLES](quickstart-install-connect-suse.md)
    * [Ubuntu](quickstart-install-connect-ubuntu.md)
1.  Настройте удаленные подключения. 
    * Перейдите на страницу [Правила брандмауэра](https://console.cloud.google.com/networking/firewalls).
    * Добавьте правило входящего трафика, разрешающее прохождение данных через порт, прослушиваемый SQL Server (по умолчанию используется TCP-порт 1433).