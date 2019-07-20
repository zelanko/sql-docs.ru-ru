---
title: Устранение неполадок и вопросы и ответы по машинному обучению
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/31/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 0cd9b4808d361cdbfa661feb31134da46baec3de
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/19/2019
ms.locfileid: "68344989"
---
# <a name="troubleshoot-machine-learning-in-sql-server"></a>Устранение неполадок машинного обучения в SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Используйте эту страницу в качестве отправной точки для работы с известными проблемами.

**Применимо к:** SQL Server 2016 служб R SQL Server 2017 Службы машинного обучения (R и Python)

## <a name="known-issues"></a>Известные проблемы

В следующих статьях описываются известные проблемы текущего и предыдущего выпусков.

+ [Известные проблемы со службами R](../advanced-analytics/known-issues-for-sql-server-machine-learning-services.md)
+ [Заметки о выпуске для SQL Server 2016](../sql-server/sql-server-2016-release-notes.md)
+ [Заметки о выпуске для SQL Server 2017](../sql-server/sql-server-2017-release-notes.md)

## <a name="how-to-gather-system-information"></a>Сбор сведений о системе

Если вы столкнулись с ошибкой или хотите разобраться в своей среде, важно систематически выполнять соотношение связанных данных. В следующей статье представлен список сведений, упрощающих устранение неполадок самостоятельно, или запрос на техническую поддержку.

+ [Сбор данных для устранения неполадок машинного обучения](data-collection-ml-troubleshooting-process.md)

## <a name="setup-and-configuration-guides"></a>Руководства по установке и настройке

Начните здесь, если вы не настроили машинное обучение с помощью SQL Server или хотите добавить эту функцию:

+ [Установка SQL Server 2017 Службы машинного обучения (в базе данных)](install/sql-machine-learning-services-windows-install.md)
+ [Установка SQL Server Machine Learning Server 2017 (автономная версия)](install/sql-machine-learning-standalone-windows-install.md)
+ [Установка служб R SQL Server 2016 (в базе данных)](install/sql-r-services-windows-install.md)
+ [Установка SQL Server R Server 2016 (изолированная версия)](install/sql-r-standalone-windows-install.md)
+ [Установка командной строки](install/sql-ml-component-commandline-install.md)
+ [Автономная установка (без Интернета)](install/sql-ml-component-install-without-internet-access.md)

### <a name="configuration"></a>Конфигурация

Следующие статьи содержат сведения о значениях по умолчанию и о настройке конфигурации для машинного обучения в экземпляре.

+ [Масштабирование параллельного выполнения внешних скриптов в SQL Server Службы машинного обучения](administration/modify-user-account-pool.md)   
+ [Настройка расширений углубленной аналитики и управление ими](r/configure-and-manage-advanced-analytics-extensions.md)  
+ [Создание пула ресурсов](r/how-to-create-a-resource-pool-for-r.md)
+ [Оптимизация для рабочих нагрузок R](r/operationalizing-your-r-code.md)
