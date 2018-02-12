---
title: "Настройка и управление | Документы Microsoft"
ms.custom: 
ms.date: 05/31/2016
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e0fd4554-60c6-4181-ac4c-2e366fb434f6
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 63448281d0e1d135a52bc1c9d0c8afa097a87596
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2018
---
# <a name="configuration-and-management"></a>Настройка и управление
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Эта статья содержит ссылки на более подробные сведения о настройке сервера для поддержки службы обучения компьютера с SQL Server в этих продуктов:

+ Службы R SQL Server 2016 (в базе данных)
+ SQL Server 2017 г машины обучения Services (в базе данных)

> [!NOTE]
> 
> Это содержимое первоначально был написан для выпуска SQL Server 2016, который поддерживается только язык R.
> 
> В SQL Server 2017 г поддержка Python был добавлен, но базовой архитектуры и служб платформы одинаково. Таким образом можно настроить безопасность, памяти, управление ресурсами и другие параметры, которые поддерживают выполнение сценариев Python, точно так же, как для R-скриптов.
> 
> Тем не менее поскольку поддержка Python — это новая функция подробные сведения о потенциальные оптимизации для рабочей нагрузки Python еще не доступны. Повторите попытку позже.

## <a name="r-package-management"></a>Управление пакетами R

В этих разделах описывается, как установить новый R-пакеты на экземпляре SQL Server, управление библиотеками пакет R и восстановление библиотеки пакета после восстановления базы данных.

+ [Установка пакетов R и управление ими](installing-and-managing-r-packages.md)
+ [Установка нового R-пакеты](install-additional-r-packages-on-sql-server.md)
+ [Включение пакета управления для экземпляра с помощью ролей базы данных](r-package-how-to-enable-or-disable.md)
+ [Создание локального репозитория пакетов с помощью miniCRAN](create-a-local-package-repository-using-minicran.md)
+ [Определение установленных пакетов R на сервере SQl Server](determine-which-packages-are-installed-on-sql-server.md)
+ [Синхронизация пакетов R между SQL Server и в файловой системе](package-install-uninstall-and-sync.md)
+ [R-пакеты, установленные в библиотек пользователей](packages-installed-in-user-libraries.md)

## <a name="service-configuration"></a>Настройка службы

В этих разделах описаны внесение изменений в базовую архитектуру службы и управление субъекты безопасности, связанных с ней расширяемости.

+ [Вопросы безопасности](security-considerations-for-the-r-runtime-in-sql-server.md)
+ [Изменение пула учетных записей пользователей для служб SQL Server R](../../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md)
+ [Настройка расширений углубленной аналитики и управление ими](../../advanced-analytics/r/configure-and-manage-advanced-analytics-extensions.md)
+ [Включение пакета управления для экземпляра с помощью ролей базы данных](r-package-how-to-enable-or-disable.md)
+ [Настройка производительности для служб R](sql-server-r-services-performance-tuning.md)

## <a name="resource-governance"></a>Управление ресурсами

В этих разделах описывается, как реализовать управление ресурсами для заданий R или Python, используя доступную функция регулятора ресурсов в выпуске Enterprise Edition.

+ [Управление ресурсами для служб R](../../advanced-analytics/r/resource-governance-for-r-services.md)
+ [Создание пула ресурсов для R](../../advanced-analytics/r/how-to-create-a-resource-pool-for-r.md)

См. также:

+ [Монитор R с помощью SSMS пользовательских отчетов](monitor-r-services-using-custom-reports-in-management-studio.md)

## <a name="initial-setup"></a>Начальная настройка

Дополнительная справка, относящиеся к начальной установки и конфигурации можно найти в следующих разделах:

+ [Часто задаваемые вопросы по обновлению и установке](../r/upgrade-and-installation-faq-sql-server-r-services.md)
+ [Вопросы безопасности](../r/security-considerations-for-the-r-runtime-in-sql-server.md)
+ [Известные проблемы для служб R](../../advanced-analytics/known-issues-for-sql-server-machine-learning-services.md)

