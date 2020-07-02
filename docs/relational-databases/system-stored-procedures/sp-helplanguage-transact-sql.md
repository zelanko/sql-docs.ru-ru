---
title: sp_helplanguage (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helplanguage
- sp_helplanguage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helplanguage
- default languages
ms.assetid: 8c4651a5-7dbc-49c5-8691-dc72103c2dfa
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 2878d206d4bc90d801e1e8f42f4f3f2c04d2c121
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85733204"
---
# <a name="sp_helplanguage-transact-sql"></a>sp_helplanguage (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Выдает отчет о конкретном альтернативном языке или обо всех языках из [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helplanguage [ [ @language = ] 'language' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @language = ] 'language'`Имя альтернативного языка, для которого отображаются сведения. *Language* имеет тип **sysname**и значение по умолчанию NULL. Если указан *язык* , возвращаются сведения об указанном языке. Если язык не указан, возвращаются сведения обо всех языках в представлении совместимости **sys.sysязыков** .  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**langid**|**smallint**|Идентификационный номер языка.|  
|**DATEFORMAT**|**nchar(3)**|Формат даты.|  
|**DATEFIRST**|**tinyint**|Первый день недели: 1 для Понедельник, 2 для вторника и так далее до 7 для воскресенья.|  
|**обновления**|**int**|Версия последнего обновления [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для данного языка.|  
|**name**|**sysname**|Имя языка.|  
|**alias**|**sysname**|Альтернативное имя языка.|  
|**months**|**nvarchar (372)**|Названия месяцев.|  
|**shortmonths**|**nvarchar (132)**|Сокращенные названия месяцев.|  
|**недели**|**nvarchar (217)**|Названия дней.|  
|**lcid**|**int**|Код данной локали в Windows.|  
|**msglangid**|**smallint**|Идентификатор группы сообщений компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public**.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-information-about-a-single-language"></a>A. Возвращение сведений об отдельном языке  
 В следующем примере отображаются сведения об альтернативном языке `French`.  
  
```  
sp_helplanguage French;  
```  
  
### <a name="b-returning-information-about-all-languages"></a>Б. Возвращение сведений обо всех языках  
 В следующем примере отображаются сведения обо всех установленных альтернативных языках.  
  
```  
sp_helplanguage;  
```  
  
## <a name="see-also"></a>См. также  
 [Ядро СУБД хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [@@LANGUAGE (Transact-SQL)](../../t-sql/functions/language-transact-sql.md)   
 [ЗАДАТЬ язык &#40;Transact-SQL&#41;](../../t-sql/statements/set-language-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
