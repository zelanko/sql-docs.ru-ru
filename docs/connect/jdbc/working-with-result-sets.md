---
title: Работа с результирующим наборами | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4fc4b1c6-3075-4ad7-9244-865d9ede7ae6
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d38cb92fbbf83f9b8a110d2e17f60af70c177ab4
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "69025441"
---
# <a name="working-with-result-sets"></a>Работа с результирующими наборами

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Во время работы с данными, содержащимися в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], одним из способов обработки данных является использование результирующего набора. Драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] поддерживает работу с результирующими наборами через объект [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md). С помощью объекта SQLServerResultSet можно получить данные, возвращенные инструкцией SQL или хранимой процедурой, обновить данные в случае необходимости, а затем снова сохранить данные в базе данных.  
  
Кроме того, объект SQLServerResultSet предоставляет методы для перехода по строкам данных, получения или задания данных, содержащихся в наборе, а также для настройки различных уровней учета изменений в базовой базе данных.  
  
> [!NOTE]  
> Дополнительные сведения об управлении результирующими наборами, включая порядок учета изменений, см. в статье [Управление результирующими наборами с помощью драйвера JDBC](../../connect/jdbc/managing-result-sets-with-the-jdbc-driver.md).  
  
Здесь представлены разделы, где описываются различные способы использования результирующего набора для обработки данных, содержащихся в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="in-this-section"></a>В этом разделе  
  
| Раздел                                                                                        | Описание                                                                                                                                                                                          |
| -------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Пример получения данных результирующего набора](../../connect/jdbc/retrieving-result-set-data-sample.md) | Описывает использование результирующего набора для получения данных из базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и их отображения.                                                         |
| [Изменение примера данных результирующего набора](../../connect/jdbc/modifying-result-set-data-sample.md)   | Описывается использование результирующего набора для вставки, получения и изменения данных в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].                                                      |
| [Пример кэширования данных результирующего набора](../../connect/jdbc/caching-result-set-data-sample.md)       | Описывается использование результирующего набора для получения данных большого объема из базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и управления кэшированием этих данных в клиенте. |
  
## <a name="see-also"></a>См. также раздел

 [Примеры приложений JDBC Driver](../../connect/jdbc/sample-jdbc-driver-applications.md)  
  
