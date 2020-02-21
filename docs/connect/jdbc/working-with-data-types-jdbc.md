---
title: Работа с типами данных (JDBC) | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b39f44d0-3710-4bc6-880c-35bd8c10a734
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 19d75051b03a3d6d966961e681e9ce9d70396e86
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "76934446"
---
# <a name="working-with-data-types-jdbc"></a>Работа с типами данных (JDBC)

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Основная функция [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] — предоставить разработчикам на Java доступ к данным в базах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. С этой целью драйвер JDBC контролирует преобразование между типами данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и типами и объектами языка Java.  
  
> [!NOTE]  
> Подробные сведения о [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и типах данных JDBC Driver, в том числе об их отличиях и о преобразовании в типы данных языка Java, см. в статье [Основные сведения о типах данных JDBC Driver](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md).  
  
Для совместимости с типами данных SQL Server драйвер JDBC предоставляет методы get\<Type> и set\<Type> для классов [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) и [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md), а также методы get\<Type> и update\<Type> для класса [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md). Применяемый метод зависит от типа обрабатываемых данных, а также от использования либо результирующих наборов, либо запросов.  
  
В этом разделе описано использование типов данных драйвера JDBC для доступа к данным [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в приложениях Java.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Пример базовых типов данных](../../connect/jdbc/basic-data-types-sample.md)|Описывает использование методов получения результирующих наборов для извлечения значений с базовыми типами данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а также применение методов обновления результирующего набора для изменения этих значений.|  
|[Пример типа данных SQLXML](../../connect/jdbc/sqlxml-data-type-sample.md)|Описывает сохранение данных XML в реляционной базе данных, их извлечение из базы и выполнение их анализа с помощью типа данных Java **SQLXML**.|  
|[Пример пространственных типов данных](../../connect/jdbc/spatial-data-types-sample.md)|Показывает, как хранить и загружать данные с пространственными типами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] данных geometry и geography в базе с **геометрией** и **географией** языка Java, определяемыми драйвером Microsoft JDBC.|

## <a name="see-also"></a>См. также раздел

[Примеры приложений JDBC Driver](../../connect/jdbc/sample-jdbc-driver-applications.md)  
