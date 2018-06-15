---
title: SET STATISTICS IO (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 11/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- SET_STATISTICS_IO_TSQL
- IO
- IO_TSQL
- SET STATISTICS IO
dev_langs:
- TSQL
helpviewer_keywords:
- disk I/O statistics [SQL Server]
- I/O [SQL Server], disk activity information
- disks [SQL Server], statement statistics
- STATISTICS IO option
- statements [SQL Server], statistical information
- SET STATISTICS IO statement
- statistical information [SQL Server], disk activity
ms.assetid: 7033aac9-a944-4156-9ff4-6ef65717a28b
caps.latest.revision: 40
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: d314a95d8955639e67da350f5fa9c67d581dde5b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "33071881"
---
# <a name="set-statistics-io-transact-sql"></a>SET STATISTICS IO (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Позволяет отображать в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сведения об активности диска, связанной с выполнением инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET STATISTICS IO { ON | OFF }  
```  
  
## <a name="remarks"></a>Remarks  
 Если значение параметра STATISTICS IO равно ON, статистические сведения отображаются. При значении OFF сведения не отображаются.  
  
 Когда данный параметр принимает значение ON, будут возвращаться сведения обо всех последующих инструкциях языка [!INCLUDE[tsql](../../includes/tsql-md.md)], пока значение параметра не будет установлено в OFF.  
  
 В следующей таблице перечислены и описаны элементы вывода.  
  
|Элемент вывода|Значение|  
|-----------------|-------------|  
|**Таблица**|Имя таблицы.|  
|**Число просмотров**|Количество операций поиска или просмотра, запущенных после достижения конечного уровня в любом направлении для получения всех значений при построении окончательного набора данных для вывода.<br /><br /> Число просмотров равно 0, если используется уникальный индекс или кластеризованный индекс первичного ключа и происходит поиск только одного значения. Например, `WHERE Primary_Key_Column = <value>`.<br /><br /> Число просмотров равно 1, если при поиске одного значения используется неуникальный кластеризованный индекс, который определен в ключевом столбце, отличном от первичного. Это позволяет проводить проверку на наличие повторяющихся значений искомого значения ключа. Например, `WHERE Clustered_Index_Key_Column = <value>`.<br /><br /> Число просмотров равно n, где n — количество различных операций поиска или просмотра, начатых по левую или правую сторону от конечного уровня после обнаружения значения ключа с помощью ключа индекса.|  
|**логические операции чтения**|Число страниц, считанных из кэша данных.|  
|**физические операции чтения**|Число страниц, считанных с диска.|  
|**операции упреждающего чтения**|Число страниц, помещенных в кэш для запроса.|  
|**lob логических чтений**|Число страниц типа **text**, **ntext**, **image** или с большими значениями (**varchar(max)**, **nvarchar(max)**, **varbinary(max)**), считанных из кэша данных.|  
|**физические операции чтения lob**|Число страниц типов **text**, **ntext**, **image** или типов больших значений, считанных с диска.|  
|**lob упреждающих чтений**|Число страниц типов **text**, **ntext**, **image** или типов больших значений, помещенных в кэш для запроса.|  
  
 Параметр настройки SET STATISTICS IO устанавливается во время запуска или выполнения, но не во время синтаксического анализа.  
  
> [!NOTE]  
>  При получении столбцов больших объектов (LOB) инструкциями языка Transact-SQL для некоторых операций получения может потребоваться многократный обход дерева LOB. При этом инструкция SET STATISTICS IO может выдавать значения логических считываний выше ожидаемых.  
  
## <a name="permissions"></a>Разрешения  
 Для использования инструкции SET STATISTICS IO пользователи должны обладать соответствующими разрешениями на выполнение инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)]. Разрешение SHOWPLAN не требуется.  
  
## <a name="examples"></a>Примеры  
 В данном примере отображается число логических и физических операций чтения, выполняемых сервером [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по мере обработки инструкций.  
  
```  
USE AdventureWorks2012;  
GO         
SET STATISTICS IO ON;  
GO  
SELECT *   
FROM Production.ProductCostHistory  
WHERE StandardCost < 500.00;  
GO  
SET STATISTICS IO OFF;  
GO  
```  
  
 Результирующий набор:  
  
```  
Table 'ProductCostHistory'. Scan count 1, logical reads 5, physical   
reads 0, read-ahead reads 0, lob logical reads 0, lob physical reads 0,   
lob read-ahead reads 0.  
```  
  
## <a name="see-also"></a>См. также:  
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET SHOWPLAN_ALL (Transact-SQL)](../../t-sql/statements/set-showplan-all-transact-sql.md)   
 [SET STATISTICS TIME (Transact-SQL)](../../t-sql/statements/set-statistics-time-transact-sql.md)  
  
  
