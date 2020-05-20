---
title: sys. external_file_formats (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: a89efb2c-0a3a-4b64-9284-6e93263e29ac
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 75e3f884e09d41c2ae7aa5c7610b0c7ac24691a7
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82828520"
---
# <a name="sysexternal_file_formats-transact-sql"></a>sys. external_file_formats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Содержит по одной строке для каждого формата внешнего файла в текущей базе данных для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , [!INCLUDE[ssSDS](../../includes/sssds-md.md)] и [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] .  
  
 Содержит по одной строке для каждого формата внешнего файла на сервере для [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] .  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|file_format_id|**int**|Идентификатор объекта для формата внешнего файла.||  
|name|**sysname**|Имя формата файла. в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] это уникальное значение для базы данных. В [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] это уникальное значение для сервера.||  
|format_type|**tinyint**|Тип формата файла.|DELIMITEDTEXT, RCFILE, ORC, PARQUET|  
|field_terminator|**nvarchar (10)**|Для format_type = DELIMITEDTEXT это признак конца поля.||  
|string_delimiter|**nvarchar (10)**|Для format_type = DELIMITEDTEXT это разделитель строк.||  
|date_format|**nvarchar(50)**|Для format_type = DELIMITEDTEXT это определяемый пользователем формат даты и времени.||  
|use_type_default|**bit**|Для format_type = текст с РАЗДЕЛИТЕЛями указывает, как следует выполнять обработку отсутствующих значений, когда Polybase импортирует данные из текстовых файлов HDFS в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] .|0 — сохранить отсутствующие значения как строку "NULL".<br /><br /> 1. Сохранение отсутствующих значений в качестве значения по умолчанию для столбца.|  
|serde_method|**nvarchar(255)**|Для format_type = RCFILE это метод сериализации и десериализации.||  
|row_terminator|**nvarchar (10)**|Для format_type = DELIMITEDTEXT это символьная строка, которая завершает каждую строку во внешнем файле Hadoop.|Всегда равно "\n".|  
|encoding|**nvarchar (10)**|Для format_type = DELIMITEDTEXT это метод кодирования для внешнего файла Hadoop.|Всегда имеет кодировку "UTF8".|  
|data_compression|**nvarchar(255)**|Метод сжатия данных для внешних данных.|Для format_type = DELIMITEDTEXT:<br /><br /> -"org. Apache. Hadoop. IO. сжимать. Дефаулткодек"<br />-"org. Apache. Hadoop. IO. сжимать. Гзипкодек"<br /><br /> Для format_type = RCFILE:<br /><br /> -"org. Apache. Hadoop. IO. сжимать. Дефаулткодек"<br /><br /> Для format_type = ORC:<br /><br /> -"org. Apache. Hadoop. IO. сжимать. Дефаулткодек"<br />-"org. Apache. Hadoop. IO. сжимать. SnappyCodec"<br /><br /> Для format_type = PARQUET:<br /><br /> -"org. Apache. Hadoop. IO. сжимать. Гзипкодек"<br />-"org. Apache. Hadoop. IO. сжимать. SnappyCodec"|  
  
## <a name="permissions"></a>Разрешения  
 Видимость метаданных в представлениях каталогов ограничивается защищаемыми объектами, которыми пользователь владеет или на которые ему были предоставлены разрешения.  Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [sys. external_data_sources &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-data-sources-transact-sql.md)   
 [sys. external_tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-tables-transact-sql.md)   
 [CREATE EXTERNAL FILE FORMAT (Transact-SQL)](../../t-sql/statements/create-external-file-format-transact-sql.md)  
  
  
