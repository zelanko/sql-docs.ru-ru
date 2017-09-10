---
title: "Устранение неполадок и вопросы и ответы для машинного обучения в SQL Server | Документы Microsoft"
ms.custom: 
ms.date: 06/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 05976158e43d7dfafaf02289462d1537f5beeb36
ms.openlocfilehash: 6e45e8dc4df1404833fddd9000eb40cad6e5299f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/08/2017

---

# <a name="troubleshoot-machine-learning"></a>Устранение неполадок машинного обучения

В этой статье содержатся сведения об устранении неполадок, связанных с установкой и настройкой машины обучения функции в SQL Server. Эти сведения включают ссылки на руководства, известные проблемы и заметки о выпуске. Другие статьи, связанные с из этой статьи, предоставляют советы по оптимизации производительности по обучению машины в SQL Server.

Используйте эту страницу в качестве отправной точки для поиска известных проблем, часто задаваемые вопросы установки и процедуры для устранения неполадок.

**Применяется к:** служб R SQL Server 2016, SQL Server 2017 г машинного обучения службы (R и Python)

## <a name="known-issues"></a>Известные проблемы

Следующие статьи список известных проблем в текущем выпуске или описаны проблемы, связанные с предыдущими версиями:

+ [Известные проблемы для служб R](../advanced-analytics/known-issues-for-sql-server-machine-learning-services.md)
+ [Заметки о выпуске для SQL Server 2016](../sql-server/sql-server-2016-release-notes.md)
+ [Заметки о выпуске для SQL Server 2017](../sql-server/sql-server-2017-release-notes.md)

## <a name="troubleshooting-prerequisites"></a>Устранение неполадок предварительные требования

Если произошла ошибка, или необходимо понять проблему в вашей среде, важно систематически собирать сведения. Эта информация включает версию, выпуск, контекст безопасности и контекст выполнения.

Следующие статьи список информации, которая позволяет самостоятельного устранения неполадок или запрос для получения технической поддержки.

+ [Сбор данных для устранения неполадок машинного обучения](data-collection-ml-troubleshooting-process.md)

## <a name="setup-and-configuration-guides"></a>Руководства по установке и настройке

Начните здесь, если вы не настроили машинного обучения с помощью SQL Server или если вы хотите добавить компонент:

+ [Установка служб R или Machine Services обучения с помощью R](../advanced-analytics/r/set-up-sql-server-r-services-in-database.md)
+ [Настройка службы обучения машины с Python](../advanced-analytics/python/setup-python-machine-learning-services.md)
+ [Часто задаваемые вопросы установки](../advanced-analytics/r/upgrade-and-installation-faq-sql-server-r-services.md)
+ [Используйте SqlBindR, чтобы обновить экземпляр служб R](../advanced-analytics/r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)

В следующих статьях описывается дополнительные действия, необходимые для автономной установки функций компьютера обучения в SQL Server:

+ [Автоматической установки служб R](../advanced-analytics/r/unattended-installs-of-sql-server-r-services.md) 
+ [Автоматически устанавливать службы обучения машины с Python](../advanced-analytics/python/unattended-installs-of-sql-server-python-services.md)

Если необходимо установить машинного обучения на компьютере без подключения к Интернету, используйте ссылки в этой статье, загрузить компоненты R и Python до начала установки:

+ [Установка компонентов обучения компьютер без доступа к Интернету](../advanced-analytics/r/installing-ml-components-without-internet-access.md)

### <a name="configuration"></a>Конфигурация

В следующих статьях содержатся сведения о значения по умолчанию, а также настройке конфигурации для машинного обучения на экземпляр:

+ [Изменение пула учетных записей пользователей для SQL Server R Services](../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md)  
+ [Настройка и Управление расширениями углубленной аналитики](../advanced-analytics/r/configure-and-manage-advanced-analytics-extensions.md)  
+ [Создание пула ресурсов](r/how-to-create-a-resource-pool-for-r.md)
+ [Оптимизация для рабочих нагрузок R](r/operationalizing-your-r-code.md)

## <a name="related-tools-and-services"></a>Связанные инструменты и службы

+ [Настройка автономного сервера обучения машины Microsoft](../advanced-analytics/r/create-a-standalone-r-server.md)
+ [Настройка сервера R на Виртуальной машине Azure](../advanced-analytics/r/provision-the-r-server-only-sql-server-2016-enterprise-vm-on-azure.md)
+ [Установка R Server для Windows](https://msdn.microsoft.com/microsoft-r/rserver-install-windows)
+ [Получить средства R для Visual Studio](https://www.visualstudio.com/vs/rtvs/)

