---
title: sys.external_file_formats (Transact-SQL) | Документация Майкрософт
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
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4a9d7d8e73dc61afc90485c0d5cd36b3bb009fda
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47658952"
---
# <a name="sysexternalfileformats-transact-sql"></a>sys.external_file_formats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Содержит по одной строке для каждого формата внешнего файла в текущей базе данных для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssSDS](../../includes/sssds-md.md)], и [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].  
  
 Содержит по одной строке для каждого формата внешнего файла на сервере для [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|file_format_id|**int**|Идентификатор объекта для формата внешнего файла.||  
|name|**sysname**|Имя формата файла. в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], является уникальным для базы данных. В [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], он уникален для сервера.||  
|format_type|**tinyint**|Тип формата файла.|DELIMITEDTEXT, RCFILE, ORC, PARQUET|  
|признак_конца_поля|**nvarchar(10)**|Format_type = DELIMITEDTEXT, это признак конца поля.||  
|string_delimiter|**nvarchar(10)**|Format_type = DELIMITEDTEXT, это разделитель строк.||  
|date_format|**nvarchar(50)**|Format_type = DELIMITEDTEXT, это определяемые пользователем формат даты и времени.||  
|use_type_default|**bit**|Format_type = текста с разделителями, указывает способ обработки отсутствующих значений, когда PolyBase Импорт данных из текстовых файлов HDFS в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].|0 — хранения отсутствующих значений в строку «NULL».<br /><br /> 1 — сохраните отсутствующие значения как значение столбца по умолчанию.|  
|serde_method|**nvarchar(255)**|Format_type = RCFILE, метод сериализации/десериализации.||  
|признак_конца_строки|**nvarchar(10)**|Format_type = DELIMITEDTEXT, это символьная строка, которая завершает каждой строки во внешнем файле Hadoop.|Всегда «\n».|  
|кодировка|**nvarchar(10)**|Format_type = DELIMITEDTEXT, этот способ кодирования для внешнего файла Hadoop.|Всегда 'UTF8'.|  
|data_compression|**nvarchar(255)**|Метод сжатия данных для внешних данных.|Format_type = DELIMITEDTEXT:<br /><br /> -«org.apache.hadoop.io.compress.DefaultCodec»<br />-«org.apache.hadoop.io.compress.GzipCodec»<br /><br /> Format_type = RCFILE:<br /><br /> -«org.apache.hadoop.io.compress.DefaultCodec»<br /><br /> Format_type = ORC:<br /><br /> -«org.apache.hadoop.io.compress.DefaultCodec»<br />-«org.apache.hadoop.io.compress.SnappyCodec»<br /><br /> Format_type = PARQUET:<br /><br /> -«org.apache.hadoop.io.compress.GzipCodec»<br />-«org.apache.hadoop.io.compress.SnappyCodec»|  
  
## <a name="permissions"></a>Разрешения  
 Видимость метаданных в представлениях каталогов ограничивается защищаемыми объектами, которыми пользователь владеет или на которые ему были предоставлены разрешения. Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [sys.external_data_sources &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-data-sources-transact-sql.md)   
 [sys.external_tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-tables-transact-sql.md)   
 [CREATE EXTERNAL FILE FORMAT (Transact-SQL)](../../t-sql/statements/create-external-file-format-transact-sql.md)  
  
  
