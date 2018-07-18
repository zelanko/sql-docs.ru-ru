---
title: Настройка и управление экземплярами службы SQL Server Machine Learning | Документы Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: b24832c8debe12c11aaa337e9558d99e7fae5ae0
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34585506"
---
# <a name="configure-and-manage-machine-learning-components-in-sql-server"></a>Настройка и управление ими компонентов машины обучения в SQL Server
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

Эти статьи описывается, как установить новый R-пакеты на экземпляре SQL Server, управление библиотеками пакет R и восстановление библиотеки пакета после восстановления базы данных.

+ [По умолчанию R и Python пакетов в SQL Server](installing-and-managing-r-packages.md)
+ [Установка нового R-пакеты](install-additional-r-packages-on-sql-server.md)
+ [Включение пакета управления для экземпляра с помощью ролей базы данных](r-package-how-to-enable-or-disable.md)
+ [Создание локального репозитория пакетов с помощью miniCRAN](create-a-local-package-repository-using-minicran.md)
+ [Определение установленных пакетов R на сервере SQl Server](determine-which-packages-are-installed-on-sql-server.md)
+ [Синхронизация пакетов R между SQL Server и в файловой системе](package-install-uninstall-and-sync.md)
+ [R-пакеты, установленные в библиотек пользователей](packages-installed-in-user-libraries.md)

## <a name="service-configuration"></a>Настройка службы

Эти статьи описывается внесение изменений в базовую архитектуру службы и управлять субъектами безопасности, связанных с ней расширяемости.

+ [Вопросы безопасности](security-considerations-for-the-r-runtime-in-sql-server.md)
+ [Изменение пула учетных записей пользователей для служб SQL Server R](../../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md)
+ [Настройка расширений углубленной аналитики и управление ими](../../advanced-analytics/r/configure-and-manage-advanced-analytics-extensions.md)
+ [Включение пакета управления для экземпляра с помощью ролей базы данных](r-package-how-to-enable-or-disable.md)
+ [Настройка производительности для служб R](sql-server-r-services-performance-tuning.md)

## <a name="resource-governance"></a>Управление ресурсами

Эти статьи описывают, как реализовать управление ресурсами для заданий R или Python, используя доступную функция регулятора ресурсов в выпуске Enterprise Edition.

+ [Управление ресурсами для служб R](../../advanced-analytics/r/resource-governance-for-r-services.md)
+ [Создание пула ресурсов для R](../../advanced-analytics/r/how-to-create-a-resource-pool-for-r.md)

См. также:

+ [Монитор R с помощью SSMS пользовательских отчетов](monitor-r-services-using-custom-reports-in-management-studio.md)

## <a name="initial-setup"></a>Начальная настройка

Дополнительная справка, относящиеся к начальной установки и конфигурации можно найти в следующих статьях:

+ [Часто задаваемые вопросы по обновлению и установке](../r/upgrade-and-installation-faq-sql-server-r-services.md)
+ [Вопросы безопасности](../r/security-considerations-for-the-r-runtime-in-sql-server.md)
+ [Известные проблемы для служб R](../../advanced-analytics/known-issues-for-sql-server-machine-learning-services.md)

