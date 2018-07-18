---
title: Устранение неполадок и вопросы и ответы для машинного обучения в SQL Server | Документы Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/31/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 6ef72ae56973e695b96f0dfac7c0a3414bca5225
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34707362"
---
# <a name="troubleshoot-machine-learning-in-sql-server"></a>Устранение неполадок машинного обучения в SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Используйте эту страницу для начала работы в рамках известных проблем.

**Применяется к:** служб R SQL Server 2016, SQL Server 2017 г машинного обучения службы (R и Python)

## <a name="known-issues"></a>Известные проблемы

В следующих статьях описывается известные проблемы с текущих и предыдущих выпусках:

+ [Известные проблемы для служб R](../advanced-analytics/known-issues-for-sql-server-machine-learning-services.md)
+ [Заметки о выпуске для SQL Server 2016](../sql-server/sql-server-2016-release-notes.md)
+ [Заметки о выпуске для SQL Server 2017](../sql-server/sql-server-2017-release-notes.md)

## <a name="how-to-gather-system-information"></a>Как собирать сведения о системе

Если произошла ошибка, или необходимо понять проблему в вашей среде, важно систематически собирать сведения. Следующие статьи список информации, которая позволяет самостоятельного устранения неполадок или запрос для получения технической поддержки.

+ [Сбор данных для устранения неполадок машинного обучения](data-collection-ml-troubleshooting-process.md)

## <a name="setup-and-configuration-guides"></a>Руководства по установке и настройке

Начните здесь, если вы не настроили машинного обучения с помощью SQL Server или если вы хотите добавить компонент:

+ [Установка служб SQL Server 2017 г машинного обучения (в базе данных)](install/sql-machine-learning-services-windows-install.md)
+ [Установка обучения машины 2017 г. сервер SQL Server (автономный)](install/sql-machine-learning-standalone-windows-install.md)
+ [Установка служб R SQL Server 2016 (в базе данных)](install/sql-r-services-windows-install.md)
+ [Установка SQL Server 2016 R Server (изолированный)](install/sql-r-standalone-windows-install.md)
+ [Программа установки командной строки](install/sql-ml-component-commandline-install.md)
+ [Автономная установка (без Интернета)](install/sql-ml-component-install-without-internet-access.md)

### <a name="configuration"></a>Конфигурация

В следующих статьях содержатся сведения о значения по умолчанию, а также настройке конфигурации для машинного обучения на экземпляр:

+ [Изменение пула учетных записей пользователей для SQL Server R Services](r/modify-the-user-account-pool-for-sql-server-r-services.md)  
+ [Настройка и Управление расширениями углубленной аналитики](r/configure-and-manage-advanced-analytics-extensions.md)  
+ [Создание пула ресурсов](r/how-to-create-a-resource-pool-for-r.md)
+ [Оптимизация для рабочих нагрузок R](r/operationalizing-your-r-code.md)
