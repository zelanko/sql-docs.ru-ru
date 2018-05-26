---
title: Функция Switch (система платформы аналитики)
description: Отображает сведения о параметрах две функции, представленные в AU7 системы платформы аналитики.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/24/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: e384a252584fed0e7543a7a4000fc9a70f6533e7
ms.sourcegitcommit: fc3cd23685c6b9b6972d6a7bab2cc2fc5ebab5f2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/25/2018
---
#<a name="appliance-feature-switch"></a>Переключение функции устройства
**Переключение функции** странице отображаются сведения о параметрах две функции, представленные в AU7 системы платформы аналитики. Эта страница служит для обновления или включение или отключение компонентов и параметров в Analytics Platform System. Для изменения значения компонента коммутатора требуется перезапуск службы.

![Переключение функции устройства DWConig](media/feature-switch/SQL_Server_PDW_DWConfig_feature_switch.png "DWConig переключение функции устройства") 

##<a name="autostatsenabled-switch"></a>Коммутатор AutoStatsEnabled
Определяет функцию автоматического статистики. Этот компонент переключатель установлен в положение true по умолчанию после обновления до AU7. Любой базы данных, созданные после обновления будут наследовать автоматического создания и асинхронного обновления статистики. Для существующих баз данных, администраторы базы данных можно включить автоматическое статистики с [инструкции alter database] (/ sql/t-sql/statements/alter-database-parallel-data-warehouse). Дополнительные сведения о статистике см. в разделе [статистики](../relational-databases/statistics/statistics.md).

##<a name="dmsprocessstopmessagetimeoutinseconds-switch"></a>Коммутатор DmsProcessStopMessageTimeoutInSeconds
Определяет время ожидания службы перемещения данных (DMS) для синхронизации данных на загруженной системе после отмены запрос, включающий перемещения данных. Обновление до AU7 это значение устанавливается равным 900 секунд (15 минут) по умолчанию. Допустимый диапазон: от 0 до 3600 секунд.
