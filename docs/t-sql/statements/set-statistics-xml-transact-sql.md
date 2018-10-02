---
title: SET STATISTICS XML (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SET_STATISTICS_XML_TSQL
- SET STATISTICS XML
dev_langs:
- TSQL
helpviewer_keywords:
- statistical information [SQL Server], statement processing
- STATISTICS XML option
- SET STATISTICS XML statement
- statements [SQL Server], statistical information
- XML [SQL Server], statement execution information
ms.assetid: 2b6d4c5a-a7f5-4dd1-b10a-7632265b1af7
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e59bea343c8dab06510c2cd2247f49aa171bba73
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47712504"
---
# <a name="set-statistics-xml-transact-sql"></a>SET STATISTICS XML (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  При установке этого параметра Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняет инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] и формирует подробные сведения о выполнении инструкций в форме четко определенного XML-документа.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET STATISTICS XML { ON | OFF }  
```  
  
## <a name="remarks"></a>Remarks  
 Настройка инструкции SET STATISTICS XML устанавливается во время выполнения или запуска, а не во время синтаксического анализа.  
  
 Если выполнена инструкция SET STATISTICS XML ON, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает сведения о выполнении каждого оператора после его выполнения. После присвоения этому параметру значения ON сведения обо всех последующих инструкциях [!INCLUDE[tsql](../../includes/tsql-md.md)] возвращаются до тех пор, пока параметру не будет присвоено значение OFF. Учтите, что SET STATISTICS XML может быть не единственной инструкцией в пакете.  
  
 SET STATISTICS XML возвращает вывод в качестве **nvarchar(max)** для приложений, таких как служебная программа **sqlcmd**, где вывод XML последовательно используется другими инструментами для отображения и обработки сведений о плане запроса.  
  
 SET STATISTICS XML возвращает данные в виде набора документов XML. Каждой инструкции после выполнения SET STATISTICS XML ON соответствует один документ на выходе. Каждый документ содержит текст инструкции, за которым следуют подробности об этапах выполнения команды. Вывод отображает данные времени выполнения, такие как стоимость, индексы, к которым производился доступ, тип выполненных операций, порядок соединения, количество выполнения физических операций, количество строк, созданных каждым физическим оператором и т. д.  
  
 Документ, содержащий XML-схему для вывода XML-данных, формируемых инструкцией SET STATISTICS XML, копируется во время установки в локальный каталог на компьютере, на котором установлен Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ее можно найти на диске, содержащем файлы установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
 \Microsoft SQL Server\100\Tools\Binn\schemas\sqlserver\2004\07\showplan\showplanxml.xsd  
  
 Схему для инструкции SHOWPLAN также можно найти на [следующем веб-сайте](http://go.microsoft.com/fwlink/?linkid=43100&clcid=0x409).  
  
 Инструкции SET STATISTICS PROFILE и SET STATISTICS XML являются дубликатами друг друга. Первая выводит данные в текстовом формате, а вторая выводит данные в формате XML. В будущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сведения о плане выполнения новых запросов будут доступны лишь посредством инструкции SET STATISTICS XML, но не посредством инструкции SET STATISTICS PROFILE.  
  
> [!NOTE]  
>  Если в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] установлен параметр **Включить действительный план выполнения**, то при указании этого параметра SET вывод инструкции SHOWPLAN в формате XML формироваться не будет. Снимите флажок **Включить действительный план выполнения** перед использованием параметра SET.  
  
## <a name="permissions"></a>Разрешения  
 Чтобы пользоваться инструкцией SET STATISTICS XML и просматривать ее вывод, пользователи должны иметь следующие разрешения.  
  
-   соответствующие разрешения на выполнение инструкций языка [!INCLUDE[tsql](../../includes/tsql-md.md)];  
  
-   разрешение SHOWPLAN на все базы данных, содержащие объекты, на которые ссылаются инструкции языка [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 Для инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)], не производящих результирующие наборы STATISTICS XML, требуются только соответствующие разрешения на выполнение инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)]. Для инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)], не создающих результирующие наборы STATISTICS XML, должны успешно завершиться как проверки разрешений на выполнение инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)], так и проверки разрешений SHOWPLAN, иначе выполнение инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] прерывается и сведения о разрешении SHOWPLAN не формируются.  
  
## <a name="examples"></a>Примеры  
 Две следующие инструкции используют параметры инструкции SET STATISTICS XML, чтобы продемонстрировать анализ и оптимизацию использования индексов в запросах в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В первом запросе используется оператор сравнения (=) в предложении WHERE для индексируемого столбца. Во втором запросе в предложении WHERE используется оператор LIKE. При этом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] принудительно использует просмотр кластеризованного индекса, чтобы найти данные, соответствующие условию в предложении WHERE. Значения атрибутов **EstimateRows** и **EstimatedTotalSubtreeCost** меньше у первого, индексируемого запроса, из чего следует, что первый запрос выполнился намного быстрее и потребовал меньше ресурсов, чем неиндексируемый запрос.  
  
```  
USE AdventureWorks2012;  
GO  
SET STATISTICS XML ON;  
GO  
-- First query.  
SELECT BusinessEntityID   
FROM HumanResources.Employee  
WHERE NationalIDNumber = '509647174';  
GO  
-- Second query.  
SELECT BusinessEntityID, JobTitle   
FROM HumanResources.Employee  
WHERE JobTitle LIKE 'Production%';  
GO  
SET STATISTICS XML OFF;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [SET SHOWPLAN_XML (Transact-SQL)](../../t-sql/statements/set-showplan-xml-transact-sql.md)   
 [Служебная программа sqlcmd](../../tools/sqlcmd-utility.md)  
  
  
