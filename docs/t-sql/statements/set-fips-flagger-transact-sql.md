---
title: SET FIPS_FLAGGER (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3dc9d43b01c6297478672f3de2b7797ff25c69ff
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2020
ms.locfileid: "81634392"
---
# <a name="set-fips_flagger-transact-sql"></a>SET FIPS_FLAGGER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Указывает режим проверки на соответствие стандарту FIPS 127-2. Основывается на стандарте ISO. Сведения о совместимости SQL Server FIPS см. в статье об [использовании SQL Server 2016 в режиме совместимости с FIPS 140-2](https://support.microsoft.com/help/4014354/how-to-use-sql-server-2016-in-fips-140-2-compliant-mode). 
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
SET FIPS_FLAGGER ( 'level' |  OFF )  
```  
  
## <a name="arguments"></a>Аргументы  
 **'** *level* **'**  
 Уровень соответствия стандарту FIPS 127-2 для проверки всех операций базы данных. При наличии конфликтов операции базы данных с выбранным уровнем стандартов ISO [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] формирует предупреждение.  
  
 *level* должен иметь одно из следующих значений.  
  
|Значение|Description|  
|-----------|-----------------|  
|ENTRY|Проверка на соответствие начальному уровню стандарта ISO.|  
|FULL|Проверка на полное соответствие стандарту ISO.|  
|INTERMEDIATE|Проверка на соответствие промежуточному уровню стандарта ISO.|  
|OFF|Без проверки стандарта.|  
  
## <a name="remarks"></a>Remarks  
 Значение параметра `SET FIPS_FLAGGER` устанавливается во время выполнения или запуска, а не во время синтаксического анализа. Проверка на этапе синтаксического анализа означает, что если инструкция SET присутствует в пакете или хранимой процедуре, то она вступает в силу независимо от того, достигает ли фактическое выполнение кода соответствующей точки. Кроме того, инструкция `SET` вступает в силу до выполнения любых операторов. Например, если инструкция `SET` находится в блоке `IF...ELSE`, который никогда не выполняется во время обработки, то она, тем не менее, `SET` вступает в силу, поскольку блок `IF...ELSE` подвергается синтаксическому анализу.  
  
 Если инструкция `SET FIPS_FLAGGER` установлена в хранимой процедуре, значение `SET FIPS_FLAGGER` восстанавливается после того, как управление выходит из этой хранимой процедуры. Поэтому инструкция `SET FIPS_FLAGGER`, определенная в динамическом коде SQL, не действует на инструкции, следующие за инструкцией динамического SQL.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public**.  
  
## <a name="see-also"></a>См. также:  
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)  
  
  
