---
title: Типы данных SQL Server и служб SSIS, поддерживаемые для доменов DQS | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 4931143a-b84d-478b-9b45-174128d36ed3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ad79983f570beb4c789379b2b48682b358c34e1b
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84937375"
---
# <a name="supported-sql-server-and-ssis-data-types-for-dqs-domains"></a>Типы данных SQL Server и службы SSIS, поддерживаемые для доменов DQS
  В SQL Server и службах SQL Server Integration Services (SSIS) имеется много типов данных, но только четыре из них предназначены для доменов DQS: Date, Decimal, Integer и String. В DQS поддерживаются не все типы данных SQL Server и служб SSIS. Сопоставление исходных данных с доменом DQS для проведения действия по обеспечению качества данных возможно только в том случае, если исходный тип данных поддерживается службами DQS и совпадает с типом данных домена DQS. В данном разделе приведены сведения о типах данных SQL Server и службах SSIS, которые поддерживаются и доступны для сопоставления с каждым из четырех типов данных для доменов DQS.  
  
> [!NOTE]  
>  В XLSX-файлах и XLS-файлах тип данных исходного столбца определяется по преобладающему типу данных в первых восьми строках. Если данные в ячейке не соответствуют данному типу, ячейке присваивается значение NULL. Аналогичным образом, в CSV-файлах тип данных исходного столбца определяется по преобладающему типу данных в первых восьми строках.  
  
##  <a name="supported-sql-server-data-types"></a><a name="SQLServer"></a>Поддерживаемые типы данных SQL Server  
 В следующей таблице приведены сведения о типах данных SQL Server, поддерживаемых для каждого из типов данных домена DQS.  
  
|Тип данных доменов DQS|Поддерживаемый тип данных SQL Server|  
|--------------------------|------------------------------------|  
|Дата|дата|  
|Decimal|Decimal<br /><br /> FLOAT<br /><br /> money<br /><br /> NUMERIC<br /><br /> real<br /><br /> smallmoney|  
|Целое число|BIGINT<br /><br /> INT<br /><br /> smallint<br /><br /> tinyint|  
|Строка|char<br /><br /> nchar<br /><br /> nvarchar<br /><br /> varchar|  
  
 Остальные типы данных SQL Server в DQS не поддерживаются. Дополнительные сведения обо всех типах данных SQL Server см. в статье [Типы данных &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).  
  
##  <a name="supported-ssis-data-types"></a><a name="SSIS"></a>Поддерживаемые типы данных служб SSIS  
 В следующей таблице приведены сведения о типах данных служб SSIS, поддерживаемых для каждого из типов данных домена DQS.  
  
|Тип данных доменов DQS|Поддерживаемые типы данных служб SSIS|  
|--------------------------|------------------------------|  
|Дата|DT_DATE|  
|Decimal|DT_DECIMAL<br /><br /> DT_NUMERIC<br /><br /> DT_R4<br /><br /> DT_R8|  
|Целое число|DT_I1<br /><br /> DT_I2<br /><br /> DT_I4<br /><br /> DT_I8<br /><br /> DT_U1<br /><br /> DT_U2<br /><br /> DT_U4<br /><br /> DT_U8|  
|Строка|DT_STR<br /><br /> DT_WSTR|  
  
 Остальные типы данных служб SSIS в DQS не поддерживаются. Дополнительные сведения обо всех типах данных служб SSIS см. в разделе [Integration Services Data Types](../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="see-also"></a>См. также:  
 [Управление доменом](../../2014/data-quality-services/managing-a-domain.md)  
  
  
