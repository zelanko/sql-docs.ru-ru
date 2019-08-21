---
title: Примеры приложений драйвера JDBC | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e136b87c-a138-45d6-8c3e-bcef94b7e483
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6ef5c2d71d398be52ebed2b69020e87d54818176
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028307"
---
# <a name="sample-jdbc-driver-applications"></a>Примеры приложений JDBC Driver

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

Примеры приложений [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] демонстрируют различные функции драйвера JDBC. Кроме того, они демонстрируют хороший стиль программирования, которого можно придерживаться при использовании драйвера JDBC с базой данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
Все образцы приложений содержатся в файлах кода *.java. Их можно откомпилировать и запустить на локальном компьютере. Они расположены в различных вложенных папках в следующих расположениях:  

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples  
```

 В подразделах данного раздела описан порядок настройки и выполнения образцов приложений, приводится обсуждение результатов работы образцов приложений.  
  
## <a name="in-this-section"></a>В этом разделе  
  
| Раздел                                                                                                                  | Описание                                                                                                                                                                                                                                                                   |
| ---------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Подключение к данным и их извлечение](../../../connect/jdbc/code-samples/connecting-and-retrieving-data.md)                              | Эти примеры приложений показывают, как подключиться к базе данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Они также демонстрируют различные способы получения данных из базы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. |
| [Работа с типами данных (JDBC)](../../../connect/jdbc/code-samples/working-with-data-types-jdbc.md)                        | Эти примеры приложений показывают, как использовать методы драйвера JDPC для работы с различными типами данных в базе [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].                                                                                              |
| [Работа с результирующими наборами](../../../connect/jdbc/code-samples/working-with-result-sets.md)                                          | Эти примеры приложений показывают, как использовать результирующие наборы для обработки данных, содержащихся в базе [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].                                                                                                            |
| [Работа с большими объемами данных](../../../connect/jdbc/code-samples/working-with-large-data.md)                                            | Эти примеры приложений показывают, как использовать адаптивную буферизацию для извлечения данных большого размера из базы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и при этом избежать излишней нагрузки, связанной с использованием серверных курсоров.                                                         |
| [Обнаружение и классификация данных SQL](../../jdbc/code-samples/data-discovery-and-classification-sample.md) | В этом примере приложения показано, как получить сведения об обнаружении данных и классификации [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , содержащиеся в базе данных, из объекта ResultSet с помощью драйвера JDBC.                                            |
  
## <a name="see-also"></a>См. также раздел

[Общие сведения о JDBC Driver](../../../connect/jdbc/overview-of-the-jdbc-driver.md)
