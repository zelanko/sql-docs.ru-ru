---
title: Классификатор DROP WORKLOAD (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 05/01/2019
ms.prod: sql
ms.prod_service: sql-data-warehouse
ms.reviewer: jrasnick
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- WORKLOAD CLASSIFIER
- WORKLOAD_CLASSIFIER_TSQL
- DROP_WORKLOAD_CLASSIFIER_TSQL
- DROP WORKLOAD GROUP
dev_langs:
- TSQL
helpviewer_keywords:
- DROP WORKLOAD CLASSIFIER statement
ms.assetid: ''
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: =azure-sqldw-latest||=sqlallproducts-allversions
ms.openlocfilehash: 67909db180af056add12324622cfd6094d8729fe
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2019
ms.locfileid: "65105831"
---
# <a name="drop-workload-classifier-transact-sql"></a>Классификатор DROP WORKLOAD (Transact-SQL)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Удаляет существующий определяемый пользователем классификатор рабочей нагрузки управления.  
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  

```
DROP WORKLOAD CLASSIFIER classifier_name;
```

## <a name="arguments"></a>Аргументы

*classifier_name*  
Указывает имя, по которому идентифицируется классификатор рабочей нагрузки.  Значение classifier_name — это sysname.  Оно может иметь длину до 128 символов и должно быть уникальным в пределах экземпляра.
  
## <a name="remarks"></a>Remarks

Инструкция DROP WORKLOAD CLASSIFIER не допускается для системных классификаторов рабочей нагрузки.

Если запросы выполняются или находятся в очереди запросов в приостановленном состоянии, они сохраняют свою классификацию и классификатор может быть удален немедленно.  Удаление и повторное создание классификатора с другим уровнем важности не затрагивает уже классифицированные запросы.

## <a name="permissions"></a>Разрешения

Необходимо разрешение CONTROL DATABASE.  
  
## <a name="examples"></a>Примеры

В следующем примере удаляется классификатор рабочей нагрузки с именем `wgcELTROLE`.  

```sql
DROP WORKLOAD CLASSIFIER wgcELTRole;
```

> [!NOTE]
> Запрос, отправленный без соответствующего классификатора, классифицируется в группу рабочей нагрузки по умолчанию.  Группа рабочей нагрузки по умолчанию — класс ресурсов smallrc.
  
## <a name="see-also"></a>См. также:

[CREATE WORKLOAD CLASSIFIER &#40;Transact-SQL&#41;](../../t-sql/statements/create-workload-classifier-transact-sql.md)</br>
[Классификация рабочих нагрузок хранилища данных SQL](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification)
