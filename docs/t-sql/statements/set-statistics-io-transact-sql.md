---
title: "ЗАДАТЬ STATISTICS IO (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 11/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET_STATISTICS_IO_TSQL
- IO
- IO_TSQL
- SET STATISTICS IO
dev_langs: TSQL
helpviewer_keywords:
- disk I/O statistics [SQL Server]
- I/O [SQL Server], disk activity information
- disks [SQL Server], statement statistics
- STATISTICS IO option
- statements [SQL Server], statistical information
- SET STATISTICS IO statement
- statistical information [SQL Server], disk activity
ms.assetid: 7033aac9-a944-4156-9ff4-6ef65717a28b
caps.latest.revision: "40"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 8d19ec8f11ae314dd4c420ba8b72689169e5e29b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="set-statistics-io-transact-sql"></a>SET STATISTICS IO (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Позволяет отображать в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сведения об активности диска, связанной с выполнением инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET STATISTICS IO { ON | OFF }  
```  
  
## <a name="remarks"></a>Замечания  
 Если значение параметра STATISTICS IO равно ON, статистические сведения отображаются. При значении OFF сведения не отображаются.  
  
 Когда данный параметр принимает значение ON, будут возвращаться сведения обо всех последующих инструкциях языка [!INCLUDE[tsql](../../includes/tsql-md.md)], пока значение параметра не будет установлено в OFF.  
  
 В следующей таблице перечислены и описаны элементы вывода.  
  
|Элемент вывода|Значение|  
|-----------------|-------------|  
|**Таблица**|Имя таблицы.|  
|**Число просмотров**|Количество операций поиска или просмотра, запущенных после достижения конечного уровня в любом направлении для получения всех значений при построении окончательного набора данных для вывода.<br /><br /> Число просмотров равно 0, если используется уникальный индекс или кластеризованный индекс первичного ключа и происходит поиск только одного значения. Например, `WHERE Primary_Key_Column = <value>`.<br /><br /> Число просмотров равно 1, если при поиске одного значения используется неуникальный кластеризованный индекс, который определен в ключевом столбце, отличном от первичного. Это позволяет проводить проверку на наличие повторяющихся значений искомого значения ключа. Например, `WHERE Clustered_Index_Key_Column = <value>`.<br /><br /> Число просмотров равно n, где n — количество различных операций поиска или просмотра, начатых по левую или правую сторону от конечного уровня после обнаружения значения ключа с помощью ключа индекса.|  
|**логических чтений**|Число страниц, считанных из кэша данных.|  
|**физических операций чтения**|Число страниц, считанных с диска.|  
|**упреждающих чтений**|Число страниц, помещенных в кэш для запроса.|  
|**LOB логических чтений**|Число **текст**, **ntext**, **изображения**, или тип больших значений (**varchar(max)**, **nvarchar(max)**, **varbinary(max)**) страниц, считываемых из кэша данных.|  
|**LOB физических чтений**|Число **текст**, **ntext**, **изображение** или больших значений типа страницы считываются с диска.|  
|**lob упреждающих чтений**|Число **текст**, **ntext**, **изображение** или введите страниц, помещенных в кэш для запроса типов больших значений.|  
  
 Параметр настройки SET STATISTICS IO устанавливается во время запуска или выполнения, но не во время синтаксического анализа.  
  
> [!NOTE]  
>  При получении столбцов больших объектов (LOB) инструкциями языка Transact-SQL для некоторых операций получения может потребоваться многократный обход дерева LOB. При этом инструкция SET STATISTICS IO может выдавать значения логических считываний выше ожидаемых.  
  
## <a name="permissions"></a>Permissions  
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
 [SET SHOWPLAN_ALL &#40; Transact-SQL &#41;](../../t-sql/statements/set-showplan-all-transact-sql.md)   
 [SET STATISTICS TIME #40; Transact-SQL &#41;](../../t-sql/statements/set-statistics-time-transact-sql.md)  
  
  
