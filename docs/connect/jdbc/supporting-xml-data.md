---
title: Поддержка XML-данных | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 32b7217e-1f0c-473d-9a45-176daa81584e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f98ef1cbff732bc969b8eea45ad38ee2f158fa73
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47622062"
---
# <a name="supporting-xml-data"></a>Поддержка XML-данных
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] содержит тип данных **xml**, который позволяет хранить XML-документы и фрагменты в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Тип данных **xml** — это встроенный в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных, несколько напоминающий другие встроенные типы данных, такие как **int** и **varchar**. Аналогично другим встроенным типам, тип данных **xml** можно использовать следующим образом: как тип переменной, тип параметра, тип возвращаемой функции или тип столбца при создании таблицы, а также в функциях CAST и CONVERT [!INCLUDE[tsql](../../includes/tsql-md.md)]. В драйвере JDBC тип данных **xml** может быть сопоставлен со строкой, байтовым массивом, потоком или объектом CLOB, BLOB или SQLXML. Строка является средством сопоставления по умолчанию.  
  
 Драйвер JDBC обеспечивает поддержку API JDBC 4.0, который реализует интерфейс SQLXML. Интерфейс SQLXML определяет методы для обмена данными XML и их обработки. **SQLXML** является типом данных JDBC 4.0 и сопоставляется с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **xml** тип данных. Следовательно, для использования типа данных SQLXMLв приложениях необходимо задать путь к классу, включающий файл sqljdbc4.jar. Если приложение использует файл sqljdbc3.jar при обращении к объекту SQLXML и его методам, возникает исключение.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] всегда производит проверку XML-данных, прежде чем сохранить их в столбце базы данных. В приложениях можно использовать тип данных **SQLXML**, так как драйвер JDBC автоматически сопоставляет его с типом данных **xml**. Поддержка типа данных **SQLXML** доступна в пакете sqljdbc4.jar. См. в разделе [требования к системе для драйвера JDBC](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md) список версий JRE, поддерживаемых [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)].  
  
 В этом разделе описывается интерфейс SQLXML и программирование с использованием типа данных **SQLXML** с помощью методов API JDBC.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Интерфейс SQLXML](../../connect/jdbc/sqlxml-interface.md)|Описывает интерфейс SQLXML и его методы.|  
|[Программирование с SQLXML](../../connect/jdbc/programming-with-sqlxml.md)|Описывает порядок использования методов API [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] для сохранения и извлечения XML-данных в реляционной базе данных с помощью типа данных Java **SQLXML**. Также содержит сведения о типах объектов SQLXML и список основных рекомендаций и ограничений при работе с объектами SQLXML.|  
  
## <a name="see-also"></a>См. также:  
 [Основные сведения о типах данных драйвера JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  
