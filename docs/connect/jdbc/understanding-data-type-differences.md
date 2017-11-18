---
title: "Различия типов изучения данных | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ab8fa00f-cb16-47e2-94b8-3a76f56c2b84
caps.latest.revision: 33
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1a0068e98ab284ff3fbe89a7047cf485ecb5ef4b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="understanding-data-type-differences"></a>Общие сведения о различиях типов данных
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Существует ряд различий между типами данных языка программирования Java и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] типов данных. [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] Помогает уменьшить значимость этих различий посредством различных преобразований.  
  
## <a name="character-types"></a>Символьные типы  
 Типами данных символьных строк JDBC являются **CHAR**, **VARCHAR**, и **LONGVARCHAR**. Драйвер JDBC обеспечивает поддержку API-интерфейса JDBC 4.0. В JDBC 4.0 типами данных символьных строк JDBC могут также быть **NCHAR**, **NVARCHAR**, и **LONGNVARCHAR**. Эти новые типы символьных строк поддерживают собственные символьные типы Java в формате Юникода и исключают необходимость выполнять какие-либо преобразования из ANSI в Юникод или из Юникода в ANSI.  
  
|Тип|Description|  
|----------|-----------------|  
|Фиксированная длина|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **Char** и **nchar** типы данных сопоставляются непосредственно с JDBC **CHAR** и **NCHAR** типов. Они представляют собой типы фиксированной длины с заполнением, предоставляемым сервером, при условии, что для столбца установлено значение SET ANSI_PADDING ON. Заполнение всегда включено для **nchar**, но для **char**, в случае, если на сервере столбцов символьных типов не предусмотрено, заполнение добавляет драйвер JDBC.|  
|Переменная длина|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **Varchar** и **nvarchar** типы непосредственно сопоставляются с JDBC **VARCHAR** и **NVARCHAR** соответственно.|  
|Long|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **Текст** и **ntext** типы сопоставляются с JDBC **LONGVARCHAR** и **LONGNVARCHAR** введите соответственно. Эти типы являются устаревшими начиная с версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)], поэтому следует использовать типы больших значений **varchar(max)** или **nvarchar(max)**, вместо этого.<br /><br /> С помощью обновления\<числового типа > и [updateObject (int, java.lang.Object)](../../connect/jdbc/reference/updateobject-method-int-java-lang-object.md) методы завершится ошибкой для **текст** и **ntext** server столбцов. Однако использование [setObject](../../connect/jdbc/reference/setobject-method-sqlserverpreparedstatement.md) метод с указанным символьным типом преобразования поддерживается для **текст** и **ntext** server столбцов.|  
  
## <a name="binary-string-types"></a>Типы двоичных строк  
 Типами двоичных строк JDBC являются **ДВОИЧНЫХ**, **VARBINARY**, и **LONGVARBINARY**.  
  
|Тип|Description|  
|----------|-----------------|  
|Фиксированная длина|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **Двоичных** введите прямо сопоставляется с JDBC **ДВОИЧНЫХ** типа. Это тип фиксированной длины с заполнением, предоставляемым сервером в случае, если для столбца установлено значение SET ANSI_PADDING ON. Если на сервере заполнение для столбцов символьных типов не предусмотрено, то заполнение добавляет драйвер JDBC.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **Timestamp** тип — JDBC **ДВОИЧНЫХ** тип с фиксированной длиной 8 байт.|  
|Переменная длина|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **Varbinary** сопоставляется JDBC **VARBINARY** типа.<br /><br /> **Определяемого пользователем типа** введите [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] сопоставляется с JDBC как **VARBINARY** типа.|  
|Long|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **Изображения** сопоставляется JDBC **LONGVARBINARY** типа. Этот тип является устаревшим, начиная с версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)], поэтому следует использовать тип больших значений **varbinary(max)** вместо него.|  
  
## <a name="exact-numeric-types"></a>Точные числовые типы  
 Точные числовые типы JDBC непосредственно сопоставляются с аналогичными типами SQL Server.  
  
|Тип|Description|  
|----------|-----------------|  
|BIT|JDBC **бит** тип представляет единственный бит, который может быть 0 или 1. Он сопоставляется с [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **бит** типа.|  
|TINYINT|JDBC **TINYINT** тип представляет один байт. Он сопоставляется с [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **tinyint** типа.|  
|SMALLINT|JDBC **SMALLINT** тип представляет 16-разрядное знаковое целое число. Он сопоставляется с [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **smallint** типа.|  
|INTEGER|JDBC **целое** тип представляет 32-разрядное знаковое целое число. Он сопоставляется с [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **int** типа.|  
|bigint|JDBC **BIGINT** тип представляет 64-разрядное знаковое целое число. Он сопоставляется с [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **bigint** типа.|  
|NUMERIC|JDBC **ЧИСЛОВОЕ** тип представляет значение десятичного числа постоянной точности, которое хранит значения идентичной точности. **ЧИСЛОВОЕ** тип сопоставляется [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **числовое** типа.|  
|DECIMAL|JDBC **ДЕСЯТИЧНОЕ** тип представляет значение десятичного числа постоянной точности, которое хранит значения по крайней мере указанной точности. **ДЕСЯТИЧНОЕ** тип сопоставляется [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **десятичное** типа.<br /><br /> JDBC **ДЕСЯТИЧНОЕ** тип сопоставляется с [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **money** и **smallmoney** типы, которые являются определенных типов десятичное число двойной точности, хранящихся в 8 и 4 байт, соответственно.|  
  
## <a name="approximate-numeric-types"></a>Приблизительные числовые типы  
 Приблизительными числовыми типами JDBC являются **РЕАЛЬНЫЕ**, **ДВОЙНЫЕ**, и **FLOAT**.  
  
|Тип|Description|  
|----------|-----------------|  
|REAL|JDBC **РЕАЛЬНЫЕ** тип имеет семь цифр точности (одинарная точность) и сопоставляется непосредственно с [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **реальные** типа.|  
|DOUBLE|JDBC **ДВОЙНЫЕ** тип имеет 15 цифр точности (двойная точность) и сопоставляется с [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **float** типа. JDBC **FLOAT** тип является синонимом **ДВОЙНЫЕ**. Из-за возможной путаницей между **FLOAT** и **ДВОЙНЫЕ**, **ДВОЙНЫЕ** является предпочтительным.|  
  
## <a name="datetime-types"></a>Типы даты и времени  
 JDBC **TIMESTAMP** тип сопоставляется [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **datetime** и **smalldatetime** типов. **Datetime** тип хранится в двух 4-байтовые целые числа. **Smalldatetime** тип хранит ту же информацию (дату и время), но с меньшей точностью, в два 2-байтовые двухбайтовые целые числа.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **Timestamp** тип — это тип двоичной строки фиксированной длины. Он не соответствует времени типами JDBC: **даты**, **время**, или **TIMESTAMP**.  
  
## <a name="custom-type-mapping"></a>Сопоставление пользовательских типов  
 Функция сопоставления пользовательских типов JDBC, использующее интерфейсы данных SQL для JDBC расширенные типы (определяемые пользователем типы, структуры и т. д.). не реализовано в драйвере JDBC.  
  
## <a name="see-also"></a>См. также:  
 [Основные сведения о типах данных драйвера JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  

