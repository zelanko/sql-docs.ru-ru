---
title: "Параметры (сопоставление типов) проекта (MySQLToSQL) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-mysql
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 136fdf6d-657f-447b-af41-49bbc6e0e93e
caps.latest.revision: 
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7ca62e82b85d401f99a6e59f6f440d9a6519e58d
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="project-settings-type-mapping-mysqltosql"></a>Параметры (сопоставление типов) проекта (MySQLToSQL)
Параметры сопоставления типов проекта позволяют задать сопоставления типов по умолчанию для проекта SSMA.  

Сопоставление типов доступен в диалоговых окнах параметры проекта и параметры проекта по умолчанию:  
  
-   Используйте диалоговое окно параметров проекта, чтобы задать параметры конфигурации для текущего проекта. Для доступа к параметрам типа сопоставления, в меню "Сервис" выберите параметры проекта и нажмите кнопку сопоставление типов в левой области.  
  
-   Используйте диалоговое окно Параметры проекта по умолчанию, чтобы задать параметры конфигурации для всех проектов. Для доступа к сопоставление типов параметров, в меню "Сервис" выберите параметры по умолчанию проекта, выберите миграции типа проекта, для которого требуются параметры быть просмотреть / изменить из **миграции целевой версии** раскрывающийся список и выберите сопоставление типов в левой области.  
  
## <a name="options"></a>Параметры  
  
##### <a name="source-type"></a>Исходный тип  
Он имеет тип данных MySQL, имеющая сопоставить тип данных целевой базы данных.  
  
##### <a name="target-type"></a>Тип целевого объекта  
Тип данных целевой базы данных для указанного типа данных MySQL.  
  
##### <a name="add"></a>Добавить  
Щелкните, чтобы добавить в список сопоставления типа данных.  
  
##### <a name="edit"></a>Изменить  
Щелкните для изменения выбранного типа данных в списке сопоставления.  
  
##### <a name="remove"></a>Удалить  
Щелкните, чтобы удалить сопоставление типов данных, выбранного из списка сопоставления.  
  
##### <a name="reset-to-default"></a>По умолчанию  
Щелкните, чтобы сбросить список сопоставления типа по умолчанию SSMA.  
  
## <a name="type-mappings"></a>Сопоставления типов  
В следующей таблице показаны сопоставления по умолчанию между исходной и целевой типы данных  
  
|||  
|-|-|  
|**Тип данных MySQL**|**Тип данных SQL Server**|  
|bigint|bigint|  
|bigint [*.. 255]|bigint|  
|BINARY|двоичные [1]|  
|двоичные [от 0 до 1]|двоичные [1]|  
|двоичные [2..255]|двоичные [*]|  
|bit|двоичные [1]|  
|bit[0..8]|двоичные [1]|  
|bit[17..24]|двоичный файл [3]|  
|бит [25..32]|двоичный файл [4]|  
|bit[33..40]|двоичные [5]|  
|bit[41..48]|двоичные [6]|  
|бит [49..56]|двоичные [7]|  
|bit[57..64]|двоичные [8]|  
|бит [9..16]|двоичный файл [2]|  
|большой двоичный объект|varbinary(max)|  
|blob[0..1]|varbinary [1]|  
|blob[2..8000]|varbinary [*]|  
|blob[8001..*]|varbinary(max)|  
|bool|bit|  
|boolean|bit|  
|char;|nchar [1]|  
|char байтов|двоичные [1]|  
|char байтов [от 0 до 1]|двоичные [1]|  
|байтов char [2..255]|двоичные [*]|  
|char [от 0 до 1]|nchar [1]|  
|char [2..255]|nchar [*]|  
|character|nchar [1]|  
|символ varying [от 0 до 1]|nvarchar [1]|  
|символ varying [2..255]|nvarchar|  
|символ [от 0 до 1]|nchar [1]|  
|символ [2..255]|nchar [*]|  
|date|date|  
|datetime|datetime2[0]|  
|dec|Decimal|  
|dec[*..65]|decimal[*][0]|  
|dec[*..65][\*..30]|decimal[*][\*]|  
|Decimal|Decimal|  
|decimal[*..65]|decimal[*][0]|  
|decimal[*..65][\*..30]|decimal[*][\*]|  
|double|float[53]|  
|число двойной точности|float[53]|  
|число двойной точности [*.. 255][\*.. 30]|numeric[*][\*]|  
|double[*..255][\*..30]|numeric[*][\*]|  
|исправлена|numeric|  
|fixed[*..65][\*..30]|numeric[*][\*]|  
|float|float[24]|  
|число с плавающей запятой [*.. 255][\*.. 30]|numeric[*][\*]|  
|число с плавающей запятой [*.. 53]|float[53]|  
|int|int|  
|int [*.. 255]|int|  
|integer|int|  
|integer[*..255]|int|  
|longblob|varbinary(max)|  
|LONGTEXT|nvarchar(max)|  
|mediumblob|varbinary(max)|  
|mediumint|int|  
|mediumint [*.. 255]|int|  
|mediumtext|nvarchar(max)|  
|Национальный char|nchar [1]|  
|Национальный char [от 0 до 1]|nchar [1]|  
|Национальный char [2..255]|nchar [*]|  
|символов национального алфавита|nchar [1]|  
|изменение символов национального алфавита|nvarchar [1]|  
|символов национального алфавита varying [от 0 до 1]|nvarchar [1]|  
|символов национального алфавита varying [2..4000]|nvarchar [*]|  
|изменение символов национального алфавита [4001.. *]|nvarchar(max)|  
|символов национального алфавита [от 0 до 1]|nchar [1]|  
|национальных символов [2..255]|nchar [*]|  
|Национальный varchar|nvarchar [1]|  
|Национальный varchar [от 0 до 1]|nvarchar [1]|  
|Национальный varchar [2..4000]|nvarchar [*]|  
|Национальный varchar [4001.. *]|nvarchar(max)|  
|NCHAR|nchar [1]|  
|varchar, nchar|nvarchar [1]|  
|nchar, varchar [от 0 до 1]|nvarchar [1]|  
|nchar, varchar [2..4000]|nvarchar [*]|  
|varchar, nchar [4001.. *]|nvarchar(max)|  
|nchar [от 0 до 1]|nchar [1]|  
|nchar [2..255]|nchar [*]|  
|numeric|numeric|  
|numeric[*..65]|numeric[*][0]|  
|numeric[*..65][\*..30]|numeric[*][\*]|  
|nvarchar|nvarchar [1]|  
|nvarchar [от 0 до 1]|nvarchar [1]|  
|nvarchar [2..4000]|nvarchar [*]|  
|nvarchar [4001.. *]|nvarchar(max)|  
|real|float[53]|  
|real[*..255][\*..30]|numeric[*][\*]|  
|Последовательный|bigint|  
|smallint|smallint|  
|smallint [*.. 255]|smallint|  
|text|nvarchar(max)|  
|text[0..1]|nvarchar [1]|  
|text[2..4000]|nvarchar [*]|  
|text[4001..*]|nvarchar(max)|  
|time|time|  
|TIMESTAMP|datetime|  
|tinyblob|varbinary [255]|  
|tinyint|smallint|  
|tinyint [*.. 255]|smallint|  
|tinytext|nvarchar [255]|  
|без знака bigint|bigint|  
|без знака bigint [*.. 255]|bigint|  
|десятичное число без знака|Decimal|  
|десятичное число без знака [*.. 65]|decimal[*][0]|  
|десятичное число без знака [*.. 65][\*.. 30]|decimal[*][\*]|  
|Десятичный значение без знака|Decimal|  
|Десятичный значение без знака [*.. 65]|decimal[*][0]|  
|Десятичный значение без знака [*.. 65][\*.. 30]|decimal[*][\*]|  
|без знака типа double|float[53]|  
|без знака двойной точности|float[53]|  
|без знака двойной точности [*.. 255][\*.. 30]|numeric[*][\*]|  
|без знака double [*.. 255][\*.. 30]|numeric[*][\*]|  
|без знака основных|numeric|  
|без знака основных [*.. 65][\*.. 30]|numeric[*][\*]|  
|число с плавающей запятой без знака|float[24]|  
|число с плавающей запятой без знака [*.. 255][\*.. 30]|numeric[*][\*]|  
|число с плавающей запятой без знака [*.. 53]|float[53]|  
|Целочисленное число без знака|bigint|  
|Тип unsigned int [*.. 255]|bigint|  
|целое число без знака|bigint|  
|целое число без знака [*.. 255]|bigint|  
|mediumint число без знака|int|  
|без знака mediumint [*.. 255]|int|  
|Числовые без знака|numeric|  
|без знака числовой [*.. 65]|numeric[*][0]|  
|без знака числовой [*.. 65][\*.. 30]|numeric[*][\*]|  
|без реальных знака|float[53]|  
|без знака real [*.. 255[[\*.. 30]|numeric[*][\*]|  
|smallint без знака|int|  
|без знака smallint [*.. 255]|int|  
|тип tinyint и без знака|tinyint|  
|без знака tinyint [*.. 255]|tinyint|  
|varbinary [от 0 до 1]|varbinary [1]|  
|varbinary [2..8000]|varbinary [*]|  
|varbinary [8001.. *]|varbinary(max)|  
|varchar [от 0 до 1]|nvarchar [1]|  
|varchar [2..4000]|nvarchar [*]|  
|varchar[4001..*]|nvarchar(max)|  
|year|smallint|  
|год [2..2]|smallint|  
|год [4..4]|smallint|  
  
##### <a name="add"></a>Добавить  
Щелкните, чтобы добавить в список сопоставления типа данных.  
  
##### <a name="edit"></a>Изменить  
Щелкните, чтобы изменить тип данных в списке сопоставления.  
  
##### <a name="remove"></a>Удалить  
Щелкните, чтобы удалить сопоставление типов данных, выбранного из списка сопоставления.  
  
##### <a name="reset-to-default"></a>По умолчанию  
Щелкните, чтобы сбросить все сопоставления типов данных по умолчанию SSMA.  
  
