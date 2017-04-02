---
title: "Типы данных SQL Server и службы SSIS, поддерживаемые для доменов DQS | Microsoft Docs"
ms.custom: ""
ms.date: "11/08/2011"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4931143a-b84d-478b-9b45-174128d36ed3
caps.latest.revision: 7
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 7
---
# Типы данных SQL Server и службы SSIS, поддерживаемые для доменов DQS
  В SQL Server и службах SQL Server Integration Services (SSIS) имеется много типов данных, но только четыре из них предназначены для доменов DQS: Date, Decimal, Integer и String. В DQS поддерживаются не все типы данных SQL Server и служб SSIS. Сопоставление исходных данных с доменом DQS для проведения действия по обеспечению качества данных возможно только в том случае, если исходный тип данных поддерживается службами DQS и совпадает с типом данных домена DQS. В данном разделе приведены сведения о типах данных SQL Server и службах SSIS, которые поддерживаются и доступны для сопоставления с каждым из четырех типов данных для доменов DQS.  
  
> [!NOTE]  
>  В XLSX-файлах и XLS-файлах тип данных исходного столбца определяется по преобладающему типу данных в первых восьми строках. Если данные в ячейке не соответствуют данному типу, ячейке присваивается значение NULL. Аналогичным образом, в CSV-файлах тип данных исходного столбца определяется по преобладающему типу данных в первых восьми строках.  
  
##  <a name="SQLServer"></a> Поддерживаемые типы данных SQL Server  
 В следующей таблице приведены сведения о типах данных SQL Server, поддерживаемых для каждого из типов данных домена DQS.  
  
|Тип данных доменов DQS|Поддерживаемый тип данных SQL Server|  
|--------------------------|------------------------------------|  
|Дата|Дата|  
|Decimal|Decimal<br /><br /> float<br /><br /> money<br /><br /> numeric<br /><br /> real<br /><br /> smallmoney|  
|Целочисленный|bigint<br /><br /> int<br /><br /> smallint<br /><br /> tinyint|  
|Строковые значения|char;<br /><br /> nchar<br /><br /> nvarchar<br /><br /> varchar|  
  
 Остальные типы данных SQL Server в DQS не поддерживаются. Сведения обо всех типах данных SQL Server см. в разделе [типов данных и #40; Transact-SQL & #41;](../t-sql/data-types/data-types-transact-sql.md).  
  
##  <a name="SSIS"></a> Поддерживаемые типы данных служб SSIS  
 В следующей таблице приведены сведения о типах данных служб SSIS, поддерживаемых для каждого из типов данных домена DQS.  
  
|Тип данных доменов DQS|Поддерживаемые типы данных служб SSIS|  
|--------------------------|------------------------------|  
|Дата|DT_DATE|  
|Decimal|DT_DECIMAL<br /><br /> DT_NUMERIC<br /><br /> DT_R4<br /><br /> DT_R8|  
|Целочисленный|DT_I1<br /><br /> DT_I2<br /><br /> DT_I4<br /><br /> DT_I8<br /><br /> DT_U1<br /><br /> DT_U2<br /><br /> DT_U4<br /><br /> DT_U8|  
|Строковые значения|DT_STR<br /><br /> DT_WSTR|  
  
 Остальные типы данных служб SSIS в DQS не поддерживаются. Дополнительные сведения обо всех типах данных служб SSIS см. в разделе [Integration Services Data Types](../integration-services/data-flow/integration-services-data-types.md).  
  
## См. также:  
 [Управление доменом](../data-quality-services/managing-a-domain.md)  
  
  