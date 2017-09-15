---
title: "Работа с результирующими наборами | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4fc4b1c6-3075-4ad7-9244-865d9ede7ae6
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d4940b42078d0a89a7c9c3fd5834d8a5c707dfba
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="working-with-result-sets"></a>Работа с результирующими наборами
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  При работе с данными, содержащимися в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] базы данных, одним из способов обработки данных является использование результирующего набора. [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] Поддерживает результирующих наборами через [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта. С помощью объекта SQLServerResultSet, можно извлекать данные, возвращенные из инструкции SQL или хранимой процедуры, при необходимости обновите данные и затем снова сохранить данные в базу данных.  
  
 Кроме того объект SQLServerResultSet предоставляет методы для перехода по строкам данных, получения или задания данных, которые он содержит, а также для настройки различных уровней чувствительности к переменам в основной базе данных.  
  
> [!NOTE]  
>  Дополнительные сведения об управлении результирующими наборами, включая порядок учета изменений, в разделе [управление результирующие наборы с драйвером JDBC](../../../connect/jdbc/managing-result-sets-with-the-jdbc-driver.md).  
  
 В этом разделе описываются различные способы, результирующий набор можно использовать для управления данными, содержащимися в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] базы данных.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Получение примера данных результирующего набора](../../../connect/jdbc/retrieving-result-set-data-sample.md)|Описывает использование результирующего набора для получения данных из [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] базы данных и его отображения.|  
|[Изменение примера данных результирующего набора](../../../connect/jdbc/modifying-result-set-data-sample.md)|Описывает использование результирующего набора для вставки, получения и изменения данных в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] базы данных.|  
|[Пример кэширования данных результирующего набора](../../../connect/jdbc/caching-result-set-data-sample.md)|Описывает использование результирующего набора для извлечения больших объемов данных из [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] базы данных, а также для управления кэшированием этих данных на стороне клиента.|  
  
## <a name="see-also"></a>См. также:  
 [Пример приложений драйвера JDBC](../../../connect/jdbc/sample-jdbc-driver-applications.md)  
  
  
