---
title: Основные сведения о типах данных JDBC Driver | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 7802328d-4d23-4775-9573-4169b127d258
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 15ecca3277dcba3cd2235da9bff9a8d9fc2e4f6f
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80920275"
---
# <a name="understanding-the-jdbc-driver-data-types"></a>Основные сведения о типах данных JDBC Driver

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] поддерживает использование базовых и расширенных типов данных JDBC внутри приложения Java, использующего [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в качестве своей базы данных.  
  
С этой целью система типов драйвера JDBC включается в процесс преобразования между типами данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и типами и объектами языка Java. Типы JDBC моделируются на основе типов SQL-92 и SQL-99. Драйвер JDBC соответствует требованиям JDBC и разработан для обеспечения правильного баланса между предсказуемостью и гибкостью.  
  
В подразделах данного раздела приводится описание использования базовых и расширенных типов данных и преобразования типов данных в другие типы данных.  
  
## <a name="in-this-section"></a>В этом разделе  
  
| Раздел                                                                                                                                            | Description                                                                                                                                                                                                                                                          |
| ------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Использование базовых типов данных](../../connect/jdbc/using-basic-data-types.md)                                                                           | Описывает базовые типы данных JDBC. Включает примеры работы с типами данных при помощи результирующих наборов, параметризованных запросов и хранимых процедур.                                                                                                        |
| [Настройка способа отправки значений java.sql.Time на сервер](../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md) | Описывает создание дат драйвером JDBC.                                                                                                                                                                                                                       |
| [Использование расширенных типов данных](../../connect/jdbc/using-advanced-data-types.md)                                                                     | Описывает расширенные типы данных JDBC.                                                                                                                                                                                                                              |
| [Основные сведения о различиях между типами данных](../../connect/jdbc/understanding-data-type-differences.md)                                                 | Описывает отличия между различными типами данных драйвера JDBC.                                                                                                                                                                                                    |
| [Основные сведения о преобразованиях типов данных](../../connect/jdbc/understanding-data-type-conversions.md)                                                 | Описывает преобразование типов данных при использовании методов считывания и задания.                                                                                                                                                                                  |
| [Поддержка национального набора символов](../../connect/jdbc/national-character-set-support.md)                                                           | Описывает поддержку типов наборов национальных символов.                                                                                                                                                                                                          |
| [Поддержка данных XML](../../connect/jdbc/supporting-xml-data.md)                                                                                 | Описывает интерфейс SQLXML. Кроме того, описывается считывание из реляционной базы данных XML и запись в нее данных XML с типом данных Java **SQLXML**.                                                                                                             |
| [Оболочки и интерфейсы](../../connect/jdbc/wrappers-and-interfaces.md)                                                                         | Описываются интерфейсы, имеющие методы и константы, определяемые драйвером [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], которые позволяют серверу приложений создавать классы-посредники. Кроме того, обсуждается поддержка интерфейса `java.sql.Wrapper`. |
  
## <a name="see-also"></a>См. также раздел

[Общие сведения о JDBC Driver](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
