---
title: Общие сведения о данных введите различия | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ab8fa00f-cb16-47e2-94b8-3a76f56c2b84
caps.latest.revision: 33
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5395b915d2f261813495d364730d0442a8139334
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "37992946"
---
# <a name="understanding-data-type-differences"></a>Общие сведения о различиях типов данных
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Есть целый ряд различий между типами данных языка программирования Java и типами данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] помогает уменьшить значимость этих различий посредством различных преобразований.  
  
## <a name="character-types"></a>Символьные типы  
 Типами данных символьных строк JDBC являются **CHAR**, **VARCHAR**, и **LONGVARCHAR**. Драйвер JDBC обеспечивает поддержку API-интерфейса JDBC 4.0. В JDBC 4.0 типами данных символьных строк JDBC могут также быть **NCHAR**, **NVARCHAR**, и **LONGNVARCHAR**. Эти новые типы символьных строк поддерживают собственные символьные типы Java в формате Юникода и исключают необходимость выполнять какие-либо преобразования из ANSI в Юникод или из Юникода в ANSI.  
  
|Тип|Описание|  
|----------|-----------------|  
|Фиксированная длина|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **Char** и **nchar** типы данных сопоставляются непосредственно с JDBC **CHAR** и **NCHAR** типов. Они представляют собой типы фиксированной длины с заполнением, предоставляемым сервером, при условии, что для столбца установлено значение SET ANSI_PADDING ON. Заполнение всегда включено для **nchar**, а что касается **char**, то в случае, если на сервере заполнение для столбцов символьных типов не предусмотрено, то заполнение добавляет драйвер JDBC.|  
|Переменная длина|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **Varchar** и **nvarchar** типы непосредственно сопоставляются с JDBC **VARCHAR** и **NVARCHAR** соответственно.|  
|Long|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **Текст** и **ntext** типы сопоставляются с JDBC **LONGVARCHAR** и **LONGNVARCHAR** введите, соответственно. Эти типы являются устаревшими начиная с версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)], поэтому следует использовать типы больших значений **varchar(max)** или **nvarchar(max)** вместо нее.<br /><br /> С помощью обновления\<числового типа > и [updateObject (int, java.lang.Object)](../../connect/jdbc/reference/updateobject-method-int-java-lang-object.md) методы не удастся от **текст** и **ntext** серверным столбцам. Однако использование метода [setObject](../../connect/jdbc/reference/setobject-method-sqlserverpreparedstatement.md) с указанным символьным типом преобразования по отношению к серверным столбцам **text** и **ntext** поддерживается.|  
  
## <a name="binary-string-types"></a>Типы двоичных строк  
 Типами двоичных строк JDBC являются **ДВОИЧНЫХ**, **VARBINARY**, и **LONGVARBINARY**.  
  
|Тип|Описание|  
|----------|-----------------|  
|Фиксированная длина|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **Двоичных** введите прямо сопоставляется с JDBC **ДВОИЧНЫХ** типа. Это тип фиксированной длины с заполнением, предоставляемым сервером в случае, если для столбца установлено значение SET ANSI_PADDING ON. Если на сервере заполнение для столбцов символьных типов не предусмотрено, то заполнение добавляет драйвер JDBC.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **Timestamp** измеряется JDBC **ДВОИЧНЫХ** тип с постоянной длиной 8 байт.|  
|Переменная длина|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **Varbinary** тип сопоставляется JDBC **VARBINARY** типа.<br /><br /> **Определяемого пользователем типа** введите [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] сопоставляется с JDBC как **VARBINARY** типа.|  
|Long|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **Изображение** тип сопоставляется JDBC **LONGVARBINARY** типа. Этот тип является устаревшим начиная с версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)], и вместо него следует использовать тип больших значений **varbinary(max)**.|  
  
## <a name="exact-numeric-types"></a>Точные числовые типы  
 Точные числовые типы JDBC непосредственно сопоставляются с аналогичными типами SQL Server.  
  
|Тип|Описание|  
|----------|-----------------|  
|BIT|Тип **BIT** JDBC представляет единственный бит, который может иметь значение 0 или 1. Это значение соответствует значению [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **бит** типа.|  
|TINYINT|Тип JDBC **TINYINT** представляет единственный байт. Это значение соответствует значению [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **tinyint** типа.|  
|SMALLINT|Тип JDBC **SMALLINT** представляет 16-разрядное целочисленное значение со знаком. Это значение соответствует значению [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **smallint** типа.|  
|INTEGER|Тип JDBC **INTEGER** представляет 32-разрядное целочисленное значение со знаком. Это значение соответствует значению [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **int** типа.|  
|bigint|Тип JDBC **BIGINT** представляет 64-разрядное целочисленное значение со знаком. Это значение соответствует значению [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **bigint** типа.|  
|NUMERIC|Тип JDBC **NUMERIC** представляет значение десятичного числа постоянной точности, которое хранит значения идентичной точности. **ЧИСЛОВЫХ** тип сопоставляется [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **числовых** типа.|  
|DECIMAL|Тип JDBC **DECIMAL** представляет значение десятичного числа постоянной точности, которое хранит значения по крайней мере указанной точности. **ДЕСЯТИЧНОЕ** тип сопоставляется [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **десятичное** типа.<br /><br /> Тип JDBC **DECIMAL** сопоставляется с типами [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]**money** и **smallmoney**, которые являются десятичными типами с фиксированной точностью, хранящимися в 8 и 4 байтах соответственно.|  
  
## <a name="approximate-numeric-types"></a>Приблизительные числовые типы  
 Приблизительными числовыми типами JDBC являются **РЕАЛЬНЫХ**, **ДВОЙНЫЕ**, и **FLOAT**.  
  
|Тип|Описание|  
|----------|-----------------|  
|real|Тип JDBC **REAL** имеет семь цифр точности (одинарная точность) и непосредственно сопоставляется с типом [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **real**.|  
|DOUBLE|Тип JDBC **DOUBLE** имеет 15 цифр точности (двойная точность) и сопоставляется с типом [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]**float**. JDBC **FLOAT** тип является синонимом **ДВОЙНЫЕ**. Так как может существовать путаницы между **FLOAT** и **ДВОЙНЫЕ**, **ДВОЙНЫЕ** является предпочтительным.|  
  
## <a name="datetime-types"></a>Типы даты и времени  
 JDBC **TIMESTAMP** тип сопоставляется [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **datetime** и **smalldatetime** типов. Значения типа **datetime** хранятся в двух четырехбайтовых целых числах. Тип **smalldatetime** хранит ту же информацию (дату и время), но с меньшей точностью, в двух двухбайтовых целых числах типа small.  
  
> [!NOTE]  
>  Тип [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]**timestamp** — это тип двоичной строки фиксированной длины. Он сопоставляется с ни одном из типов JDBC времени: **даты**, **время**, или **TIMESTAMP**.  
  
## <a name="custom-type-mapping"></a>Сопоставление пользовательских типов  
 Сопоставление пользовательских типов JDBC, использующее интерфейсы SQLData для усовершенствованных типов JDBC (пользовательские, типы Struct и так далее). не реализовано в драйвере JDBC.  
  
## <a name="see-also"></a>См. также:  
 [Основные сведения о типах данных драйвера JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  
