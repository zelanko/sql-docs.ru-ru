---
title: Классификатор CREATE WORKLOAD (Transact-SQL) | Документация Майкрософт
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
- CREATE WORKLOAD CLASSIFIER
- CREATE_WORKLOAD_CLASSIFIER_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE WORKLOAD CLASSIFIER statement
ms.assetid: ''
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: =azure-sqldw-latest||=sqlallproducts-allversions
ms.openlocfilehash: 0cb7587cd88dd2d6c3915482f0741cf048dfda06
ms.sourcegitcommit: 5905c29b5531cef407b119ebf5a120316ad7b713
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66428883"
---
# <a name="create-workload-classifier-transact-sql"></a>Классификатор CREATE WORKLOAD (Transact-SQL)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Создает классификатор управления рабочей нагрузкой.  Классификатор назначает входящие запросы в группу рабочей нагрузки и присваивает ранг важности в зависимости от параметров, указанных в инструкции определения классификатора.  Классификаторы вычисляются при каждом запросе.  Если запрос не соответствует классификатору, то он назначается в группу рабочей нагрузки по умолчанию.  Группа рабочей нагрузки по умолчанию — класс ресурсов smallrc.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис

```
CREATE WORKLOAD CLASSIFIER classifier_name  
WITH  
    ( WORKLOAD_GROUP = 'name'  
     ,MEMBERNAME = 'security_account'
 [ [ , ] IMPORTANCE = { LOW | BELOW_NORMAL | NORMAL (default) | ABOVE_NORMAL | HIGH }])
[;]
```

## <a name="arguments"></a>Аргументы

 *classifier_name*  
 Указывает имя, по которому идентифицируется классификатор рабочей нагрузки.  Значение classifier_name — это sysname.  Оно может иметь длину до 128 символов и должно быть уникальным в пределах экземпляра.

WORKLOAD_GROUP = *"name"* При выполнении условий правила классификатора имя name сопоставляется запросу группы рабочей нагрузки.  Значение name — это sysname.  Оно может иметь длину до 128 символов и должно быть допустимым именем группы рабочей нагрузки во время создания классификатора.

WORKLOAD_GROUP должно сопоставляться с существующим классом ресурсов:

|Статические классы ресурсов|Динамические классы ресурсов|
|------------------------|-----------------------|
|staticrc10|smallrc|
|staticrc20|mediumrc|
|staticrc30|largerc|
|staticrc40|xlargerc|
|staticrc50||
|staticrc60||
|staticrc70||
|staticrc80||

MEMBERNAME = *'security_account'* Это учетная запись безопасности, добавляемая к роли.  Значение security_account — это sysname, которое не имеет значения по умолчанию. Значением security_account может быть пользователь базы данных, роль базы данных, учетная запись Azure Active Directory или группа Azure Active Directory.

IMPORTANCE = { LOW | BELOW_NORMAL | NORMAL | ABOVE_NORMAL | HIGH } Указывает относительную важность запроса.  Важность принимает одно из следующих значений:

- LOW
- BELOW_NORMAL
- NORMAL (по умолчанию)
- ABOVE_NORMAL
- HIGH.  

Важность влияет на порядок, в котором будут запланированы запросы, тем самым обеспечивая приоритетный доступ к ресурсам и блокировке.

Если пользователь является членом нескольких ролей, которым назначены разные классы ресурсов или сопоставлены несколько классификаторов, пользователю назначается класс ресурсов наиболее высокого уровня. Дополнительные сведения см. в разделе о [классификации рабочих нагрузок](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification#classification-precedence).

## <a name="permissions"></a>Разрешения

 Необходимо разрешение CONTROL DATABASE.  
  
## <a name="examples"></a>Примеры

 В следующем примере демонстрируется, как создать классификатор рабочей нагрузки с именем `wgcELTRole`. Он использует группу рабочей нагрузки staticrc20, имя пользователя `ELTRole` и задает уровень важности `above_normal`.

```sql
CREATE WORKLOAD CLASSIFIER wgcELTRole
  WITH (WORKLOAD_GROUP = 'staticrc20'
       ,MEMBERNAME = 'ELTRole'
      ,IMPORTANCE = above_normal);
```

## <a name="see-also"></a>См. также:

[DROP WORKLOAD CLASSIFIER &#40;Transact-SQL&#41;](../../t-sql/statements/drop-workload-classifier-transact-sql.md)</br>
Представление каталога [sys.workload_management_workload_classifier_details](../../relational-databases/system-catalog-views/sys-workload-management-workload-classifier-details-transact-sql.md)</br>
Представление каталога [sys.workload_management_workload_classifiers](../../relational-databases/system-catalog-views/sys-workload-management-workload-classifiers-transact-sql.md)
[Классификация Хранилища данных SQL](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification)
