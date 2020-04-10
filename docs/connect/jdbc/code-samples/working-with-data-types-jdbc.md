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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d05200ff0c634ea327e58e5288ff8e99c0ec9418
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80922558"
---
# <a name="working-with-data-types-jdbc"></a>Работа с типами данных (JDBC)

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

Основная функция [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] — предоставить разработчикам на Java доступ к данным в базах [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. С этой целью драйвер JDBC контролирует преобразование между типами данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и типами и объектами языка Java.  
  
> [!NOTE]  
> Подробные сведения о [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и типах данных JDBC Driver, в том числе об их отличиях и о преобразовании в типы данных языка Java, см. в статье [Основные сведения о типах данных JDBC Driver](../../../connect/jdbc/understanding-the-jdbc-driver-data-types.md).  
  
Для совместимости с типами данных SQL Server драйвер JDBC предоставляет методы get\<Type> и set\<Type> для классов [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) и [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md), а также методы get\<Type> и update\<Type> для класса [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md). Применяемый метод зависит от типа обрабатываемых данных, а также от использования либо результирующих наборов, либо запросов.  
  
В этом разделе описано использование типов данных драйвера JDBC для доступа к данным [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в приложениях Java.  
  
## <a name="in-this-section"></a>В этом разделе  
  
| Раздел                                                                         | Description                                                                                                                                                                                                                                                  |
| ----------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [Пример базовых типов данных](../../../connect/jdbc/code-samples/basic-data-types-sample.md)   | Описывает использование методов получения результирующих наборов для извлечения значений с базовыми типами данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], а также применение методов обновления результирующего набора для изменения этих значений.                                             |
| [Пример типа данных SQLXML](../../../connect/jdbc/code-samples/sqlxml-data-type-sample.md)   | Описывает сохранение данных XML в реляционной базе данных, их извлечение из базы и выполнение их анализа с помощью типа данных Java **SQLXML**.                                                                                   |
| [Пример пространственных типов данных](../../../connect/jdbc/code-samples/spatial-data-types-sample.md) | Сведения о том, как сохранять пространственные типы данных в SQL Server и как получать такие типы обратно из SQL Server. Также обсуждается использование недавно добавленных классов драйвера **Geometry** и **Geography** путем управления ссылками на эти типы данных в Java. |
  
## <a name="see-also"></a>См. также раздел

[Примеры приложений JDBC Driver](../../../connect/jdbc/code-samples/sample-jdbc-driver-applications.md)  
