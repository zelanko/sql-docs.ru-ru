---
title: Работа с типами данных (JDBC)
description: Узнайте, как работать с типами данных в драйвере JDBC для SQL Server, с помощью этих примеров приложений.
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
ms.openlocfilehash: 6994e7ce587cf72d7879c79604cbe3c68873ddf0
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86923289"
---
# <a name="working-with-data-types-jdbc"></a>Работа с типами данных (JDBC)

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Основная функция [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] — предоставить разработчикам на Java доступ к данным в базах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. С этой целью драйвер JDBC контролирует преобразование между типами данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и типами и объектами языка Java.

> [!NOTE]
> Подробные сведения о [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и типах данных JDBC Driver, в том числе об их отличиях и о преобразовании в типы данных языка Java, см. в статье [Основные сведения о типах данных JDBC Driver](understanding-the-jdbc-driver-data-types.md).

Для совместимости с типами данных SQL Server драйвер JDBC предоставляет методы get\<Type> и set\<Type> для классов [SQLServerPreparedStatement](reference/sqlserverpreparedstatement-class.md) и [SQLServerCallableStatement](reference/sqlservercallablestatement-class.md), а также методы get\<Type> и update\<Type> для класса [SQLServerResultSet](reference/sqlserverresultset-class.md). Применяемый метод зависит от типа обрабатываемых данных, а также от использования либо результирующих наборов, либо запросов.

В этом разделе описано использование типов данных драйвера JDBC для доступа к данным [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в приложениях Java.

## <a name="in-this-section"></a>В этом разделе

|Раздел|Описание|
|-----------|-----------------|
|[Пример базовых типов данных](basic-data-types-sample.md)|Описывает использование методов получения результирующих наборов для извлечения значений с базовыми типами данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а также применение методов обновления результирующего набора для изменения этих значений.|
|[Пример типа данных SQLXML](sqlxml-data-type-sample.md)|Описывает сохранение данных XML в реляционной базе данных, их извлечение из базы и выполнение их анализа с помощью типа данных Java **SQLXML**.|
|[Пример пространственных типов данных](spatial-data-types-sample.md)|Показывает, как хранить и загружать данные с пространственными типами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] данных geometry и geography в базе с **геометрией** и **географией** языка Java, определяемыми драйвером Microsoft JDBC.|

## <a name="see-also"></a>См. также раздел

[Примеры приложений JDBC Driver](sample-jdbc-driver-applications.md)
