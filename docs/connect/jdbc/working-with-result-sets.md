---
title: Работа с результирующими наборами
description: Узнайте, как работать с большими данными с помощью результирующих наборов в драйвере JDBC для SQL Server в этих примерах приложений.
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4fc4b1c6-3075-4ad7-9244-865d9ede7ae6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 82618ee27e1aa32716fe4b4d3817ff0128baebab
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86921030"
---
# <a name="working-with-result-sets"></a>Работа с результирующими наборами

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Во время работы с данными, содержащимися в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], одним из способов обработки данных является использование результирующего набора. Драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] поддерживает работу с результирующими наборами через объект [SQLServerResultSet](reference/sqlserverresultset-class.md). С помощью объекта SQLServerResultSet можно получить данные, возвращенные инструкцией SQL или хранимой процедурой, обновить данные в случае необходимости, а затем снова сохранить данные в базе данных.

Кроме того, объект SQLServerResultSet предоставляет методы для перехода по строкам данных, получения или задания данных, содержащихся в наборе, а также для настройки различных уровней учета изменений в базовой базе данных.

> [!NOTE]
> Дополнительные сведения об управлении результирующими наборами, включая порядок учета изменений, см. в статье [Управление результирующими наборами с помощью драйвера JDBC](managing-result-sets-with-the-jdbc-driver.md).

Здесь представлены разделы, где описываются различные способы использования результирующего набора для обработки данных, содержащихся в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

## <a name="in-this-section"></a>В этом разделе

| Раздел                                                                     | Описание                                                                                                                                                                                          |
| ------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Пример получения данных результирующего набора](retrieving-result-set-data-sample.md) | Описывает использование результирующего набора для получения данных из базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и их отображения.                                                         |
| [Изменение примера данных результирующего набора](modifying-result-set-data-sample.md)   | Описывается использование результирующего набора для вставки, получения и изменения данных в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].                                                      |
| [Пример кэширования данных результирующего набора](caching-result-set-data-sample.md)       | Описывается использование результирующего набора для получения данных большого объема из базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и управления кэшированием этих данных в клиенте. |

## <a name="see-also"></a>См. также раздел

[Примеры приложений JDBC Driver](sample-jdbc-driver-applications.md)
