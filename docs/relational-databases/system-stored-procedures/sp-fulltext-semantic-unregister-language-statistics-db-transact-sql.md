---
title: sp_fulltext_semantic_unregister_language_statistics_db (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_fulltext_semantic_unregister_language_statistics_db_TSQL
- sp_fulltext_semantic_unregister_language_statistics_db
dev_langs:
- TSQL
helpviewer_keywords:
- sp_fulltext_semantic_unregister_language_statistics_db
ms.assetid: 1426ca4a-9a76-489e-98da-8f6d13ff9732
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 24103cf356afce28eced6e9e76f6af527579bf12
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="spfulltextsemanticunregisterlanguagestatisticsdb-transact-sql"></a>sp_fulltext_semantic_unregister_language_statistics_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отменяет регистрацию существующей базы данных со статистикой семантики языка на текущем экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и удаляет все связанные метаданные.  
  
 Эта инструкция не отсоединяет базу данных и не удаляет физический файл базы данных из файловой системы. После отмены регистрации базы данных можно отсоединить ее и удалить физический файл базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
EXEC sp_fulltext_semantic_unregister_language_statistics_db;  
GO  
```  
  
##  <a name="Arguments"></a> Аргументы  
 Для этой процедуры не требуются аргументы. Поскольку экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имеет только одну базу данных со статистикой семантики языка, указывать базу данных не обязательно.  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-set"></a>Результирующий набор  
 Нет.  
  
## <a name="general-remarks"></a>Общие замечания  
 При отмене регистрации базы данных статистики семантики языка удаляются и все связанные с ней метаданные.  
  
 **sp_fulltext_semantic_unregister_language_statistics_db** выполняет следующие действия:  
  
1.  Проверяет, что на текущем экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не выполняется заполнение семантической статистики.  
  
2.  Удаляет все метаданные, связанные с указанной базой данных статистики семантики языка.  
  
 Дополнительные сведения см. в разделе [Установка и настройка семантического поиска](../../relational-databases/search/install-and-configure-semantic-search.md).  
  
## <a name="metadata"></a>Метаданные  
 Сведения о базе данных статистики семантики языка, установленной на экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], запрос к представлению каталога [sys.fulltext_semantic_language_statistics_database &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql.md).  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Разрешения  
 Требуются разрешения CONTROL SERVER.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано, как отменить регистрацию базы данных семантической статистики языка путем вызова **sp_fulltext_semantic_unregister_language_statistics_db**.  
  
```sql  
EXEC sp_fulltext_semantic_unregister_language_statistics_db;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Установка и настройка семантического поиска](../../relational-databases/search/install-and-configure-semantic-search.md)  
  
  
