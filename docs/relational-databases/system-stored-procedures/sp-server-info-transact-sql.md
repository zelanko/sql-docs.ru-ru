---
title: sp_server_info (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_server_info
- sp_server_info_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_server_info
ms.assetid: 2dc2c262-3cfa-4a84-8127-3632ba583543
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a83d216b0830b035da72ad579a2448a12f41adba
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82810561"
---
# <a name="sp_server_info-transact-sql"></a>sp_server_info (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает список имен атрибутов и соответствующие значения для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], шлюза базы данных или базового источника данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_server_info [[@attribute_id = ] 'attribute_id']  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @attribute_id = ] 'attribute_id'`Целочисленный идентификатор атрибута. *attribute_id* имеет **тип int**и значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 Нет  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**ATTRIBUTE_ID**|**int**|Идентификатор атрибута.|  
|**ATTRIBUTE_NAME**|**varchar (** 60 **)**|Имя атрибута.|  
|**ATTRIBUTE_VALUE**|**varchar (** 255 **)**|Текущее значение атрибута.|  
  
 В следующей таблице перечислены атрибуты. [!INCLUDE[msCoName](../../includes/msconame-md.md)]Клиентские библиотеки ODBC в настоящий момент используют атрибуты **1**, **2**, **18**, **22**и **500** во время подключения.  
  
|ATTRIBUTE_ID|ATTRIBUTE_NAME, описание|ATTRIBUTE_VALUE|  
|-------------------|---------------------------------|----------------------|  
|**1**|DBMS_NAME|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|**2**|DBMS_VER|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] - *x. XX. xxxx*|  
|**10**|OWNER_TERM|владелец|  
|**11**|TABLE_TERM|table|  
|**12**|MAX_OWNER_NAME_LENGTH|128|  
|**13**|TABLE_LENGTH<br /><br /> Указывает максимальное количество символов в имени таблицы.|128|  
|**14**|MAX_QUAL_LENGTH<br /><br /> Указывает максимальную длину имени квалификатора таблицы (первой части трехкомпонентного имени таблицы).|128|  
|**15**|COLUMN_LENGTH<br /><br /> Указывает максимальное количество символов в имени столбца.|128|  
|**глубин**|IDENTIFIER_CASE<br /><br /> Указывает на учет регистра в именах, определяемых пользователем (имена таблиц, столбцов, хранимых процедур), в базе данных (в системных каталогах).|SENSITIVE|  
|**широкоэкранны**|TX_ISOLATION<br /><br /> Определяет начальный уровень изоляции транзакции, применяемый сервером по умолчанию, в соответствии с уровнями изоляции, определяемыми стандартом SQL-92.|2|  
|**стр**|COLLATION_SEQ<br /><br /> Определяет упорядочивание кодировок на данном сервере.|charset=iso_1 sort_order=dictionary_iso charset_num=1 sort_order_num=51|  
|**стр**|SAVEPOINT_SUPPORT<br /><br /> Определяет, поддерживает ли базовая СУБД именованные точки сохранения.|Да|  
|**20**|MULTI_RESULT_SETS<br /><br /> Определяет, поддерживает ли базовая база данных или сам шлюз множественные результирующие наборы (т.е. могут ли несколько инструкций отправляться через шлюз, возвращая клиенту несколько результирующих наборов).|Да|  
|**22**|ACCESSIBLE_TABLES<br /><br /> Указывает, будет ли в **sp_tables**шлюз возвращать только таблицы, представления и т. д., доступные текущему пользователю (то есть пользователю, у которого есть по крайней мере разрешения SELECT для таблицы).|Да|  
|**100**|USERID_LENGTH<br /><br /> Указывает максимальное количество символов в имени пользователя.|128|  
|**101**|QUALIFIER_TERM<br /><br /> Указывает термин поставщика СУБД для квалификатора таблицы (первой части трехкомпонентного имени таблицы).|База данных|  
|**102**|NAMED_TRANSACTIONS<br /><br /> Определяет, поддерживает ли базовая СУБД именованные транзакции.|Да|  
|**103**|SPROC_AS_LANGUAGE<br /><br /> Определяет, могут ли хранимые процедуры выполняться как события языка.|Да|  
|**104**|ACCESSIBLE_SPROC<br /><br /> Указывает, входит ли в **sp_stored_procedures**, что шлюз возвращает только хранимые процедуры, исполняемые текущим пользователем.|Да|  
|**105**|MAX_INDEX_COLS<br /><br /> Определяет максимальное количество столбцов в индексе для СУБД.|16|  
|**106**|RENAME_TABLE<br /><br /> Определяет, возможно ли переименование таблиц.|Да|  
|**107**|RENAME_COLUMN<br /><br /> Определяет, возможно ли переименование столбцов.|Да|  
|**108**|DROP_COLUMN<br /><br /> Определяет, возможно ли удаление столбцов.|Да|  
|**109**|INCREASE_COLUMN_LENGTH<br /><br /> Определяет, возможно ли увеличение размера столбца.|Да|  
|**110**|DDL_IN_TRANSACTION<br /><br /> Определяет, могут ли транзакции содержать DDL-инструкции.|Да|  
|**111**|DESCENDING_INDEXES<br /><br /> Определяет, поддерживаются ли индексы с сортировкой по убыванию.|Да|  
|**112**|SP_RENAME<br /><br /> Определяет, возможно ли переименование хранимых процедур.|Да|  
|**113**|REMOTE_SPROC<br /><br /> Определяет, возможно ли выполнение хранимых процедур через функции работы с удаленными хранимыми процедурами из DB-Library.|Да|  
|**500**|SYS_SPROC_VERSION<br /><br /> Определяет версию хранимых процедур каталога, реализованных на данный момент.|Номер текущей версии|  
  
## <a name="remarks"></a>Примечания  
 **sp_server_info** возвращает подмножество сведений, предоставляемых **SQLGetInfo** в ODBC.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение SELECT для схемы.  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры каталога &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
