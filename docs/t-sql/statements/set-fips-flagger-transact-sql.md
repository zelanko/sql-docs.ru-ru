---
title: "SET FIPS_FLAGGER (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/29/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FIPS_FLAGGER
- SET_FIPS_FLAGGER_TSQL
- FIPS_FLAGGER_TSQL
- SET FIPS_FLAGGER
dev_langs:
- TSQL
helpviewer_keywords:
- SET FIPS_FLAGGER statement
- FIPS 127-2 standard
- FIPS_FLAGGER option
ms.assetid: e82f6bee-6cf6-4061-be22-9ad2e8e9d3d6
caps.latest.revision: 31
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4c28fd5419aec8bf15745150288b6878fd65ac1f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="set-fipsflagger-transact-sql"></a>SET FIPS_FLAGGER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Указывает режим проверки на соответствие стандарту FIPS 127-2. Основывается на стандарте ISO. Сведения о совместимости SQL Server FIPS см. в разделе [использование SQL Server 2016 в FIPS 140-2-совместимый режим](https://support.microsoft.com/help/4014354/how-to-use-sql-server-2016-in-fips-140-2-compliant-mode). 
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
SET FIPS_FLAGGER ( 'level' |  OFF )  
```  
  
## <a name="arguments"></a>Аргументы  
 **"** *уровень* **"**  
 Уровень соответствия стандарту FIPS 127-2 для проверки всех операций базы данных. В случае конфликта операции базы данных с уровнем стандартов ISO [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создает предупреждение.  
  
 *уровень* должен быть одним из следующих значений.  
  
|Значение|Description|  
|-----------|-----------------|  
|ENTRY|Проверка на соответствие начальному уровню стандарта ISO.|  
|ПОЛНОЕ|Проверка на полное соответствие стандарту ISO.|  
|INTERMEDIATE|Проверка на соответствие промежуточному уровню стандарта ISO.|  
|OFF|Без проверки стандарта.|  
  
## <a name="remarks"></a>Замечания  
 Параметр `SET FIPS_FLAGGER` задается во время синтаксического анализа, а не на или времени выполнения. Установка во время синтаксического анализа означает, что если инструкция SET присутствует в пакете или хранимой процедуре, она вступает в силу независимо от того, достигает ли фактически выполнение кода соответствующей точки. и `SET` инструкции вступает в силу до выполнения любых операторов. Например, даже если `SET` инструкция находится в `IF...ELSE` блок операторов, который никогда не выполняется во время выполнения, `SET` инструкции по-прежнему действует, поскольку `IF...ELSE` анализируется блока инструкций.  
  
 Если `SET FIPS_FLAGGER` задается в хранимой процедуре, значение `SET FIPS_FLAGGER` восстанавливается после возврата управления из хранимой процедуры. Таким образом `SET FIPS_FLAGGER` инструкция, указанная в динамическом коде SQL не имеет влияния на инструкции, следующие за инструкцией динамического SQL.  
  
## <a name="permissions"></a>Permissions  
 Необходимо быть членом роли **public** .  
  
## <a name="see-also"></a>См. также:  
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)  
  
  

