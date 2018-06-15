---
title: Поддержка XML-данных | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 32b7217e-1f0c-473d-9a45-176daa81584e
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 56c724017d364f3e581a6f4add22ece0091a2406
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32851719"
---
# <a name="supporting-xml-data"></a>Поддержка XML-данных
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] предоставляет **xml** тип данных, который позволяет хранить XML-документы и фрагменты в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных. **Xml** тип данных является встроенным типом данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]и в чем-то напоминающий другие встроенные типы, такие как **int** и **varchar**. Как и другие встроенные типы можно использовать **xml** как тип данных: тип переменной, тип параметра, тип возвращаемой функции или столбца тип при создании таблицы, а также в [!INCLUDE[tsql](../../includes/tsql_md.md)] функций CAST и CONVERT. В драйвере JDBC **xml** могут быть сопоставлены типу данных String, массив байтов, поток, объект CLOB, BLOB или SQLXML. Строка является средством сопоставления по умолчанию.  
  
 Драйвер JDBC обеспечивает поддержку API JDBC 4.0, который реализует интерфейс SQLXML. Интерфейс SQLXML определяет методы для обмена данными XML и их обработки. **SQLXML** является типом данных JDBC 4.0 и сопоставляется [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **xml** тип данных. Следовательно, для использования типа данных SQLXMLв приложениях необходимо задать путь к классу, включающий файл sqljdbc4.jar. Если приложение использует файл sqljdbc3.jar при обращении к объекту SQLXML и его методам, возникает исключение.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] всегда производит проверку XML-данные перед их передачей в столбце базы данных. Приложения могут использовать **SQLXML** тип данных, так как драйвер JDBC сопоставляет его **xml** типа данных. **SQLXML** поддержка доступна в пакете sqljdbc4.jar. В разделе [требования к системе для драйвера JDBC](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md) список версий JRE, поддерживаемых [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)].  
  
 В подразделах этого раздела описывается интерфейс SQLXML и как программировать **SQLXML** тип данных с помощью API методов JDBC.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Интерфейс SQLXML](../../connect/jdbc/sqlxml-interface.md)|Описывает интерфейс SQLXML и его методы.|  
|[Программирование с SQLXML](../../connect/jdbc/programming-with-sqlxml.md)|Описывает использование [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] методов API для хранения и извлечения XML-данных в реляционной базе данных с **SQLXML** типа данных. Также содержит сведения о типах объектов SQLXML и список основных рекомендаций и ограничений при работе с объектами SQLXML.|  
  
## <a name="see-also"></a>См. также  
 [Основные сведения о типах данных драйвера JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  
