---
title: Имя параметров сортировки SQL Server (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 02/21/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- collations [SQL Server], SQL collations
- SQL collations
- names [SQL Server], collations
ms.assetid: 56483d24-add7-483d-9b96-c6fda460ddbc
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6f08564eb8821df4d25bf352ae3afce8afbc7dae
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62928671"
---
# <a name="sql-server-collation-name-transact-sql"></a>Имя параметров сортировки SQL Server (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Строка, указывающая имя параметров сортировки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает параметры сортировки Windows. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] также поддерживает ограниченное число параметров сортировки (<80), которые называются параметрами сортировки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и были разработаны до появления параметров сортировки Windows, поддерживаемых [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Параметры сортировки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по-прежнему поддерживаются для обеспечения обратной совместимости, но их не следует использовать при разработке новых программ. Дополнительные сведения о параметрах сортировки Windows см. в статье [Имя параметров сортировки Windows](../../t-sql/statements/windows-collation-name-transact-sql.md).

![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)

## <a name="syntax"></a>Синтаксис

```
<SQL_collation_name> :: =
SQL_SortRules[_Pref]_CPCodepage_<ComparisonStyle>

<ComparisonStyle> ::=
_CaseSensitivity_AccentSensitivity | _BIN
```

## <a name="arguments"></a>Аргументы

*SortRules* — строка, устанавливающая алфавит или язык, правила сортировки которого применяются при определении словарной сортировки. В качестве примеров приведены Latin1_General или Polish.

**Pref** — определяет настройки верхнего регистра. Даже если сравнение является нечувствительным, версия верхнего регистра буквы сортирует до версии нижнего регистра, когда нет другого отличия.

*Codepage* — определяет число из одной-четырех цифр, которое идентифицирует кодовую страницу, используемую параметрами сортировки. **CP1** определяет кодовую страницу 1252; для всех остальных кодовых страниц необходимо указывать их полный номер. Например, **CP1251** определяет кодовую страницу 1251, а **CP850** определяет кодовую страницу 850.

*CaseSensitivity*
**CI** — указывает, что регистр символов не учитывается. **CS** — определяет учет регистра.

*AccentSensitivity*
**AI** — указывает, что регистр символов не учитывается. **AS** — определяет учет регистра.

**BIN** — определяет двоичный порядок сортировки.

## <a name="remarks"></a>Remarks

Чтобы сформировать список параметров сортировки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которые поддерживает сервер, выполните следующий запрос.

```sql
SELECT * FROM sys.fn_helpcollations()
WHERE name LIKE 'SQL%';
```

> [!NOTE]
> Для идентификатора порядка сортировки 80 используйте любые из параметров сортировки Windows с кодовой страницей 1250 и двоичный порядок. Пример: Albanian_BIN, Croatian_BIN, Czech_BIN, Romanian_BIN, Slovak_BIN, Slovenian_BIN.

## <a name="see-also"></a>См. также:

- [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md)
- [Константы](../../t-sql/data-types/constants-transact-sql.md)
- [CREATE DATABASE](../../t-sql/statements/create-database-transact-sql.md?view=sql-server-2017)
- [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md)
- [DECLARE @local_variable](../../t-sql/language-elements/declare-local-variable-transact-sql.md)
- [table](../../t-sql/data-types/table-transact-sql.md)
- [sys.fn_helpcollations](../../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md)
