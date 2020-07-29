---
title: Примеры приложений JDBC Driver
description: Примеры приложений JDBC Driver for SQL Server демонстрируют различные функции и практические рекомендации по программированию, которых следует придерживаться при использовании драйвера JDBC.
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e136b87c-a138-45d6-8c3e-bcef94b7e483
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 17479d32cd752650b4bfb1d03f5bc36ab52d8ca4
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86915920"
---
# <a name="sample-jdbc-driver-applications"></a>Примеры приложений JDBC Driver

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Примеры приложений [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] демонстрируют различные функции драйвера JDBC. Кроме того, они демонстрируют хороший стиль программирования, которого можно придерживаться при использовании драйвера JDBC с базой данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

Все образцы приложений содержатся в файлах кода *.java. Их можно откомпилировать и запустить на локальном компьютере. Они расположены в различных вложенных папках в следующих расположениях:

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples
```

В подразделах данного раздела описан порядок настройки и выполнения образцов приложений, приводится обсуждение результатов работы образцов приложений.

## <a name="in-this-section"></a>В этом разделе

| Раздел                                                                            | Описание                                                                                                                                                                                                                                                             |
| -------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Подключение к данным и их извлечение](connecting-and-retrieving-data.md)              | Эти примеры приложений показывают, как подключиться к базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Они также демонстрируют различные способы получения данных из базы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. |
| [Работа с типами данных (JDBC)](working-with-data-types-jdbc.md)        | Эти примеры приложений показывают, как использовать методы драйвера JDPC для работы с различными типами данных в базе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].                                                                                           |
| [Работа с результирующими наборами](working-with-result-sets.md)                          | Эти примеры приложений показывают, как использовать результирующие наборы для обработки данных, содержащихся в базе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].                                                                                                         |
| [Работа с большими объемами данных](working-with-large-data.md)                            | Эти примеры приложений показывают, как использовать адаптивную буферизацию для извлечения данных большого размера из базы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и при этом избежать излишней нагрузки, связанной с использованием серверных курсоров.                                                      |
| [Обнаружение и классификация данных SQL](data-discovery-classification-sample.md) | В этом примере приложения показано, как получить информацию об обнаружении и классификации данных, содержащуюся в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], из объекта ResultSet с помощью драйвера JDBC.                                         |

## <a name="see-also"></a>См. также раздел

[Общие сведения о JDBC Driver](overview-of-the-jdbc-driver.md)
