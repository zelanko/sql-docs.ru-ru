---
title: Работа с результирующими наборами | Документация Майкрософт
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4fc4b1c6-3075-4ad7-9244-865d9ede7ae6
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9d33dbebaad162feb77a4cbea8de33993fc79f14
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67956954"
---
# <a name="working-with-result-sets"></a>Работа с результирующими наборами

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

Во время работы с данными, содержащимися в базе данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], одним из способов обработки данных является использование результирующего набора. Драйвер [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] поддерживает работу с результирующими наборами через объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md). С помощью объекта SQLServerResultSet можно получить данные, возвращенные инструкцией SQL или хранимой процедурой, обновить данные в случае необходимости, а затем снова сохранить данные в базе данных.  
  
Кроме того, объект SQLServerResultSet предоставляет методы для перехода по строкам данных, получения или задания данных, содержащихся в наборе, а также для настройки различных уровней учета изменений в базовой базе данных.  
  
> [!NOTE]  
> Дополнительные сведения об управлении результирующими наборами, включая их чувствительность к изменениям, см. в разделе [Управление результирующими наборами с помощью драйвера JDBC](../../../connect/jdbc/managing-result-sets-with-the-jdbc-driver.md).  
  
Здесь представлены разделы, где описываются различные способы использования результирующего набора для обработки данных, содержащихся в базе данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="in-this-section"></a>в этом разделе  
  
| Раздел                                                                                           | Описание                                                                                                                                                                                             |
| ----------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Получение примера данных результирующего набора](../../../connect/jdbc/code-samples/retrieving-result-set-data-sample.md) | Описывает использование результирующего набора для получения данных из базы данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и их отображения.                                                         |
| [Изменение примера данных результирующего набора](../../../connect/jdbc/code-samples/modifying-result-set-data-sample.md)   | Описывается использование результирующего набора для вставки, получения и изменения данных в базе данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].                                                      |
| [Пример кэширования данных результирующего набора](../../../connect/jdbc/code-samples/caching-result-set-data-sample.md)       | Описывается использование результирующего набора для получения данных большого объема из базы данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и управления кэшированием этих данных в клиенте. |
  
## <a name="see-also"></a>См. также:  

[Пример приложений драйвера JDBC](../../../connect/jdbc/code-samples/sample-jdbc-driver-applications.md)  
  
