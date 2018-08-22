---
title: Параметры проекта (сопоставление типов) (SybaseToSQL) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 2698fb3a-f9e6-4e04-94e0-dad289d7ed0a
caps.latest.revision: 6
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: b0c4e2743c4169bd7626ca66c9d9dba609facdaa
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2018
ms.locfileid: "40395342"
---
# <a name="project-settings-type-mapping-sybasetosql"></a>Параметры проекта (сопоставление типов) (SybaseToSQL)
На странице сопоставления типов **параметры проекта** диалоговое окно содержит настройки, установленные как SSMA преобразует типы данных Sybase Adaptive Server Enterprise (ASE) в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типов данных.  
  
Страница сопоставления типов доступна в **параметры проекта** и **параметры проекта по умолчанию** диалоговым окнам.  
  
-   Чтобы указать параметры сопоставления типа для всех будущих проектов SSMA на **средства** меню, выберите **параметры проекта по умолчанию**, выберите тип проекта миграции, для которого требуются параметры для просмотра или изменено с **целевой версии миграции** раскрывающийся список и выберите **сопоставления типов** в нижней части левой панели.  
  
-   Для задания параметров для текущего проекта, на **средства** меню, выберите **параметры проекта**, а затем выберите **сопоставления типов** в нижней части левой панели.  
  
## <a name="options"></a>Параметры  
**Исходный тип**  
Сопоставленный тип данных среды ASE.  
  
**Тип целевого объекта**  
Целевой объект [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных для указанного типа данных ASE.  
  
См. в таблице в следующем разделе для применяемого по умолчанию SSMA для Sybase сопоставление типов.  
  
**Добавить**  
Щелкните, чтобы добавить в список сопоставления типа данных.  
  
**Изменить**  
Щелкните, чтобы изменить тип данных выбранного в списке сопоставление.  
  
**Удалить**  
Щелкните, чтобы удалить сопоставление типов данных, выбранного в списке сопоставление.  
  
**Сброс до значений по умолчанию**  
Щелкните, чтобы сбросить список сопоставления типа по умолчанию SSMA.  
  
## <a name="default-type-mapping"></a>Сопоставление типов по умолчанию  
Следующая таблица содержит сопоставление типов по умолчанию ASE и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типов данных.  
  
|Тип данных ASE|Тип данных SQL Server|  
|-----------------|------------------------|  
|**bigint**|**bigint**|  
|**binary**|**binary**|  
|**двоичные [\*.. 8000]**|**двоичные [\*]**|  
|**двоичные [8001..\*]**|**varbinary(max)**|  
|**bit**|**bit**|  
|**char**|**char**|  
|**char varying**|**varchar**|  
|**char varying [\*.. 8000]**|**varchar [\*]**|  
|**char varying [8001..\*]**|**varchar(max)**|  
|**char [\*.. 8000]**|**char [\*]**|  
|**char [8001..\*;]**|**varchar(max)**|  
|**character**|**char**|  
|**Изменение символа**|**varchar**|  
|**Изменение символа [\*.. 8000]**|**varchar [\*]**|  
|**Изменение символа [8001..\*]**|**varchar(max)**|  
|**символ [\*.. 8000]**|**char [\*]**|  
|**символ [8001..\*]**|**varchar(max)**|  
|**date**|**date**|  
|**datetime**|**datetime2[3]**|  
|**dec**|**decimal**|  
|**DEC [\*.. \*]**|**Decimal [\*]**|  
|**DEC [\*.. \*][\*.. \*]**|**decimal[\*][\*]**|  
|**decimal**|**decimal**|  
|**Decimal [\*.. \*]**|**Decimal [\*]**|  
|**Decimal [\*.. \*][\*.. \*]**|**decimal[\*][\*]**|  
|**двойной точности**|**число с плавающей запятой [53]**|  
|**float**|**число с плавающей запятой [53]**|  
|**число с плавающей запятой [\*.. 15]**|**число с плавающей запятой [24]**|  
|**число с плавающей запятой [16..\*]**|**число с плавающей запятой [53]**|  
|**image**|**image**|  
|**int**|**int**|  
|**integer**|**int**|  
|**longsysname**|**nvarchar [255]**|  
|**money**|**money**|  
|**National char**|**nchar**|  
|**National char [\*.. 4000]**|**nchar [\*]**|  
|**National char varying**|**nvarchar**|  
|**National char varying [\*.. 4000]**|**nvarchar [\*]**|  
|**National char varying [4001..\*]**|**nvarchar(max)**|  
|**National char [4001..\*]**|**nvarchar(max)**|  
|**символов национального алфавита**|**nchar**|  
|**символов национального алфавита [\*.. 4000]**|**nchar [\*]**|  
|**символов национального алфавита [4001..\*]**|**nvarchar(max)**|  
|**изменение символов национального алфавита**|**nvarchar**|  
|**различных национальных символов [\*.. 4000]**|**nvarchar [\*]**|  
|**различных национальных символов [4001..\*]**|**nvarchar(max)**|  
|**Национальный varchar**|**nvarchar**|  
|**Национальный varchar [\*.. 4000]**|**nvarchar [\*]**|  
|**Национальный varchar [4001..\*]**|**nvarchar(max)**|  
|**nchar**|**nchar**|  
|**изменения nchar**|**nvarchar**|  
|**nchar varying [\*.. 4000]**|**nvarchar [\*]**|  
|**nchar varying [4001..\*]**|**nvarchar(max)**|  
|**nchar [\*.. 4000]**|**nchar [\*]**|  
|**nchar [4001..\*]**|**nvarchar(max)**|  
|**numeric**|**numeric**|  
|**числовые [\*.. \*]**|**числовые [\*]**|  
|**числовые [\*.. \*][\*.. \*]**|**numeric[\*][\*]**|  
|**nvarchar**|**nvarchar**|  
|**nvarchar [\*.. 4000]**|**nvarchar [\*]**|  
|**nvarchar [4001..\*]**|**nvarchar(max)**|  
|**real**|**число с плавающей запятой [24]**|  
|**smalldatetime**|**smalldatetime**|  
|**smallint**|**smallint**|  
|**smallmoney**|**smallmoney**|  
|**sysname**|**nvarchar [128]**|  
|**sysname [\*.. \*]**|**nvarchar [255]**|  
|**text**|**text**|  
|**time**|**время [3]**|  
|**timestamp**|**rowversion**|  
|**tinyint**|**tinyint**|  
|**unichar**|**nchar**|  
|**изменения unichar**|**nvarchar**|  
|**Изменение unichar [\*.. 4000]**|**nvarchar [\*]**|  
|**Изменение unichar [4001..\*]**|**nvarchar(max)**|  
|**unichar [\*.. 4000]**|**nchar [\*]**|  
|**unichar [4001..\*]**|**nvarchar(max)**|  
|**unitext**|**nvarchar(max)**|  
|**univarchar**|**nvarchar**|  
|**univarchar [\*.. 4000]**|**nvarchar [\*]**|  
|**univarchar [4001..\*]**|**nvarchar(max)**|  
|**unsigned bigint**|**numeric[20][0]**|  
|**int без знака**|**bigint**|  
|**без знака smallint**|**int**|  
|**без знака tinyint**|**tinyint**|  
|**varbinary**|**varbinary**|  
|**varbinary [\*.. 8000]**|**varbinary [\*]**|  
|**varbinary [8001..\*]**|**varbinary(max)**|  
|**varchar**|**varchar**|  
|**varchar [\*.. 8000]**|**varchar [\*]**|  
|**varchar [8001..\*]**|**varchar(max)**|  
  
