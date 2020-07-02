---
title: sp_fulltext_semantic_register_language_statistics_db (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_fulltext_semantic_register_language_statistics_db
- sp_fulltext_semantic_register_language_statistics_db_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_fulltext_semantic_register_language_statistics_db
ms.assetid: bef1b104-5a44-4327-9ae4-45eae3000f7e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: e34bc48b469ab0dd575e6f4a87ede90187101b82
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85727189"
---
# <a name="sp_fulltext_semantic_register_language_statistics_db-transact-sql"></a>sp_fulltext_semantic_register_language_statistics_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Регистрирует предварительно заполненную базу данных семантической статистики языка в текущем экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Семантическое извлечения возможно только после присоединения этой базы данных статистики языка и ее регистрации с помощью этой хранимой процедуры. Это действие выполняется только один раз для каждого из экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
EXEC sp_fulltext_semantic_register_language_statistics_db  
    [ @dbname = ] 'database_name';  
GO  
```  
  
##  <a name="arguments"></a><a name="Arguments"></a>Даваемых  
 [ @dbname =] "*database_name*"  
 Имя базы данных семантической статистики языка, регистрируемой в текущем экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. База данных должна быть уже присоединена. Аргумент *database_name* имеет тип **sysname**и не может иметь значение null.  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-set"></a>Результирующий набор  
 Нет.  
  
## <a name="general-remarks"></a>Общие замечания  
 База данных семантической статистики языка содержит статистическую информацию, связанную с языком и необходимую для семантической обработки текстового содержимого.  
  
 **sp_fulltext_semantic_register_language_statistics_db** выполняет следующие действия.  
  
1.  Проверяет, является ли экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версией, которая поддерживает семантическую обработку.  
  
2.  Проверяет, определена ли уже база данных семантической статистики языка в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
3.  Проверяет, является ли база данных допустимой базой данных семантической статистики языка.  
  
4.  Устанавливает разрешения для базы данных семантической статистики языка, ограничивая доступ пользователей к этой базе данных.  
  
5.  Вставляет метаданные, определяющие имя базы данных семантической статистики языка для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
6.  Вставляет метаданные, определяющие соответствие между установленной базой данных семантической статистики языка и внутренними таблицами языковой модели.  
  
7.  Проверяет, готова ли база данных к использованию.  
  
 Дополнительные сведения см. в разделе [Установка и настройка семантического поиска](../../relational-databases/search/install-and-configure-semantic-search.md).  
  
## <a name="metadata"></a>Метаданные  
 Для получения сведений о Семантическая статистика языка базе данных, установленной на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , запросите представление каталога [sys. Fulltext_semantic_language_statistics_database &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql.md).  
  
## <a name="security"></a>Безопасность  
  
### <a name="permissions"></a>Разрешения  
 Требуются разрешения CONTROL SERVER.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано, как зарегистрировать базу данных Семантическая статистика языка, вызвав **sp_fulltext_semantic_register_language_statistics_db**.  
  
```sql  
EXEC sp_fulltext_semantic_register_language_statistics_db @dbname = 'semanticsDb';  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Установка и настройка семантического поиска](../../relational-databases/search/install-and-configure-semantic-search.md)  
  
  
