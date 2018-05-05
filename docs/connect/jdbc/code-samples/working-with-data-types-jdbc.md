---
title: Работа с типами данных (JDBC) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b39f44d0-3710-4bc6-880c-35bd8c10a734
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6ccecd482516979a2f3ace2a4ce2c039af3ad1c4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="working-with-data-types-jdbc"></a>Работа с типами данных (JDBC)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Основная функция [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] позволяет разработчикам Java для доступа к данным, содержащимся в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] баз данных. Чтобы добиться этого, драйвер JDBC является посредником преобразование между [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] типы данных и типы языка Java и объекты.  
  
> [!NOTE]  
>  Подробное описание [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] и типов данных драйвера JDBC, включая различия между ними и как они преобразуются в типы данных языка Java, в разделе [основные сведения о типах данных драйвера JDBC](../../../connect/jdbc/understanding-the-jdbc-driver-data-types.md).  
  
 Для работы с типами данных SQL Server, драйвер JDBC предоставляет get\<типа > и задайте\<типа > методы для [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) и [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md) классы и предоставляет get\<типа > и обновить\<типа > методы для [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) класса. Применяемый метод зависит от типа обрабатываемых данных, а также от использования либо результирующих наборов, либо запросов.  
  
 В этом разделе описываются способы использования типов данных драйвера JDBC для доступа к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] данных в приложениях Java.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Пример базовых типов данных](../../../connect/jdbc/basic-data-types-sample.md)|Описывает использование методов считывания результирующих наборов для извлечения базовых [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] тип данных значения, а также использование методов обновления результирующего набора для обновления этих величин.|  
|[Пример типа данных SQLXML](../../../connect/jdbc/sqlxml-data-type-sample.md)|Описывает способ хранения XML-данных в реляционной базе данных, как получить XML-данных из базы данных и как выполнить синтаксический анализ XML-данных с **SQLXML** типа данных.|  
  
## <a name="see-also"></a>См. также  
 [Пример приложений драйвера JDBC](../../../connect/jdbc/sample-jdbc-driver-applications.md)  
  
  
