---
title: Основные сведения о типах данных драйвера JDBC | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 7802328d-4d23-4775-9573-4169b127d258
caps.latest.revision: 27
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 399037b5f888c767edf28c40c0658d31e8703ddc
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32851379"
---
# <a name="understanding-the-jdbc-driver-data-types"></a>Основные сведения о типах данных драйвера JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] поддерживает использование типов базовых и расширенных данных JDBC внутри приложения Java, использующего [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] качестве своей базы данных.  
  
 Система типов JDBC является посредником преобразование между [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] типы данных и типы языка Java и объекты. Типы JDBC моделируются на основе типов SQL-92 и SQL-99. Драйвер JDBC соответствует требованиям JDBC и разработан для обеспечения правильного баланса между предсказуемостью и гибкостью.  
  
 В подразделах данного раздела приводится описание использования базовых и расширенных типов данных и преобразования типов данных в другие типы данных.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Использование базовых типов данных](../../connect/jdbc/using-basic-data-types.md)|Описывает базовые типы данных JDBC. Включает примеры работы с типами данных при помощи результирующих наборов, параметризованных запросов и хранимых процедур.|  
|[Настройка способа отправки значений java.sql.Time на сервер](../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md)|Описывает создание дат драйвером JDBC.|  
|[Использование расширенных типов данных](../../connect/jdbc/using-advanced-data-types.md)|Описывает расширенные типы данных JDBC.|  
|[Общие сведения о различиях типов данных](../../connect/jdbc/understanding-data-type-differences.md)|Описывает отличия между различными типами данных драйвера JDBC.|  
|[Общие сведения о преобразованиях типов данных](../../connect/jdbc/understanding-data-type-conversions.md)|Описывает преобразование типов данных при использовании методов считывания и задания.|  
|[Поддержка национального набора символов](../../connect/jdbc/national-character-set-support.md)|Описывает поддержку типов наборов национальных символов.|  
|[Поддержка XML-данных](../../connect/jdbc/supporting-xml-data.md)|Описывает интерфейс SQLXML. Также описывает, как для чтения и записи XML-данных из реляционной базы данных с **SQLXML** типа данных.|  
|[Оболочки и интерфейсы](../../connect/jdbc/wrappers-and-interfaces.md)|Описываются интерфейсы, имеющие [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] методы и константы, которые позволяют серверу приложений создать прокси-класса, а также обсуждается поддержка интерфейса java.sql.Wrapper.|  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о драйвере JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
