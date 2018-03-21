---
title: "Устранение неполадок и вопросы и ответы для машинного обучения в SQL Server | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2018
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.workload: Inactive
ms.openlocfilehash: 5b9a5c6497781ef67d9d2ef9b9032a4d9ee250e5
ms.sourcegitcommit: 8e897b44a98943dce0f7129b1c7c0e695949cc3b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/21/2018
---
# <a name="troubleshoot-machine-learning"></a>Устранение неполадок машинного обучения
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье по устранению неполадок ссылки на руководства, известные проблемы и заметки о выпуске. Другие статьи, связанные с из этой статьи, предоставляют советы по оптимизации производительности по обучению машины в SQL Server.

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

+ [Установка служб SQL Server 2017 г машинного обучения (в базе данных)](install/sql-machine-learning-services-windows-install.md)
+ [Установка обучения машины 2017 г. сервер SQL Server (автономный)](install/sql-machine-learning-standalone-windows-install.md)
+ [Установка служб R SQL Server 2016 (в базе данных)](install/sql-r-services-windows-install.md)
+ [Установка сервера SQL Server 2016R (автономный)](install/sql-r-standalone-windows-install.md)
+ [Программа установки командной строки](install/sql-ml-component-commandline-install.md)
+ [Автономной установки (без Интернет)](install/sql-ml-component-install-without-internet-access.md)

### <a name="configuration"></a>Конфигурация

В следующих статьях содержатся сведения о значения по умолчанию, а также настройке конфигурации для машинного обучения на экземпляр:

+ [Изменение пула учетных записей пользователей для SQL Server R Services](r/modify-the-user-account-pool-for-sql-server-r-services.md)  
+ [Настройка и Управление расширениями углубленной аналитики](r/configure-and-manage-advanced-analytics-extensions.md)  
+ [Создание пула ресурсов](r/how-to-create-a-resource-pool-for-r.md)
+ [Оптимизация для рабочих нагрузок R](r/operationalizing-your-r-code.md)
