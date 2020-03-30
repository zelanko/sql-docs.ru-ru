---
title: VERSION (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 95a79b33-98f2-4929-a1a5-93b522a9e152
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: ed3eab701a8edbbf118e228bd90080a61a214b32
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "67927430"
---
# <a name="version---transact-sql-metadata-functions"></a>Version — функции метаданных Transact SQL
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

 Возвращает версию [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] или [!INCLUDE[ssPDW_md](../../includes/sspdw-md.md)], выполняющуюся на устройстве.  
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Azure SQL Data Warehouse and Parallel Data Warehouse  
VERSION ( )  
```  
  
## <a name="arguments"></a>Аргументы  
  
## <a name="general-remarks"></a>Общие замечания  
Чтобы эта функция вернула результат, необходимо указать имя таблицы в предложении [FROM](../../t-sql/queries/from-transact-sql.md). Для каждой строки в результирующем наборе для запроса будет возвращаться строка результата. Чтобы ограничить число возвращаемых строк, используйте функцию [TOP (Transact-SQL)](../../t-sql/queries/top-transact-sql.md).  
  
## <a name="examples"></a>Примеры  
В следующем примере возвращается номер версии.  
  
```  
SELECT VERSION();  
```  
  
## <a name="see-also"></a>См. также: 
[SESSION_ID (Transact-SQL)](../../t-sql/functions/session-id-transact-sql.md)  
[DB_NAME (Transact-SQL)](../../t-sql/functions/db-name-transact-sql.md)  
  
  
