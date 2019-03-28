---
title: sp_db_selective_xml_index (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_db_selective_xml_index_TSQL
- sp_db_selective_xml_index
dev_langs:
- TSQL
helpviewer_keywords:
- sp_db_selective_xml_index procedure
ms.assetid: 017301a2-4a23-4e68-82af-134f3d4892b3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e9b1752b5e567c2a26080422874e5bf6e31bc568
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58528606"
---
# <a name="spdbselectivexmlindex-transact-sql"></a>sp_db_selective_xml_index (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Включает и выключает функциональность селективного XML-индекса в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. При вызове без параметров хранимая процедура возвращает 1, если селективный XML-индекс включен в определенной базе данных.  
  
> [!NOTE]  
>  Чтобы отключить Селективный XML-индекс, с помощью этой хранимой процедуры, базы данных должен быть помещен в режим простого восстановления с помощью [параметры ALTER DATABASE SET &#40;Transact-SQL&#41; ](../../t-sql/statements/alter-database-transact-sql-set-options.md) команды.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
  
      sys.sp_db_selective_xml_index[[ @db_name = ] 'db_name'],   
[[ @action = ] 'action']  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @ db_name = ] 'db_name'` Имя базы данных, чтобы включить или отключить Селективный XML-индекс на. Если *db_name* имеет значение NULL, предполагается текущая база данных.  
  
`[ @action = ] 'action'` Определяет, следует ли включить или отключить индекс. Если значение, отличное «on», «true», «off» или «ЛОЖЬ» передается, возникает ошибка.  
  
```  
  
Allowed values: 'on', 'off', 'true', 'false'  
```  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **1** Если Селективный XML-индекс включен в определенной базе данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-enable-selective-xml-index-functionality"></a>A. Включение функциональности селективного XML-индекса  
 В следующем примере включается селективный XML-индекс в текущей базе данных.  
  
```  
EXECUTE sys.sp_db_selective_xml_index  
    @db_name = NULL  
  , @action = N'on';  
GO  
```  
  
 В следующем примере включается селективный XML-индекс в базе данных AdventureWorks2012.  
  
```  
EXECUTE sys.sp_db_selective_xml_index  
    @db_name = N'AdventureWorks2012'  
  , @action = N'true';  
GO  
```  
  
### <a name="b-disable-selective-xml-index-functionality"></a>Б. Отключение возможностей селективного XML-индекса  
 В следующем примере выключается селективный XML-индекс в текущей базе данных.  
  
```  
EXECUTE sys.sp_db_selective_xml_index  
    @db_name = NULL  
  , @action = N'off';  
GO  
```  
  
 В следующем примере выключается селективный XML-индекс в базе данных AdventureWorks2012.  
  
```  
EXECUTE sys.sp_db_selective_xml_index  
    @db_name = N'AdventureWorks2012'  
  , @action = N'false';  
GO  
```  
  
### <a name="c-detect-if-selective-xml-index-is-enabled"></a>В. Включен ли селективный XML-индекс  
 В следующем примере определяется наличие селективного XML-индекса. Возвращает 1, если селективный XML-индекс включен.  
  
```  
EXECUTE sys.sp_db_selective_xml_index;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Выборочный XML-индекс (SXI)](../../relational-databases/xml/selective-xml-indexes-sxi.md)  
  
  
