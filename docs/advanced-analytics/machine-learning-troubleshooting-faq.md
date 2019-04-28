---
title: Устранение неполадок и часто задаваемые вопросы о машинное обучение — службы SQL Server машинного обучения
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/31/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 4a62dd0710a97a33f5a4703f194df2c6bcef2a54
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62650331"
---
# <a name="troubleshoot-machine-learning-in-sql-server"></a>Устранение неполадок машинного обучения в SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Используйте эту страницу в качестве отправной точки для работы через известные проблемы.

**Применимо к:** Службы R SQL Server 2016, SQL Server 2017 службы машинного обучения (R и Python)

## <a name="known-issues"></a>Известные проблемы

В следующих статьях описываются известные проблемы с текущих и предыдущих выпусках:

+ [Известные проблемы со службами R](../advanced-analytics/known-issues-for-sql-server-machine-learning-services.md)
+ [Заметки о выпуске для SQL Server 2016](../sql-server/sql-server-2016-release-notes.md)
+ [Заметки о выпуске для SQL Server 2017](../sql-server/sql-server-2017-release-notes.md)

## <a name="how-to-gather-system-information"></a>Как собирать сведения о системе

Если произошла ошибка, или должны понимать проблемы в вашей среде, важно собрать систематически связанные сведения. Следующие статьи список сведений, который облегчает Устранение неполадок самостоятельного решения проблем или запрос для получения технической поддержки.

+ [Сбор данных для устранения неполадок машинного обучения](data-collection-ml-troubleshooting-process.md)

## <a name="setup-and-configuration-guides"></a>Руководства по установке и настройке

Начните отсюда, если вы не настроили машинного обучения с использованием SQL Server, или если вы хотите добавить компонент:

+ [Установка служб SQL Server 2017 машинного обучения (в базе данных)](install/sql-machine-learning-services-windows-install.md)
+ [Установка сервера SQL Server 2017 машинного обучения (изолированного)](install/sql-machine-learning-standalone-windows-install.md)
+ [Установка служб R SQL Server 2016 (в базе данных)](install/sql-r-services-windows-install.md)
+ [Установка SQL Server 2016 R Server (изолированный)](install/sql-r-standalone-windows-install.md)
+ [Программа установки командной строки](install/sql-ml-component-commandline-install.md)
+ [Автономная установка (без Интернета)](install/sql-ml-component-install-without-internet-access.md)

### <a name="configuration"></a>Конфигурация

Следующие статьи содержат сведения о значения по умолчанию и как настроить конфигурацию для машинного обучения на экземпляр:

+ [Масштаб параллельного выполнения внешних скриптов в службах машинного обучения SQL Server](administration/modify-user-account-pool.md)   
+ [Настройка и Управление расширениями углубленной аналитики](r/configure-and-manage-advanced-analytics-extensions.md)  
+ [Создание пула ресурсов](r/how-to-create-a-resource-pool-for-r.md)
+ [Оптимизация для рабочих нагрузок R](r/operationalizing-your-r-code.md)
