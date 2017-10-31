---
title: "Имя параметров сортировки SQL Server (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 05/11/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- collations [SQL Server], SQL collations
- SQL collations
- names [SQL Server], collations
ms.assetid: 56483d24-add7-483d-9b96-c6fda460ddbc
caps.latest.revision: 30
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: fc7265f4efe0d790ab61e4e522af83d6b91b710a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="sql-server-collation-name-transact-sql"></a>Имя параметров сортировки SQL Server (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Строка, указывающая имя параметров сортировки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает параметры сортировки Windows. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] также поддерживает ограниченное число параметров сортировки (<80), которые называются параметрами сортировки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и были разработаны до появления параметров сортировки Windows, поддерживаемых [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Параметры сортировки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по-прежнему поддерживаются для обеспечения обратной совместимости, но их не следует использовать при разработке новых программ. Дополнительные сведения о параметрах сортировки Windows см. в разделе [имя параметров сортировки Windows &#40; Transact-SQL &#41; ](../../t-sql/statements/windows-collation-name-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<SQL_collation_name> :: =   
SQL_SortRules[_Pref]_CPCodepage_<ComparisonStyle>  
  
<ComparisonStyle> ::=  
_CaseSensitivity_AccentSensitivity | _BIN  
```  
  
## <a name="arguments"></a>Аргументы  
 *SortRules*  
 Строка, устанавливающая алфавит или язык, правила сортировки которого применяются при определении словарной сортировки. В качестве примеров приведены Latin1_General или Polish.  
  
 **Pref**  
 Определяет настройки верхнего регистра. Даже если сравнение является нечувствительным, версия верхнего регистра буквы сортирует до версии нижнего регистра, когда нет другого отличия.  
  
 *Codepage*  
 Определяет число из одной-четырех цифр, которое идентифицирует кодовую страницу, используемую параметрами сортировки. **CP1** определяет кодовую страницу 1252, задается для всех остальных кодовых страниц номер страницы полный код. Например **CP1251** определяет кодовую страницу 1251 и **CP850** определяет кодовую страницу 850.  
  
 *CaseSensitivity*  
 **CI** определяет нечувствительность к регистру, **CS** задает регистр.  
  
 *AccentSensitivity*  
 **AI** указывает диакритических знаков, **AS** указывает диакритических знаков.  
  
 **BIN**  
 Определяет двоичный порядок сортировки.  
  
## <a name="remarks"></a>Замечания  
 Чтобы сформировать список параметров сортировки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которые поддерживает сервер, выполните следующий запрос.  
  
```  
SELECT * FROM sys.fn_helpcollations()   
WHERE name LIKE 'SQL%';  
```  

>  [!NOTE]  
>  Для идентификатора порядка сортировки 80 используйте любой из параметров сортировки Windows с кодовой страницей 1250 и двоичный порядок. Например: Albanian_BIN, Croatian_BIN, Czech_BIN, Romanian_BIN, Slovak_BIN, Slovenian_BIN.  
  
## <a name="see-also"></a>См. также:  
 [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)   
 [Константы &#40; Transact-SQL &#41;](../../t-sql/data-types/constants-transact-sql.md)   
 [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [DECLARE @local_variable (Transact-SQL)](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
 [Таблица &#40; Transact-SQL &#41;](../../t-sql/data-types/table-transact-sql.md)   
 [sys.fn_helpcollations &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md)  
  
  

