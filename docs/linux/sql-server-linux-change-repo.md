---
title: "Регистрация репозитория общей доступности для SQL Server для Linux | Документы Microsoft"
description: "Изменить репозиториев из репозитория preview 2017 г. SQL Server в репозиторий Общая доступность (GA) для Linux (GA также иногда называют RTM)."
author: annashres
ms.author: anshrest
manager: jhubbard
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.translationtype: MT
ms.sourcegitcommit: bc1321dd91a0fcb7ab76b207301c6302bb3a5e64
ms.openlocfilehash: a0d6ff0a983f1d1d1ad8fdcc7de37d9a06032025
ms.contentlocale: ru-ru
ms.lasthandoff: 10/06/2017

---
# <a name="change-repositories-from-the-preview-repository-to-the-ga-repository"></a>Изменить репозиториев из репозитория предварительного просмотра в репозитории общедоступной версии

Когда вы обновляете 2017 г. SQL Server CTP-версии 2.1, версия-кандидат 1 или версии-кандидата 2 версии Общая доступность (GA), необходимо переключиться в репозитории. В следующих разделах объясняется репозиториев и внесение изменений перед обновлением.

## <a name="repository-choices"></a>Выбор хранилища

Это важно отметить, что существует два основных типа хранилища для каждого распределения:

  > [!IMPORTANT]
  > Все версии до CTP-версии 2.1, необходимо обновить до по крайней мере 2.1 перед обновлением до общедоступной.

- **Накопительный пакет обновления (CU)**: репозиторий накопительное обновление (CU) содержит пакеты для базовой версии SQL Server и исправления или улучшения версии. Накопительные пакеты обновления относятся только к версии, например 2017 г. SQL Server. Их появления в обычных ритме.

- **GDR**: GDR репозитория пакетов для базовой версии SQL Server и только важные исправления и обновления для системы безопасности содержит версии. Эти обновления также добавляются в следующий выпуск CU.

Каждое CU и GDR содержит полный пакет SQL Server и все последующие обновления для этого репозитория. Обновление с версии GDR на текущую версию поддерживается изменение настроенного хранилища SQL Server. Вы также можете [понизить](sql-server-linux-setup.md#rollback) для любого из выпусков в ваш основной номер версии (например: 2017 г.).

> [!NOTE]
> Можно обновить с версии GDR на CU выпуска в любое время, изменив репозиториев. Обновление с накопительным пакетом обновления версии GDR не поддерживается. 

## <a name="change-to-a-ga-repository"></a>Изменения в репозитории общедоступной версии

Чтобы изменить один исходный репозиторий (CU или GDR) из репозитория предварительного просмотра, выполните следующие действия:

1. Удаляет ранее настроенный Предварительный просмотр репозитория.

   | Платформа | Команда удаления репозитория |
   |-----|-----|
   | RHEL | `sudo rm -rf /etc/yum.repos.d/mssql-server.repo` |
   | SLES | `sudo zypper removerepo 'packages-microsoft-com-mssql-server'` |
   | Ubuntu | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server xenial main'` |

1. Для **Ubuntu только**, Импорт ключей GPG общедоступный репозиторий.

   ```bash
   sudo curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

1. Настройте новый репозиторий.

   | Платформа | Хранилище | Command |
   |-----|-----|-----|
   | RHEL | CU | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo` |
   | RHEL | GDR | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017-gdr.repo` |
   | SLES | CU  | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017.repo` |
   | SLES | GDR | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017-gdr.repo` |
   | Ubuntu | CU | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)" && sudo apt-get update` |
   | Ubuntu | GDR | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017-gdr.list)" && sudo apt-get update` |

1. [Установка](sql-server-linux-setup.md#platforms) или [обновление](sql-server-linux-setup.md#upgrade) SQL Server с помощью Общедоступной репозитория.

   > [!IMPORTANT]
   > На этом этапе, если вы решили выполнить полную установку с помощью [по основам](#platforms), помните, что вы настроили целевой репозиторий. В учебниках по не нужно повторять этот шаг. Это особенно важно, если настроить хранилище GDR, так как статьи краткого руководства используйте CU репозитория.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения об установке 2017 г. SQL Server в Linux см. в разделе [руководство по установке для SQL Server в Linux](sql-server-linux-setup.md).

