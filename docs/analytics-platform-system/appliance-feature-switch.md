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
ms.openlocfilehash: b06c715549cd1c9cf464a13b03790764ebf40b97
ms.sourcegitcommit: 3e5f1545e5c6c92fa32e116ee3bff1018ca946a2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/29/2018
ms.locfileid: "37107182"
---
#<a name="appliance-feature-switch"></a>Коммутатор функций устройства
**Переключатель** странице отображаются сведения о параметры двух функций, представленных в платформе аналитики System 2016-AU7. Эта страница позволяет обновить или включение или отключение функциях и параметрах в Analytics Platform System. Изменение значения параметра компонента потребуется перезапустить службу.

![Параметр компонента устройства DWConig](media/feature-switch/SQL_Server_PDW_DWConfig_feature_switch.png "DWConig устройства функция Switch") 

##<a name="autostatsenabled-switch"></a>Коммутатор AutoStatsEnabled
Определяет функцию автоматического статистики. Этот компонент переключатель установлен в значение true, по умолчанию после обновления до AU7. Любой базы данных, созданные после обновления будут наследовать автоматическое создание и асинхронного обновления статистики. Для существующих баз данных, администраторы баз данных можно включить автоматическое статистики с [alter database] (/ sql/t-sql/statements/alter-database-parallel-data-warehouse). Дополнительные сведения о статистике см. в разделе [статистики](../relational-databases/statistics/statistics.md).

##<a name="dmsprocessstopmessagetimeoutinseconds-switch"></a>Коммутатор DmsProcessStopMessageTimeoutInSeconds
Определяет время ожидания службы перемещения данных (DMS) для синхронизации на занятой системе, когда отменяется запрос, включающий перемещения данных. По умолчанию обновление до AU7 задает это значение 900 секунд (15 минут). Допустимый диапазон: 0 – 3600 секунд.
