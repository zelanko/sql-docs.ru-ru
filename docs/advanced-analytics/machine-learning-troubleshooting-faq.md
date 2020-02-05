---
title: Устранение неполадок
description: Отправная точка для решения известных проблем.
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/31/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: c9be3a8dff314f6645029fb54803ad30dc04db27
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "73727564"
---
# <a name="troubleshoot-machine-learning-in-sql-server"></a>Устранение неполадок с машинным обучением в SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Используйте эту статью в качестве отправной точки для решения известных проблем.

## <a name="known-issues"></a>Известные проблемы

В следующих статьях описываются известные проблемы в текущем и предыдущих выпусках:

+ [Известные проблемы со службами R Services](../advanced-analytics/known-issues-for-sql-server-machine-learning-services.md)
+ [Заметки о выпуске для SQL Server 2016](../sql-server/sql-server-2016-release-notes.md)
+ [Заметки о выпуске для SQL Server 2017](../sql-server/sql-server-2017-release-notes.md)

## <a name="how-to-gather-system-information"></a>Сбор сведений о системе

Если вы столкнулись с ошибкой или хотите разобраться с проблемой в своей среде, важно собрать все связанные данные. В следующей статье представлен список сведений, упрощающих самостоятельное устранение неполадок или обращение в службу технической поддержки:

+ [Сбор данных для устранения неполадок машинного обучения](data-collection-ml-troubleshooting-process.md)

## <a name="setup-and-configuration-guides"></a>Руководства по установке и настройке

Начните со следующих статей, если вы еще не настроили машинное обучение в SQL Server или хотите добавить этот компонент:

+ [Установка служб машинного обучения SQL Server (в базе данных)](install/sql-machine-learning-services-windows-install.md)
+ [Установка SQL Server Machine Learning Server (изолированного)](install/sql-machine-learning-standalone-windows-install.md)
+ [Настройка командной строки](install/sql-ml-component-commandline-install.md)
+ [Автономная установка (без Интернета)](install/sql-ml-component-install-without-internet-access.md)

### <a name="configuration"></a>Конфигурация

В следующих статьях содержатся сведения о значениях по умолчанию и о настройке конфигурации машинного обучения в экземпляре:

+ [Масштабирование параллельного выполнения внешних сценариев в Службах машинного обучения SQL Server](administration/modify-user-account-pool.md)   
+ [Настройка и управление расширениями углубленной аналитики](r/configure-and-manage-advanced-analytics-extensions.md)  
+ [Создание пула ресурсов](r/how-to-create-a-resource-pool-for-r.md)
+ [Оптимизация для рабочих нагрузок R](r/operationalizing-your-r-code.md)
