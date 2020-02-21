---
title: Поддержка XML-данных | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 32b7217e-1f0c-473d-9a45-176daa81584e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 799b22cfac669846c606456f1911e27353a9ba9f
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "69027716"
---
# <a name="supporting-xml-data"></a>Поддержка данных XML
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] содержит тип данных **xml**, который позволяет хранить XML-документы и фрагменты в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Тип данных **xml** — это встроенный в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных, несколько напоминающий другие встроенные типы данных, такие как **int** и **varchar**. Аналогично другим встроенным типам, тип данных **xml** можно использовать следующим образом: как тип переменной, тип параметра, тип возвращаемой функции или тип столбца при создании таблицы, а также в функциях CAST и CONVERT [!INCLUDE[tsql](../../includes/tsql-md.md)]. В драйвере JDBC тип данных **xml** может быть сопоставлен со строкой, байтовым массивом, потоком или объектом CLOB, BLOB или SQLXML. Строка является средством сопоставления по умолчанию.  
  
 Драйвер JDBC обеспечивает поддержку API JDBC 4.0, который реализует интерфейс SQLXML. Интерфейс SQLXML определяет методы для обмена данными XML и их обработки. The **SQLXML** является типом данных JDBC 4.0, и он сопоставляется с типом данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**xml**. Следовательно, для использования типа данных SQLXMLв приложениях необходимо задать путь к классу, включающий файл sqljdbc4.jar. Если приложение использует файл sqljdbc3.jar при обращении к объекту SQLXML и его методам, возникает исключение.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] всегда производит проверку XML-данных, прежде чем сохранить их в столбце базы данных. В приложениях можно использовать тип данных **SQLXML**, так как драйвер JDBC автоматически сопоставляет его с типом данных **xml**. Поддержка типа данных **SQLXML** доступна в пакете sqljdbc4.jar. Список версий JRE-файлов, поддерживаемых [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], см. в описании [требований к системе для JDBC Driver](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  
  
 В этом разделе описывается интерфейс SQLXML и программирование с использованием типа данных **SQLXML** с помощью методов API JDBC.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Интерфейс SQLXML](../../connect/jdbc/sqlxml-interface.md)|Описывает интерфейс SQLXML и его методы.|  
|[Программирование с SQLXML](../../connect/jdbc/programming-with-sqlxml.md)|Описывает порядок использования методов API [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] для сохранения и извлечения XML-данных в реляционной базе данных с помощью типа данных Java **SQLXML**. Также содержит сведения о типах объектов SQLXML и список основных рекомендаций и ограничений при работе с объектами SQLXML.|  
  
## <a name="see-also"></a>См. также раздел  
 [Основные сведения о типах данных JDBC Driver](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  
