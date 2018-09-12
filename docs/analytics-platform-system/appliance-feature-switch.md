---
title: Функция Switch (Analytics Platform System)
description: Отображает сведения о параметрах две функции, представленные в AU7 системы платформы аналитики.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 06/27/2018
ms.author: murshedz
ms.reviewer: martinle
monikerRange: '>= aps-pdw-2016-au7 || = sqlallproducts-allversions'
ms.openlocfilehash: 70eed88b1224a712dcb8d1c76085fffc839155a5
ms.sourcegitcommit: 8008ea52e25e65baae236631b48ddfc33014a5e0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2018
ms.locfileid: "44311644"
---
#<a name="appliance-feature-switches"></a>Параметры функций устройства
**Переключатель** странице отображаются сведения о параметрах функции, которые вводятся в AU7 системы платформы аналитики и более поздних версий. Эта страница конфигурации для обновления или включение или отключение функциях и параметрах в Analytics Platform System. Изменения значений переключателя функции требуют перезапуска службы.

![Параметр компонента устройства DWConig](media/feature-switch/SQL_Server_PDW_DWConfig_feature_switch.png "DWConig устройства функция Switch") 

##<a name="autostatsenabled"></a>AutoStatsEnabled
Определяет функцию автоматического статистики. Этот компонент переключатель установлен в значение true, по умолчанию после обновления до AU7. Любой базы данных, созданные после обновления будут наследовать автоматическое создание и асинхронного обновления статистики. Для существующих баз данных, администраторы баз данных можно включить автоматическое статистики с [ALTER DATABASE (Parallel Data Warehouse)](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw). Дополнительные сведения о статистике см. в разделе [статистики](../relational-databases/statistics/statistics.md).

##<a name="usecatalogqueries"></a>UseCatalogQueries
Использование объектов каталога для вызовов некоторых метаданных вместо использования SMO показали повышение производительности. Значение true по умолчанию в CU7.1, этот параметр контролирует это поведение. 

##<a name="dmsprocessstopmessagetimeoutinseconds"></a>DmsProcessStopMessageTimeoutInSeconds
Определяет время ожидания службы перемещения данных (DMS) для синхронизации на занятой системе, когда отменяется запрос, включающий перемещения данных. По умолчанию обновление до AU7 задает это значение 900 секунд (15 минут). Допустимый диапазон: 0 – 3600 секунд.
