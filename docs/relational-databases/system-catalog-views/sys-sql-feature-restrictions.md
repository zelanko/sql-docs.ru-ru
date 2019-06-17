---
title: sys.sql_feature_restrictions (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/07/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sql_sql_feature_restrictions
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sql_feature_restrictions catalog view
author: vainolo
ms.author: arib
manager: tomerw
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: b583afef9f52da7801384d4a7a9c76deaf8d4ee4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66822675"
---
# <a name="syssqlfeaturerestrictions-transact-sql"></a>sys.sql_feature_restrictions (Transact-SQL)

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Возвращает одну строку для каждого ограничения в базе данных.
  
| Имя столбца | Тип данных | Описание |
|-------------|-----------|-------------|
| class       | NVARCHAR(128) | Класс объекта, к которому применяется ограничение |
| объект      | nvarchar(256) | Имя объекта, к которому применяется ограничение |
| Функция     | NVARCHAR(128) | Компонент, который является ограниченным |
  
## <a name="remarks"></a>Примечания

В настоящее время следующие функции могут быть ограничены:

| Компонент          | Описание |
|------------------|-------------|
| N'ErrorMessages | При ограничения, будут замаскированы какие-либо данные в сообщении об ошибке. |
| N'Waitfor "       | Когда ограничена, команда вернет сразу без задержки. |
  
## <a name="permissions"></a>Разрешения

Должен иметь исполняющему участнику `CONTROL` разрешение в базе данных.
  
## <a name="see-also"></a>См. также

 [Функциональные ограничения](../../relational-databases/security/feature-restrictions.md)
