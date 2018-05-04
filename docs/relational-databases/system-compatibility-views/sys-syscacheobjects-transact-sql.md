---
title: sys.syscacheobjects (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-compatibility-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.syscacheobjects_TSQL
- sys.syscacheobjects
- syscacheobjects
- syscacheobjects_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- syscacheobjects system table
- sys.syscacheobjects compatibility view
ms.assetid: 9b14f37c-b7f5-4f71-b070-cce89a83f69e
caps.latest.revision: 37
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: b0585b2eb8d0b8547e6b22e5817e3ca985cbea71
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="syssyscacheobjects-transact-sql"></a>sys.syscacheobjects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит сведения об использовании кэша.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**BucketID**|**int**|Идентификатор сегмента. Может принимать значения от 0 до величины, равной размеру каталога минус 1. Размер каталога равен размеру хэш-таблицы.|  
|**cacheobjtype**|**nvarchar(17)**|Тип объекта, содержащегося в кэше:<br /><br /> Скомпилированный план<br /><br /> Исполняемый план.<br /><br /> Дерево синтаксического анализа<br /><br /> Курсор<br /><br /> Расширенная хранимая процедура|  
|**objtype**|**nvarchar(8)**|Тип объекта:<br /><br /> Хранимая процедура<br /><br /> Подготовленная инструкция<br /><br /> Нерегламентированный запрос ([!INCLUDE[tsql](../../includes/tsql-md.md)] отправлены в виде событий языка из **sqlcmd** или **osql** программ, а не удаленные вызовы процедур)<br /><br /> ReplProc (процедура репликации) <br /><br /> Триггер<br /><br /> Просмотр<br /><br /> По умолчанию<br /><br /> Пользовательская таблица<br /><br /> Системная таблица<br /><br /> Проверить<br /><br /> Правило|  
|**objID**|**int**|Одно из основных ключевых слов, используемое для поиска объекта в кэш-памяти. Это идентификатор объекта, хранимый в **sysobjects** для объектов базы данных (процедуры, представления, триггеры и т. д.). Для объектов кэша, таких как нерегламентированные или подготовленные SQL **objid** находится внутри созданного значения.|  
|**dbid**|**smallint**|Идентификатор базы данных, в которой объект кэша был скомпилирован.|  
|**dbidexec**|**smallint**|Идентификатор базы данных, из которой выполняется запрос.<br /><br /> Для большинства объектов **dbidexec** имеет то же значение, что **dbid**.<br /><br /> Для системных представлений **dbidexec** идентификатор базы данных, из которой выполняется запрос.<br /><br /> Для нерегламентированных запросов **dbidexec** — 0. Это означает **dbidexec** имеет то же значение, что **dbid**.|  
|**UID**|**smallint**|Указывает автора подготовленных планов и планов нерегламентированных запросов.<br /><br /> -2 = Отправленный пакет не зависит от разрешения скрытых имен и может использоваться различными пользователями. Этот метод является предпочтительным. Любое другое значение обозначает идентификатор пользователя, отправившего запрос к базе данных.<br /><br /> Вызывает переполнение или возвращает значение NULL, если количество пользователей и ролей превышает 32 767.|  
|**счетчики refcount**|**int**|Количество объектов кэша, ссылающихся на данный объект. Отсчет начинается с 1.|  
|**usecounts**|**int**|Количество обращений к данному объекту с момента его внедрения.|  
|**pagesused**|**int**|Число страниц, занимаемых объектом кэша.|  
|**setopts**|**int**|Настройки параметров SET, влияющие на скомпонованный план. Данные настройки являются частью ключа кэша. При изменении пользователями параметров SET значения данного столбца также изменяются. К указанным параметрам относятся:<br /><br /> **ANSI_PADDING**<br /><br /> **FORCEPLAN**<br /><br /> **CONCAT_NULL_YIELDS_NULL**<br /><br /> **ANSI_WARNINGS**<br /><br /> **ANSI_NULLS**<br /><br /> **QUOTED_IDENTIFIER**<br /><br /> **ANSI_NULL_DFLT_ON**<br /><br /> **ANSI_NULL_DFLT_OFF**|  
|**LangID**|**smallint**|Идентификатор языка. Идентификатор языка соединения, в результате которого был создан объект кэша.|  
|**DATEFORMAT**|**smallint**|Формат даты соединения, во время которого был создан объект кэша.|  
|**status**|**int**|Указывает на принадлежность объекта кэша к плану исполнения курсора. В настоящее время используется только младший значащий бит.|  
|**lasttime**|**bigint**|Только для обратной совместимости. Всегда возвращает значение 0.|  
|**maxexectime**|**bigint**|Только для обратной совместимости. Всегда возвращает значение 0.|  
|**avgexectime**|**bigint**|Только для обратной совместимости. Всегда возвращает значение 0.|  
|**lastreads**|**bigint**|Только для обратной совместимости. Всегда возвращает значение 0.|  
|**lastwrites**|**bigint**|Только для обратной совместимости. Всегда возвращает значение 0.|  
|**SqlBytes**|**int**|Объем отправленного определения процедуры или пакета, в байтах.|  
|**sql**|**nvarchar(3900)**|Определение модуля или первые 3900 символов отправленного пакета.|  
  
## <a name="see-also"></a>См. также  
 [Представления совместимости (Transact-SQL)](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  

